# Making Bookmarklets

I'm feeling very clever. I've got this sweet line of javascript that replaces "butt" with "cloud". My mom would LOVE this but she doesn't computer very well and I'm afraid to show her the Developer Console and have her type/paste this in.

But she IS pretty good at bookmarks, she knows just how to click those!

Bookmarks normally point to web pages. Bookmarklets are bookmarks that run javascript on the current page instead of taking you to a new page. To declare that it is a bookmarklet, the "location" they point to starts with `javascript:`.


## Goal
Take a short javascript script and put it into a bookmarklet


## Try One Out

Install this bookmarklet

Make a new bookmark in your browser (on the bookmark toolbar)
  - For the "Name" you might put "Pinker".
  - Copy the code block below, paste this into the "Location" of a new bookmark.

```
javascript:(function(){document.body.style.background = 'pink';})();
```

Or just drag this to your bookmarks toolbar: [Pinker](javascript:(function(){document.body.style.background = 'pink';})();)

Navigate to google and click the bookmarklet. Voila!



## Let's Make Our Own!

To make a bookmarklet we have three steps:

1. Write some javascript code that you want in a bookmarklet (using the console)
2. Put `javascript:` in front of the code
3. Wrap everything in an [IIFE](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression) so the page doesn't freak out

Here is our cloud-to-butt function:
```
document.body.innerHTML = document.body.innerHTML.replace(/cloud/g, "butt").replace(/Cloud/g, "Butt");
```

Try just putting `javascript:` in front of it
```
javascript:document.body.innerHTML = document.body.innerHTML.replace(/cloud/g, "butt").replace(/Cloud/g, "Butt");
```

> You can debug bookmarklets much faster if you use the Location bar - see "Quicker Debugging" below for caveats.

Partway there! The page did SOMETHING but it seemed to refresh and then the CSS/images didn't load! :(

We can get around this by putting this in an [Immediately Invoked Functional Expression](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression). You don't have to understand this completely to be a bookmarkleteer.

Here are two example ways to write a standard IIFE:
```javascript
(function(){})();
// or
function(){}();
```

Here's the general template I always use:
```
javascript:(function(){CONTENTGOESHERE})();
```

Try it with your cloud to butt code!
```
javascript:(function(){
  document.body.innerHTML = document.body.innerHTML.replace(/cloud/g, "butt").replace(/Cloud/g, "Butt");
})();
```



## Quicker Debugging
Editing the bookmarklet "location" every time you have a code change can be tedious. You can save some time while debugging if you use the Location bar. If it works when you paste into the location bar, it should work as a saved bookmarklet.

Try pasting this:
```
javascript:(function(){
  document.body.innerHTML = document.body.innerHTML.replace(/cloud/g, "butt").replace(/Cloud/g, "Butt");
})();
```

> You'll have to retype `javascript:` at the front of what you paste.

The trouble with the location bar is that it strips "javascript:" from the front of whatever you paste. This probably keeps most people safe from copy-pasting code from the internet willy nilly, but you're writing your own. Hopefully you trust yourself :)



## Editing bookmarklets
When you save a bookmarklet, the browser will remove newlines. If you want to edit a bookmarklet it might be really ugly. You have at least two options:

1. Save a copy of the bookmarklet in a text file on your computer (and in github!)
2. Use a tool like [JSBeautifier](http://jsbeautifier.org/) to make it look nice again. It will put in new lines, indentation, and syntax highlight for you. (but be careful! If you press back in your browser the code is lost. I recommend using this to beautify your code, then that you edit it in a text editor.)
