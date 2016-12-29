---
layout: default
title: MVC-Controller
permalink: mvc_controller
---

## MVC - Controller

The C in MVC stands for controller.

In previous weeks we have looked at both the [Model](http://railsgirlsbne.com/mvc_model) and the [View](http://railsgirlsbne.com/mvc_view) layers. We know that the model retrieves data out of the database and that the view displays that data. But how does the model know what data is required and how does the data get passed back to the view? That is where the controller comes in.

In the same way that every object in our application has a model and a number of views, each object also has a controller. The Controller is responsible for orchestrating the whole process of handling a request in Rails.

The `routes.rb` file maps an external request from a URL entered into a browser to an internal action within your Rails application. That internal action is a method in a controller. The controller may also contain logic to implement business rules.
