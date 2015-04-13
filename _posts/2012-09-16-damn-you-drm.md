---
title: Damn You DRM!
author: joe
layout: post
permalink: /?p=555
categories:
  - technology
tags:
  - drm
  - windows
---
I hate DRM of all kinds, but the most frustrating recently has been Windows 7 activations.  While I don&#8217;t have a problem with product keys themselves, Window&#8217;s self-checking of changed hardware has been driving me crazy when dealing with [virtual machines][1].  My VM software of choice is [Parallels][2] (though [VMWare Fusion][3]is also a good one), and since the hardware in my physical desktop and virtual machine differ, Windows finds a hardware change and deactivates itself.<figure id="attachment_556" style="width: 628px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-556" title="windows-7-activation-by-phone-united-states" src="http://blog.pintozzi.com/wp-content/uploads/2012/09/windows-7-activation-by-phone-united-states.png" alt="" width="628" height="549" />][4]<figcaption class="wp-caption-text">Damn you Windows!</figcaption></figure> 

&#8220;OK&#8221;, you might think, &#8220;Just reactivate online, not a huge ordeal.&#8221;  That works, but only a handful of times, in my experience thrice, before online activations stop working.  Then you have to call the Microsoft activation hotline and talk to someone on the phone.  Again, not the worst thing ever, but due to the fact I use this instance of Windows both on physical hardware an inside of a VM, I have to do this whole song and dance about once a week.

Getting frustrated with this I figured something had to be done.  I knew that Windows activations were stored in files somewhere, so backing up the activations before they self-destroy should be as simple as copying a few files, right?  It is!  And it becomes even easier with [Advanced Tokens Manager][5].<figure id="attachment_557" style="width: 428px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-557" title="ATMv3.5B2" src="http://blog.pintozzi.com/wp-content/uploads/2012/09/ATMv3.5B2.png" alt="" width="428" height="356" />][6]<figcaption class="wp-caption-text">Back dat act(ivation) up!</figcaption></figure> 

Hardware changes will still be recognized, with with ATM I can backup the activation files relating to each hardware setup.  Once copied over onto my NAS I can restore either activation simply by running ATM again.<figure id="attachment_558" style="width: 743px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-558" title="Screen Shot 2012-09-16 at 4.33.30 PM" src="http://blog.pintozzi.com/wp-content/uploads/2012/09/Screen-Shot-2012-09-16-at-4.33.30-PM.png" alt="" width="743" height="460" />][7]<figcaption class="wp-caption-text">Safely backed up!</figcaption></figure> 

Goodbye Microsoft Activation Hotline!

 [1]: http://en.wikipedia.org/wiki/Virtual_machine
 [2]: http://www.parallels.com/
 [3]: http://www.vmware.com/products/fusion/overview.html
 [4]: http://blog.pintozzi.com/wp-content/uploads/2012/09/windows-7-activation-by-phone-united-states.png
 [5]: http://www.joshcellsoftwares.com/2011/09/AdvancedTokensManager.html
 [6]: http://blog.pintozzi.com/wp-content/uploads/2012/09/ATMv3.5B2.png
 [7]: http://blog.pintozzi.com/wp-content/uploads/2012/09/Screen-Shot-2012-09-16-at-4.33.30-PM.png