---
layout: default
title: ActionController
permalink: action_controller
---

## The magic that is ActionController

We use controllers a lot in our applications but do we really understand the magic that is behind them?

Controllers are considered to be the middleman between the model and the view. Most inherit from ApplicationController.
But did you know that ApplicationController inherits from another controller called ActionController::Base?

By using inheritance, (that's the `< ApplicationController` bit) we gain a whole lot more functionality that we can use in our app.

ActionController::Base is part of the Rails library Action Pack. It is the base class for all controllers in a Rails application.
It provides many helper methods including the filtering of inbound http requests, access to our model, and rendering a view.
But there are many more, see the [rails API] (http://api.rubyonrails.org/classes/ActionController/Base.html) for more info.

Below is a simple example of how it might look. It looks like it is doing very little. In fact, it is doing a lot!
It is getting the params from the url, asking our model for that record (using the id) and then rendering the show.html.erb view.

{% highlight sh %}
class IdeasController < ApplicationController
  def show
    @idea = Idea.find(params[:id])
  end
end
{% endhighlight %}

Easy huh?
