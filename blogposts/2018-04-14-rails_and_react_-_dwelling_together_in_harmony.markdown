---
layout: post
title:      "Rails and React - Dwelling together in harmony"
date:       2018-04-14 22:43:07 +0000
permalink:  rails_and_react_-_dwelling_together_in_harmony
---


As I opened my terminal to write the initial commands to get the app started, I wasn't sure what to type. With my prior Rails app it was a simple ```Rails new ____``` to get things up and running.  Frontend/backend -- that one command was all I needed.

This time around I looked at the blinking cursor in my terminal unsure where to start.  Or more accurately, wondering how to combine my ```Rails new``` command with the ```npm create-react-app``` one.  

Novice questions, I'm sure, but do I combine these both under the same directory?  Do I make two different directories, two different repos and some how enable calls from the frontend to this separate backend?  

Creating a repo inside of a repo didn't quite work.

Surely there is a solution that makes sense and I can follow.

Enter the ```rails new . ---api``` command.  This sets up a rails structure without the view functionality that I do not need.

After reading many-a-blog post I decided to keep frontend and backend in the same repo,  nesting the React portion of the app inside of the Rails file structure, labeled "Client".





