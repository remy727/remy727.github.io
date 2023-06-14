---
layout: post
title: "Order for organizing contents for Rails models"
date:   2023-06-14 10:00:00 -0400
categories: rails
comments: true
---

In Ruby on Rails, it's a good practice to follow a consistent order for organizing the contents of the models. Here's an order I always use:

- Constants
- Associations
- Scopes
- Validations
- Callbacks
- Enumerations
- Class methods
- Instance methods

```ruby
class Webhook < ApplicationRecord
  # Constants
  # (Add constants here if needed)

  # Associations
  belongs_to :shop

  # Scopes
  scope :marked_for_deletion, -> { where() }

  # Validations
  validates :shopify_webhook_id, presence: true, uniqueness: true
  validates :topic, presence: true

  # Callbacks
  # (Add callbacks here if needed)

  # Enumerations
  # (Add enumerations here if needed)

  # Class methods
  def self.duplicated?(shopify_webhook_id:)
    exists?(shopify_webhook_id: shopify_webhook_id)
  end

  # Instance methods
  # (Add instance methods here if needed)
end
```
