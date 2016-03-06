---
layout: default
title: Welcome
permalink: restful_rails
---

## Keeping Rails RESTful

Recently I decided to add a new download file feature to the Rails Girls Ideas app. It seemed like a straightforward task. But, upon opening the routes.rb file, I realised I there was more to this decision than I first thought. I had to decide on the _type_ of route...should I create a member route or a resource route?

### What is a Member Route
A member route simply adds an additional action to the enclosing resource.

The example below adds a new `file` action to the existing ideas controller (ideas_controller.rb). In this case the file relates to a single idea. The url to access it would be something like `/ideas/1/file`

_# routes.rb_

    resourses :ideas do
      member do
        get :file
      end
    end

*# ideas_controller.rb*

    class IdeasController < ApplicationController
      def file
       # download code here
      end
    end

However I started to think about what else I might need to do with the files: What if I want to add some more methods? What if I want to rename the file, or tag the file? What if I want to add a method to delete the file? And if I add all this new functionality, does it still belong in the ideas_controller?

## Why a Resource Route
In order to keep controllers from becoming bloated, you can put the new action into its own controller. Then if the situation arises where you want to extend the functionality of the controller and add methods such as upload/download/rename/tag/delete actions you are already in the right place.

_# routes.rb_

    resources :ideas do
      resource :file, only: [:show]
    end

_# creating the new method in its own controller_

    class FilesController < ApplicationController do
      def show
        #download method
      end
    end

The url to access it is still something like `/ideas/1/file`. The only difference lies in the fact that file is now an entity all of it's own and, as such, has it's own controller.

Remember when in doubt type `rake routes` at the command line to find your way. It will show you the http verbs, the controller and corresponding action and also the url helpers

I should point out that using a _resource route_ is considered more RESTful than a member route. However understanding the difference is the key, as it will guide you in making an informed decision :)