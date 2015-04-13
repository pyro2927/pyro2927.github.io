---
title: Breaking When It Should
author: joe
layout: post
permalink: /?p=1011
categories:
  - food
  - motorcycles
  - technology
tags:
  - cloudspokes
  - fuses
  - open source
  - programming
---
Everything breaks, that&#8217;s just the nature of life.  It&#8217;s something you just need to learn to accept, and once you accept that you can learn to work with it.  There is a very important piece of our world that breaks quite often.  That&#8217;s right, I&#8217;m talking about fuses.

While working on putting my motorcycle back together, the electrical system suddenly stopped working.  I didn&#8217;t have time at the moment to look over everything, but I had some time today and two things.

  1. Occam&#8217;s Razor holds true
  2. Sometimes Honda likes to hide fuses in random spots

There is a fuse box on the front of my motorcycle, right underneath the headlight.  There is also a rogue fuse that is clipped inside of the ignition solenoid wiring harness.  After tracking that down I found it to be blown, and while it&#8217;s a bit of a pain as I don&#8217;t have any spares at the time, I&#8217;d rather have the fuse blow than have to replace all of the electrical mechanics that could have been fried.

Tonight Erin and I also were fortunate enough to have dinner with one of my former coworkers Nate, and his girlfriend Toni.  We went to Matt&#8217;s Bar, which is a bit of a famous place in town.  They are home to the Jucy Lucy, which is two hamburger patties with American cheese melted in the core.  It is absolutely delicious, and matched with a pitcher of Summit and a basket of fries, it makes quite the meal.

The bummer news of the week is that I tied for 3rd place in the [CloudSpokes challenge][1] I competed in.  Since my code wasn&#8217;t accepted as a winner, I&#8217;m free to do what I want with the source written for the contest, so [here it is][2]!  It&#8217;s definitely not the prettiest code, but it was a fun challenge in storing OAuth tokens in a postgres database, and then using those access tokens to transfer information at a later time.  Maybe when my server is behaving better I&#8217;ll do a write up the project, but for now I&#8217;m just releasing the source.  If you want to see a working implementation, check out [e2b.herokuapp.com][3].  User credentials can be deleted at any time, so if you become uncomfortable with the access that the webapp has, you can revoke their access.

No one is going to be able to read this for another two weeks anyways, but I&#8217;ll keep trying to post so that there is content once this server is WAN accessible again.

 [1]: http://www.cloudspokes.com/challenges/1671
 [2]: https://bitbucket.org/pyro2927/evernote2box/admin
 [3]: http://e2b.herokuapp.com