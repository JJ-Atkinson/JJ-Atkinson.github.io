---
layout: post
label: Blog
title: 'Writing a css only firefox theme'
github-uname: JJ-Atkinson
author: Jarrett Atkinson
date: 2016-4-29
categories: ['CSS', 'Firefox', 'Theme']
---

Mozilla has a [tutorial][ff-theme-tut] on building a full theme extension, but if all you want to do is use css, that way is a big pain. For this we will be using [Stylish][stylish] to create our theme, since it can apply css to the firefox ui without a bunch of setup. Once you have stylish installed, click the stylish icon and go to `Write new style` -> `Blank style...`. Paste this into the editor:

~~~ css
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
~~~

This tells stylish that we want to apply our css to the firefox ui, not a webpage. To test it out, try this code:

~~~ css
#TabsToolbar {
    background: #fff !important;
}
~~~

Click the `preview` button at the top of the editor. The titlebar of firefox should turn white.

Ok, so now we can change the style of the titlebar, but how do we inspect the firefox ui to find the stuff we want to style? The [tutorial][ff-theme-tut] would lead you to believe that the only way is to use the [DOM Inspector][dom-i]. However it is a bit old compared to the firefox dev tools.

![DOM Inspector in action][dom-i-pic]

Thankfully, we can use the firefox dev tools [on firefox itself][ff-ui-tools]. To enable this, go to `about:config` and change these:

~~~
devtools.chrome.enabled: true
devtools.debugger.remote-enabled: true
~~~

Now you should be able to go to `Tools` -> `Web Devloper` -> `Browser Toolbox`. You should be prompted with a remote debugging warning. Once you click `Continue`, the dev tools should appear. Now that you have the dev tools, you should be able to style firefox on your own!

 [ff-theme-tut]: https://developer.mozilla.org/en-US/docs/Building_a_Theme
 [stylish]:      https://addons.mozilla.org/en-US/firefox/addon/stylish/
 [dom-i]:        https://developer.mozilla.org/en-US/docs/Tools/Add-ons/DOM_Inspector
 [dom-i-pic]:    /images/writing-a-css-theme-for-firefox/dom-inspector.png
 [ff-ui-tools]:  https://developer.mozilla.org/en-US/docs/Mozilla/Debugging/Debugging_JavaScript#JavaScript_Debugger