---
title: Threading in iOS
author: joe
layout: post
permalink: /?p=933
categories:
  - technology
tags:
  - gcd
  - ios
  - threading
---
Threading in applications is important, even more so when your main thread is in charge of doing all of your UI updates.  One common area to experience weak iOS code is in an UITableView that loads content from a remote source.  This post will go over a short sample app that displays a list of the five generations of Camaros, with a picture from each generation.<figure id="attachment_688" style="width: 594px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-688" title="Camaro App" src="http://192.241.141.224/wp-content/uploads/2012/11/Screen-Shot-2012-11-05-at-9.54.02-AM2.png" alt="" width="594" height="988" />][1]<figcaption class="wp-caption-text">Now available in the App Store for $4.99!</figcaption></figure> 

First, let&#8217;s take a look at an example of using no threading whatsoever to load UIImages from a URL.

`
<pre>cell.imageView.image = [[UIImage alloc] initWithData:[NSData dataWithContentsOfURL:[NSURL URLWithString:urlString]]];</pre>
<p>`

Since `tableView:cellForRowAtIndexPath:` is called on the main thread, doing this sort of image load will completely lock up our app until all of the images have been loaded.  iOS only loads UITableViewCells in view though, so our problem gets much worse once we start scrolling.

[kml\_flashembed publishmethod="static" fversion="8.0.0" movie="http://blog.pintozzi.com/wp-content/uploads/2012/11/no\_threading.swf" width="480" height="873" targetclass="flashmovie"]

[![Get Adobe Flash player][2]][3]

[/kml_flashembed]

The video is recorded smoothly, it&#8217;s the application that causes the jagged scrolling as each image loads for every cell brought into view.

Until recently I always backgrounded tasks with `[NSThread detachNewThreadSelector:ToTarget:withObject:]`.  While this isn&#8217;t necessarily a bad solution, it gets really hairy when you start trying to pass multiple arguments.  To background load those images we could use something like this:

`
<pre>NSDictionary *params = [NSDictionary dictionaryWithObjectsAndKeys:urlString, @"urlString", cell, @"cell", nil];
[NSThread detachNewThreadSelector:@selector(loadImage:) toTarget:self withObject:params];
cell.textLabel.text = name;</pre>
<p>`

And then defining the `loadImage:` method

`
<pre>-(void)loadImage:(NSDictionary*)params{
    NSData *data = [NSData dataWithContentsOfURL:[NSURL URLWithString:[params objectForKey:@"urlString"]]];
    UITableViewCell *cell = [params objectForKey:@"cell"];
    [cell.imageView performSelectorOnMainThread:@selector(setImage:) withObject:[UIImage imageWithData:data] waitUntilDone:NO];
    [cell setNeedsLayout];
}</pre>
<p>`

The result is definitely smoother.

[kml_flashembed publishmethod="static" fversion="8.0.0" movie="http://blog.pintozzi.com/wp-content/uploads/2012/11/detachThread.swf" width="480" height="873" targetclass="flashmovie"]

[![Get Adobe Flash player][2]][3]

[/kml_flashembed]

Still, the code is somewhat convoluted, and if we start trying to do multiple things in the background it will become very messy very fast. Enter our savior, Grand Central Dispatch.<figure id="attachment_697" style="width: 303px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-697" title="Grand Central Dispatch" src="http://192.241.141.224/wp-content/uploads/2012/11/4731723114_0f85e1e4312.jpeg" alt="" width="303" height="266" />][4]<figcaption class="wp-caption-text">All aboard the ^()block train!</figcaption></figure> 

With the release of iOS 4 us developers have had the wondrous tool that is GCD.  Sadly, I have not realized it&#8217;s full potential until iOS 6.  The same background threading can be achieved with much cleaner code.

`
<pre>dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_HIGH, 0ul);
    dispatch_async(queue, ^{
    NSData *imageData = [[NSData alloc] initWithContentsOfURL:[NSURL URLWithString:urlString]];
    dispatch_sync(dispatch_get_main_queue(), ^{
        UIImage *image = [[UIImage alloc] initWithData:imageData];
        [[cell imageView] setImage:image];
        [cell setNeedsLayout];
    });
});</pre>
<p>`

It looks scary because some of it follows closer to a C syntax than Obj-C, but if you read it line by line it&#8217;s quite simple.  `dispatch_get_global_queue()` fetches us a queue that we can dispatch tasks (blocks) onto.  Creating an async call with an execution block allows us to perform code without worrying about blocking the UI.  From there we fetch the image data and then dispatch another call on the main thread/queue (retrieved with `dispatch_get_main_queue()`).  Within that block we can update the UI and let the cell know it needs to layout.  The best part about this method is that variable pointers are usable in each block.  We don&#8217;t need to worry about messy pointing passing, instead we can just reference each object with ease.

I&#8217;ve only recently started using Grand Central Dispatch, but it&#8217;s already helped me refactor my code to be cleaner and faster.  I&#8217;m sure I&#8217;ll be using it more heavily as time goes on and I become more comfortable with dispatch queues.

 [1]: http://192.241.141.224/wp-content/uploads/2012/11/Screen-Shot-2012-11-05-at-9.54.02-AM2.png
 [2]: http://www.adobe.com/images/shared/download_buttons/get_flash_player.gif
 [3]: http://adobe.com/go/getflashplayer
 [4]: http://192.241.141.224/wp-content/uploads/2012/11/4731723114_0f85e1e4312.jpeg