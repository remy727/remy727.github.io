---
layout: post
title: "PostgreSQL Commands"
date:   2023-06-08 02:00:00 -0400
categories: postgresql
comments: true
---

In this blog post, you will learn some postgreSQL commands.


```sql
---  Query retrieves all the enum types and their corresponding labels in the PostgreSQL database:
SELECT pg_type.typname AS enum_type, pg_enum.enumlabel AS enmu_label FROM pg_type JOIN pg_enum ON pg_enum.enumtypid = pg_type.oid;

--- drops an enum type called
DROP TYPE your_enum_type_here;
```
