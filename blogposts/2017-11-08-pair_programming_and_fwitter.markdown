---
layout: post
title:      "Pair Programming and Fwitter"
date:       2017-11-08 15:06:07 +0000
permalink:  pair_programming_and_fwitter
---


Last night I watched as the screen flashed green over and over again.  After looking at 24 red lines for hours, it was a victorious moment, one warrenting a woop and a hollar, if my kids hadn't been sleeping.  This was the culmination of a 12 hours code day, 9 1/2 hours of which were spend on a screenshare in pair-programming with a fellow classmate.

I was looking forward to the experience.  I learn so much with every screenshare with a Flatiron TA - even beyond the curriculum itself.  A command line trick here, a pry command that allows greater efficiency there (such as disable-pry which will skip over the remaining pry's in your code, but still run each spec - compared to exit which aborts the process).

Would our personalities mesh?  (I think we got along quite well and balanced the one screen controls just fine)

Would I hold him back as I'm still not quite sure how I got to this point?  (we had equal imposter syndrome thoughts going on, and I think we were a rather equal match in our abilities - so those worries were unwarrented.)

After 5 straight hours save for a brief bathroom break for me, I felt weariness set in.  Brain fog hit as we'd be in the middle of an error and I'd completely forget what it was we were even troubleshooting.

We wisely took a 10 minute break - that brief time away allow me, at least, to be somewhat refreshed.

We had a lot of code written, but every which way we turned we ran into the same wall.  My programming partner later discovered our error -- we did not specify the user_id within the tweet table.  We were both thinking that was done automatically by ActiveRecord.

A few hours later we were looking at the same 24 red lines with no clue what to do.  Schedule required me to step away for a few hours, and in that time he was able to discover our error.  When I returned we were down to 14 errors!  He made great progress in my 2 1/2 hours absence.

When I returned I took over the tag team, and with the beautiful code he left me, I was able to knock out the last 14 errors one by one with relative ease.  

I'm not sure for my partner, but for me it seemed we reached a natural stopping point for where collective heads were helpful.  For the way I am wired, and after almost 9 straight hours of coding together, it was beneficial to be able to introspect and sort through the code, the errors and resources solo.  I returned to the computer refreshed.

### Takeaways:
1. Breaks are helpful, good and sometimes necessary
2. It's okay to switch up the team game-plan: When a wall is hit, in addition to a break, it may be good for one person to tackle a specific error (or 3 or 5) alone.
3. Extended coding with another person is tremendously informative and I highly recommend it!
4. It is exhilerating to spend a full day coding.

