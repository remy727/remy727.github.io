---
layout: post
title: "Model Types"
date:   2023-06-08 04:30:00 -0400
categories: rails
comments: true
---

### Domain models
A domain model in Rails, also known as a business model or simply a model, is a representation of the core business logic and data structures of your application. It is a part of the Model-View-Controller (MVC) architectural pattern that Rails follows. The domain model is responsible for handling the data, business rules, and relationships between different entities in your application.

In Rails, domain models are typically represented by Ruby classes that inherit from ActiveRecord::Base. These classes are stored in the app/models directory of your Rails application. The main purpose of a domain model is to interact with the database, perform validations, and define relationships between different models.

```ruby
# app/models/user.rb
class User < ActiveRecord::Base
  has_many :posts
  validates :name, presence: true
  validates :email, presence: true, uniqueness: true
end

# app/models/post.rb
class Post < ActiveRecord::Base
  belongs_to :user
  validates :title, presence: true
  validates :content, presence: true
end
```

### Form models
These models are used to handle form submissions and validations that are not directly tied to a specific domain model. They can be useful for complex forms that involve multiple domain models or for forms that don't map directly to a single domain model. Form models typically inherit from ActiveModel::Model or include ActiveModel::Model module.

```ruby
# app/models/contact_form.rb
class ContactForm
  include ActiveModel::Model

  attr_accessor :name, :email, :message

  validates :name, presence: true
  validates :email, presence: true, format: { with: URI::MailTo::EMAIL_REGEXP }
  validates :message, presence: true
end
```

### Service models
These models encapsulate complex business logic or interactions between multiple domain models. Service models are often used to keep the domain models and controllers clean and focused on their primary responsibilities. Service models are usually plain Ruby classes that don't inherit from any Rails-specific classes.

```ruby
# app/services/user_registration_service.rb
class UserRegistrationService
  def initialize(params)
    @params = params
  end

  def register
    user = User.new(@params)
    if user.save
      # Perform additional registration steps, e.g., send a welcome email
    end
    user
  end
end
```

### Decorator models
These models are used to add presentation logic to domain models, keeping the domain models focused on business logic. Decorator models typically use the decorator pattern and can be implemented using the draper gem or by creating plain Ruby classes.

```ruby
# app/decorators/user_decorator.rb
class UserDecorator
  def initialize(user)
    @user = user
  end

  def full_name
    "#{@user.first_name} #{@user.last_name}"
  end
end
```

### Policy models
These models are used to handle authorization logic, determining what actions a user is allowed to perform on a given resource. Policy models can be implemented using the pundit gem or by creating plain Ruby classes.

```ruby
# app/policies/post_policy.rb
class PostPolicy
  def initialize(user, post)
    @user = user
    @post = post
  end

  def update?
    @user == @post.user
  end
end
```
