---
title: Building an Android
author: joe
layout: post
permalink: /?p=934
categories:
  - programming
  - technology
tags:
  - android
  - eclipse
  - intellij
  - programming
  - virtualbox
---
Before I even get into talking about Android development, I should state that I&#8217;m primarily an iOS developer, and because of that am more accustomed to iOS development styles.

I&#8217;ve been developing Android apps for a while now, and one thing that I&#8217;ve always disliked is Eclipse.  It&#8217;s the [recommended IDE from Google][1], so when I first started developing it seemed like an easy choice.  Since then I&#8217;ve realized that it is bloated, slow, and the exact opposite of what I&#8217;m looking for in an IDE.  For a while I just put up with it, thinking I was as locked in with Eclipse for Android as I was with Xcode for iOS ([which turns out to not be as true as I once thought it was][2]).  Then I stumbled across a beautiful thing&#8230;&#8230;.

<p style="text-align: center;">
  <strong>IntelliJ</strong>
</p><figure id="attachment_722" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-722" title="IntelliJ" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.06.46-PM2-1024x632.png" alt="" width="584" height="360" />][3]<figcaption class="wp-caption-text">My new love affair</figcaption></figure> 

At first I was worried, there didn&#8217;t seem to be a large amount of Android tutorials using IntelliJ, but I heard good things from [Mackenzie Powers][4] and figured I should give it a try.  The thing I had the hardest time with was figuring out how to important 3rd party Android libraries.  Eclipse was easy enough, dropping any libraries I needed into `{PROJECT_ROOT}/libs`.  IntelliJ required a little more setup configuring each library as a module, and then setting each module as a dependency for my application.

But there was another problem, this module/dependency layout doesn&#8217;t seem to compile the same was as Eclipse does.  My existing project that compiled file with Eclipse was giving me all sorts of errors with IntelliJ.  Errors were being thrown around saying I had already compiled the Android-support-v4  library.<figure id="attachment_723" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-723" title="IntelliJ Top Level Error" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.36.39-PM-1024x392.png" alt="" width="584" height="223" />][5]<figcaption class="wp-caption-text">Oh noes! Errors!</figcaption></figure> 

Weird, why was it trying to compile in the support library a second time??  It took me far too long to discover the problem.  After trying to configure a bunch of settings I gave up and tried deleting the library from my project.<figure id="attachment_724" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-724" title="Safe Delete" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.38.52-PM-967x1024.png" alt="" width="584" height="618" />][6]<figcaption class="wp-caption-text">Safe Deleting support-v4</figcaption></figure> 

I was then presenting with this error:<figure id="attachment_725" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-725" title="Error deleting" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.38.59-PM-1024x147.png" alt="" width="584" height="83" />][7]<figcaption class="wp-caption-text">I can&#8217;t let you do that, Joe.</figcaption></figure> 

So that was it! My other 3rd party library was using Android-support-v13, which apparently includes v4 automatically.  The way to get around this in IntelliJ is to just have each module require the same .jar library as a dependency, and then it is smart enough to know to not include the same library twice.  Switching both modules to v13 fixed the issue and I was free to Eclipse!  After resolving all my IDE issues, I only have one other problem&#8230;

<p style="text-align: center;">
  <strong>The Simulator</strong>
</p><figure id="attachment_726" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-726" title="Android Simulator" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.44.10-PM-1024x952.png" alt="" width="584" height="542" />][8]<figcaption class="wp-caption-text">Hanging between screens</figcaption></figure> 

I don&#8217;t have any physical Android devices, nor do I really care to own any.  Problem is, the Android simulator SUCKS.  It&#8217;s terribly slow, and my mom&#8217;s Windows XP Pentium D outperforms this thing by a mile.  For months I dealt with the slowness and just accepted it.  But then I found a 2nd tool that would bring speed to the table: [VirtualBox][9].  I found [a guide][10] that walked me through setting up an [x86 version of Android][11] and configure it&#8217;s network interface to be bridged with mine.<figure id="attachment_727" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-727" title="VBox Setup" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-12.49.42-PM-1024x855.png" alt="" width="584" height="487" />][12]<figcaption class="wp-caption-text">Prepped a VM for Android</figcaption></figure> <figure id="attachment_728" style="width: 584px;" class="wp-caption aligncenter">[<img class="size-large wp-image-728" title="VBox Android Network Interface" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-12.51.24-PM-1024x855.png" alt="" width="584" height="487" />][13]<figcaption class="wp-caption-text">The interface NEEDS to be bridged or it doesn&#8217;t work</figcaption></figure> 

Setting a few screen resolutions available to the VM and restarting left me with an extremely fast Android OS.<figure id="attachment_729" style="width: 584px;" class="wp-caption aligncenter">

[<img class="size-large wp-image-729" title="Android VBox" src="http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.59.29-PM-693x1024.png" alt="" width="584" height="862" />][14]<figcaption class="wp-caption-text">I named it 4.0 and installed 2.3 :</figcaption></figure> 

The only thing more difficult with this is that is doesn&#8217;t automatically connect with ADB.  You can manually connect it by running

<pre>./adb connect 192.168.56.101</pre>

I consider this mild tradeoff completely worth it, as the speed and benefits far outweigh the costs.  Hopefully others won&#8217;t feel stuck with Eclipse and the simulator and can move forward with some tools that are a little more snappy.

 [1]: http://developer.android.com/sdk/installing/installing-adt.html
 [2]: http://www.jetbrains.com/objc/
 [3]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.06.46-PM2.png
 [4]: http://mackenziepowers.com/
 [5]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.36.39-PM.png
 [6]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.38.52-PM.png
 [7]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.38.59-PM.png
 [8]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.44.10-PM.png
 [9]: https://www.virtualbox.org/wiki/Downloads
 [10]: http://amitcs.wordpress.com/2012/12/07/how-to-speed-up-the-android-emulator-by-up-to-400/
 [11]: http://www.android-x86.org/download
 [12]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-12.49.42-PM.png
 [13]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-12.51.24-PM.png
 [14]: http://192.241.141.224/wp-content/uploads/2012/12/Screen-Shot-2012-12-09-at-1.59.29-PM.png