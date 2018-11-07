---
layout: post
title:      "Making my classes play nicely together"
date:       2017-10-04 14:21:47 -0400
permalink:  making_my_classes_play_nicely_together
---


Falling off of a cliff may be less scary than staring at a completely blank text editor for the first time.

Give me the file structure, and I can iterate through a hash like a bad boy, er girl.  
Set up the dependencies for me, and I can make my objects collaborate in sweet harmony.

But that's working in the minor leagues - pardon the mixed metaphores.

Tell me to come up with an idea, and piece it together step by step, file by file, directory by directory...that's another story.

I know I'm not the first, and won't be the last newbie to stare at a blank screen, unsure of where to even begin.

This is not a complete treatise on the topic, but it may be the start that you need to create that first project.  

The purpose of this post is specifically to understand how to set up what are called dependencies.  When I'm creating a project with multiple classes and multiple files, how do I get those different files to 1. know about each other, and 2. communicate and cooperate with each other --- in the most efficient way possible.  I want to be a good/lazy programming and set this up in the simplest way possible.

it is standard to have our ```bin``` and ```lib``` directories.  

Generally, the code we write goes into ```lib```

The executables go into ```bin```

So within ```lib``` we may very well have multiple files.  And those files may been to talk to each other and exchange information with one another.

Let's say we have a ```dog.rb```    ```cat.rb```  ```bunny.rb```   ```giraffe.rb``` -> sure, why not?

Additionally, we have a ```mammal``` module in ```mammal.rb``` that all four of the previous files interact with.  

In each of those four files we could put ```require '.lib/mammal```
We'd have to write that 4 times.  And if we add another file, we'll have to remember to add that to the new file.  And if at some point we add another module, then we need to go back into all four files and add a require statement to connect to the new module.

It works, but isn't very lazy.  Let's be lazier.

What is:
1. A single file held all of the require statements, so that when a change needed to be made, it only needed to be made in one place, and
2. Every other file connected to that single file.

So that:

```dog.rb```    ```cat.rb```  ```bunny.rb```   ```giraffe.rb```  

all point to one file.  That one file then points to everything else that is needed.

Sounds great. How do we do that?

We create a file that ```configures``` the environment

1. In a directory called ```config``` (industry standard name) we create a file called ```environment.rb```

```envorinment.rb``` holds **all** of our require statements.  

2. Our project .rb file then requires that ```'../config/environment'``` file
3. Lastly, the executable file in our ```bin``` directory requires our project.rb file.

So that, when we execute our code, it loads the ```project.rb``` which then loads ```environment.rb``` which loads all of our dependencies.

Now when we need to add a dependency, we can do so in ```environment.rb``` and all files are linked as needed.

