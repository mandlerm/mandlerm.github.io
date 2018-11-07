---
layout: post
title:      "Sinatra Portfolio Project - Homeschool Organizer"
date:       2017-11-09 21:16:05 +0000
permalink:  sinatra_portfolio_project_-_homeschool_organizer
---


Pick a project that is meaningful to you: those were part of the instructions.  What could I create that would actually be useful to me, beyond a learning experience?

I chose to create an organizational app for homeschoolers.  As a homeschool mom of 4 kids, we are daily dealing with school schedules, assignments, instruments to practice, who did what and what didn't get done.  

Anything that would make that process easier is a worthy pursuit.

While my finished product is not an exhaustive application by any means, it leaves me with a functional framework that is easily expanded for greater functionality.

I started by writing out on paper what my relationships would be and what exactly I wanted to track.  This is very much a Version 1 product with Version 1 capabilities.  I was going for simple, useful, and manageable.  'Ship often' is the mantra of the tech world.  I can always upgrade at a later date.

Clearly there are students, and teacher is likely Mom or Dad.  Students have_many subjects and (in our case) many instruments.  They also belong_to a teacher.  Instruments have_many students, as do subjects.

Setting up the student and teacher models was fun as they both have log in capabilities but different functionality.  The teacher can create new subjects whereas the students can only select the subjects they have completed; they have no ability to create or delete subjects; the same for their instruments.

Students can view only their information whereas the teacher can view both individual students as well as all students collectively.

I utilized the Corneal Gem created by a Flatiron grad to give me my initial Sinatra set up.  This was a time saved!  (https://github.com/thebrianemory/corneal).

This project was far more enjoyable and less difficult than the CLI Gem.  Maybe I didn't psych myself out this go-around like I did last time. Maybe my skills have improved (that goes without saying). Or who knows what other reasons.  

From idea to completion, I was done in under 2 full days.

There is a lot of room for greater functionality and for better design, but this meets the requirements and is a decent place to start.


