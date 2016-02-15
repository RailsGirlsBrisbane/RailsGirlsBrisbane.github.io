---
layout: default
title: Welcome
permalink: migrations_blog
---

##Rails Migrations

Recently I came across an issue with a database migration that could easily have been avoided.

I was querying a database that contained a number of boolean NULL values. This is ambiguous, as it could mean false or it could simply mean that the value has never been set.

This scenario is easily avoided by simply setting your boolean to either true or false as a part of your migration. For example;

 `add_column :staff, :is_admin, :boolean, null: false, default: false`

That's it! Easy right? It may not change your life but it will surely avoid a headache somewhere down the track.