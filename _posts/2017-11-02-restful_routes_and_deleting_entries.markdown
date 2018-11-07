---
layout: post
title:      "RESTful Routes & Deleting Entries"
date:       2017-11-02 11:36:49 -0400
permalink:  restful_routes_and_deleting_entries
---


I'm not the first nor will I be the last programmer struggling to route to a DELETE controller in Sinatra.  Hopefully my struggle can save you some time.

First, what failed:

Despite trying to 'will it' to work, simply adding an href into my show view did not do what I wanted it to do.

```
<a href=<% "/recipes/#{@recipe.id}" %> >
  Delete this recipe </a>
<input id="hidden" type="hidden" name="_method" value="delete">
```

I remembered I needed that bottom line.  Sinatra doesn't natively offer a Delete route, so we need to use Rack Middleware, which will intercept our action, and redirect to whatever we specify in Value.

I few problems with this first approach.

1.  I failed to include 
```
use Rack::MethodOverride
```
in my config.ru.

So if you are trying to get this to work, do that now.  It needs to be above your run command, like so: 

```
use Rack::MethodOverride
run ApplicationController
```

Second, (from what I can gather) this set up only works with a form.  I cannot have a <a></a> sitting out there alone. 
```
<input id="hidden" type="hidden" name="_method" value="delete">
```
must be within a form, which uses an action= and method= to specify the desired route.  

So the working code looks more like this:
```
<form action="/recipes/<%=@recipe.id%>/delete" method="post">
  <input id="hidden" type="hidden" name="_method" value="delete">
  <input type="submit" value="delete">
</form>
```

This successfully routes me to my delete controller, from where I can execute the delete process.

Hope this helps someone.


