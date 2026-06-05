---
name: rails-example-callbacks-to-service
description: Example showing how to extract after_create callback side effects into an explicit service object.
---

# Extract Callbacks to Service

Move multi-step side effects out of `after_create` callbacks into an explicit service.

## Before

```ruby
class User < ApplicationRecord
  after_create :send_welcome_email
  after_create :create_default_workspace
  after_create :notify_admin

  private

  def send_welcome_email = UserMailer.welcome(self).deliver_later
  def create_default_workspace = workspaces.create!(name: "My Workspace")
  def notify_admin = AdminMailer.new_user(self).deliver_later
end
```

## After

```ruby
# app/models/user.rb
class User < ApplicationRecord
  # callbacks removed — side effects live in the service
end

# app/services/users/create.rb
class Users::Create < ApplicationService
  param :params

  def call
    user = User.create!(params)
    UserMailer.welcome(user).deliver_later
    user.workspaces.create!(name: "My Workspace")
    AdminMailer.new_user(user).deliver_later
    user
  end
end

# app/controllers/users_controller.rb
class UsersController < ApplicationController
  def create
    @user = Users::Create.call(user_params)
    redirect_to @user, notice: "Welcome!"
  rescue ActiveRecord::RecordInvalid => e
    @user = e.record
    render :new, status: :unprocessable_entity
  end
end
```

## Why

Callbacks fire implicitly on every `User.create!` — including in tests and seeds — making side effects hard to control. The service makes the full operation explicit and testable in isolation.
