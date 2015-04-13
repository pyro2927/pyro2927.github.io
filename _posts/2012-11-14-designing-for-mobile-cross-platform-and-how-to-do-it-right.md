---
title: 'Designing for Mobile &#8211; Cross Platform and How to do it Right'
author: joe
layout: post
permalink: /?p=705
categories:
  - technology
---
The past two days I&#8217;ve attended MobCon2012, and it&#8217;s definitely helped me understand some more things in the mobile realm.  Overall it was a great conference, and I learned a lot while I was there.

A prominent theme that persisted across multiple talks and discussions was cross platform development.  Today development firms have a multitude of cross platform development tools that allow them to write the code once and compile apps for iOS, Android, Windows Mobile, etc.  One that I knew of previously was [Appcelerator][1], and I was introduced to [iFactr][2] while at the conference.  Everyone (including the makers of iFactr) agreed that these technologies were best suited for business driven applications where success is not dependent on a rich UI/UX experience.

Many people might ask &#8220;why?&#8221;  If you&#8217;re going to have two native apps, why the need for two different designs when it&#8217;s the same application?  The heart of the matter is that [Android][3] and [iOS][4] have two completely different design paradigms which can be easily briefed by going over their human interface guidelines.  Below I will highlight a few of those subtle but noticeable differences in these platforms, and hope that designers keep these kinds of differences in mind when designing for different mobile platforms.

**Searching**

<p style="text-align: left;">
  At first search fields may seem simple.  Tap in them, type some text, and click search.  These behaviors and how users interact with them are different on Android than on iOS.<a href="http://192.241.141.224/wp-content/uploads/2012/11/search2.png"><img class="aligncenter  wp-image-707" title="iOS Search" src="http://192.241.141.224/wp-content/uploads/2012/11/search2.png" alt="" width="384" height="540" /></a>
</p>

<p style="text-align: left;">
  It&#8217;s typical for a UISearchBar to be set as the header on a UITableView.  It is easily dismissed while scrolling down, and can be quickly pulled up by tapping the magnifying glass in the alpha scroller (list of characters/icons on the right).  Need to search the list you&#8217;re in, just scroll up!<a href="http://192.241.141.224/wp-content/uploads/2012/11/225614-skyfire-2-0-beta-for-android-android-search-bar2.jpeg"><img class="aligncenter size-full wp-image-708" title="Android Search" src="http://192.241.141.224/wp-content/uploads/2012/11/225614-skyfire-2-0-beta-for-android-android-search-bar2.jpeg" alt="" width="360" height="600" /></a>
</p>

<p style="text-align: left;">
  Search on Android is a little different.  First there is the matter of accessing it.  Search Dialogs are not shown by default in the UI.  They are brought up on the screen via the use of a hardware or persistent software search button (though with device fragmentation it&#8217;s also possible your users will have <a href="http://192.241.141.224/wp-content/uploads/2012/11/HTC-One-S2.jpeg">NO search button</a>).  Next, they are not usually in a scrollable portion of the screen, they become a part of the ActivityBar at the top of the screen, with results shown below.  Finally, it is common for the search itself to be more global.  Where iOS returns results for the view you are on, Android searching often returns results from within any potential part of your application.
</p>

<p style="text-align: left;">
  <strong>Tab Navigation</strong>
</p>

<p style="text-align: left;">
  This is pretty simple, but often overlooked.  iOS has separate UI elements for navigation bars and tab bars.<a href="http://192.241.141.224/wp-content/uploads/2012/11/image002.png"><img class="aligncenter size-full wp-image-710" title="iOS Tab Bar" src="http://192.241.141.224/wp-content/uploads/2012/11/image002.png" alt="" width="405" height="292" /></a>
</p>

<p style="text-align: left;">
  Android typically merges tabs and navigation bars<a href="http://blog.pintozzi.com/wp-content/uploads/2012/11/actionbar_sherlock_navtab_mainactivity.png"><img class="aligncenter size-full wp-image-712" title="actionbar_sherlock_navtab_mainactivity" src="http://blog.pintozzi.com/wp-content/uploads/2012/11/actionbar_sherlock_navtab_mainactivity.png" alt="" width="418" height="689" /></a>
</p>

<p style="text-align: left;">
  <strong>Navigation Stack</strong>
</p>

<p style="text-align: left;">
  The mobile terms for the navigation stack are push and pop for adding and removing views respectively.  Selecting elements/buttons are commonly used for pushing views.  The difference lies in how each OS pops back.<a href="http://blog.pintozzi.com/wp-content/uploads/2012/11/ios-shortcut-button-510x358.png"><img class="aligncenter size-full wp-image-713" title="iOS back button" src="http://blog.pintozzi.com/wp-content/uploads/2012/11/ios-shortcut-button-510x358.png" alt="" width="510" height="358" /></a>
</p>

<p style="text-align: left;">
  iOS shows a back button in the top left of the navigation bar, labeled with the title of the previous view controller.  Android has&#8230;. well&#8230;. nothing.  They don&#8217;t show a back button, they don&#8217;t show the title of previous activities.  Apps (should) just pop an activity off the stack each time the hardware/software back button is pressed.
</p>

<p style="text-align: left;">
  Two exceptional talks at MobCon that discussed these differences (on a higher leve) were done by <a href="https://twitter.com/mikebollinger">Mike Bollinger</a>, and <a href="https://twitter.com/drewy5">Andrew</a> & <a href="https://twitter.com/rexeisen">Jon</a> from the Nerdery.  Mike&#8217;s slides <a href="http://t.co/m8SUQIbv">can be viewed here</a>, and I&#8217;m still waiting for the Nerdery slides to go up.
</p>

<p style="text-align: left;">
  I hope designers start to take note that mobile apps can be designed similar but different across multiple platforms.  Doing so will bring richer and fuller user experiences to mobile users, and will be beneficial to your applications in the long run.
</p>

 [1]: http://www.appcelerator.com/
 [2]: http://itr-mobility.com/products/ifactr
 [3]: http://developer.android.com/guide/practices/ui_guidelines/index.html
 [4]: http://developer.apple.com/library/ios/#DOCUMENTATION/UserExperience/Conceptual/MobileHIG/Introduction/Introduction.html