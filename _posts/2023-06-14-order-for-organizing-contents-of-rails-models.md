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
- Enums
- Class methods
- Instance methods

```ruby
class Webhook < ApplicationRecord
  # Constants

  # Associations

  # Scopes

  # Validations

  # Callbacks

  # Enums

  # Class methods

  # Instance methods
end

class Color < ApplicationRecord
  # == Constants ============================================================

  # == Attributes ===========================================================
  attribute :name

  # == Extensions ===========================================================
  translates :name, fallbacks_for_empty_translations: true
  globalize_accessors

  # == Associations ========================================================
  has_many :vehicle_listings, dependent: :nullify

  # == Validations ==========================================================
  validates(*Color.globalize_attribute_names, presence: true)

  # == Scopes ===============================================================

  # == Callbacks ============================================================

  # == Class Methods ========================================================

  # == Instance Methods =====================================================
end
```
