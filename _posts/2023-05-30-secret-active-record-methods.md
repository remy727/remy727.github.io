---
layout: post
title: "Secret Active Record Methods"
date:   2023-05-30 06:00:00 -0400
categories: ruby
comments: true
---

I learned Active Record feature: using `!` query methods to modify a query object in place instead of returning a new one. Let’s use `distinct!` as an example:

```ruby
# distinct! modifies the current query object, while distinct creates a new query object:
my_query = User.all
my_query.distinct!
my_query.to_sql
#=> "SELECT DISTINCT \"users\".* FROM \"users\""

my_query = User.all
my_other_query = my_query.distinct
my_query.to_sql
#=> "SELECT \"users\".* FROM \"users\""
my_other_query.to_sql
#=> "SELECT DISTINCT \"users\".* FROM \"users\""
```

In fact, `distinct` is implemented by calling something similar to `self.dup.distinct!`. This kind of pattern also exists for other Active Record query methods like `where`/`where!`, `order`/`order!`, `joins`/`joins!`, etc.