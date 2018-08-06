---
description: To register event handlers, use the widget.on call within the App’s callback function.
seo-description: To register event handlers, use the widget.on call within the App’s callback function.
seo-title: Adding an Event Handler
solution: Experience Manager
title: Adding an Event Handler
uuid: 0131974d-d13b-4c97-a0ae-c74d0b49674d
index: y
internal: n
snippet: y
translate: y
---

# Adding an Event Handler

For example:

```
Livefyre.require(['fyre.conv#3'], function(Conv) { 
   new Conv(networkConfig, [convConfig], function(widget) { 
      widget.on('<strong><eventName></strong>', function (data) { 
         // Do something, perhaps using data 
      }); 
   }); 
}); 

```
For more information, and for a list of available events, see Reference &gt; Javascript Events.