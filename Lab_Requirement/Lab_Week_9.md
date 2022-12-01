# Lab Week 9 - JavaScript Error Handling, Monitoring, & JS Docs

Client-side JavaScript executes in a relatively uncontrolled environment and many things can and do go wrong.  Some of these issues have to do with the ever shifting challenges with browser updates while others have to do with the time pressure of building software which often results in release improperly tested software.  Whatever the reason, faults can be found in client-side code and you should be more aware of how to handle them.  

To learn how to deal with errors a bit better we are going to continue our exploration of JavaScript error handling in this lab by looking at

* More advanced use of console object including `console.log`, `console.error`, `console.table`, `console.dir`, `console.dirxml`, `console.group` (includes related functions to use properly), `console.time` / `console.timeEnd`,  and `console.trace`.  A full reference of the `console` API  can be found online including at [Console API Reference](https://developer.chrome.com/docs/devtools/)
* Use of try/catch/finally - See [Error handling, "try..catch" (javascript.info)](https://javascript.info/try-catch)
* Use of throw - See link above
* Use of Custom Error messages - [Custom errors, extending Error (javascript.info)](https://javascript.info/custom-errors)
* Use of 3rd Party JavaScript monitoring services - [JavaScript Error Logging - TrackJS](https://trackjs.com/)
 
## Expose + Explore (10 points) - Combined this week since the lab is short
 

### Step 1 - Set Up

First, clone the starter code here: https://github.com/CSE110-FA22/Lab9_Starter

You are allowed to modify any part of this code as much as you like, it's simply a starting point.

Next, make sure to host your example online on Github Pages for later steps and grading.

### Step 2 - Adding Buttons for Console Testing

Now for each of the buttons in the starter code give functionality to them that correspond to each of the `console` methods we listed previously (`console.log`, `console.error`, `console.table`, `console.dir`, `console.dirxml`, `console.group` (includes related functions to use properly), `console.time` / `console.timeEnd`,  and `console.trace`.).   The idea being is you press a button that says "Console Log Demo" and it performs that method on some data in your example.

### Step 3 - Trying Try/Catch

Next explore the use of `try`/`catch`/`finally` and `throw` in your program.  Before you do this, read the article referenced as it may work differently than Java.  To trigger an error you may need to do something like comment out a DOM node with an HTML comment or manipulate the program unexpectedly.  Try to make your example more realistic than just inserting some code like `aintGonnaWork();` and watching it error.

### Step 4 - Throw and Custom Errors

Now explore the use of `throw` and extending the `Error` object to use a custom error type.  The article here does a good job of explaining how this goes: [Custom errors, extending Error (javascript.info)](https://javascript.info/custom-errors)

### Step 5 - The Global Error handler and 3rd Party Tracking

It has long been possible to catch errors happening client side and transmit those errors some place else.  The Professor wrote a book many many years ago that has a demo that shows this happening directly -  http://ajaxref.com/ch2/jserrorreporter.html In the example you'll notice the use of `window.onerror` and how once that is caught you can collect the message and send it some place using `fetch` or `XMLHttpRequest` APIs.  First demonstrate that you see how to catch such an error that way in a simple manner and just log a message to `console`.

Once you understand the concept sign-up for a trial at an error monitoring service - we are suggesting TrackJS ([JavaScript Error Logging - TrackJS](https://trackjs.com/)).  Insert the tracking script into your example program and once you have it working take a screen capture that shows the reporting side of TrackJS is capturing the errors you trigger in your example project.


#### Tips

To give you a sense of what the functionality of the app might look like, a demo video has been provided below. Note: `window.addEventListener('error')` is also demoed in this example.  You do not need to mirror the video exactly, the point is to show your knowledge of the error APIs and constructs and there are many ways to do it that may be better or easier for you than what I did here.

![](./Image/t-T2GXjA96RXUaohZ4YJM2QGRcVaJPBDa.mp4)

## Expand - (No points)

Some ideas for ways you could improve your error logging:

* In your universal error logger, write these logs to a local store or send them to an endpoint to save (you can also look up writing to disk but the permissions for this is browser dependent)
* Try out the various logging SaaS vendors (Loggly, Datadog, etc) as a dashboard for your errors
* There are ways to style your console logs (check out [pint.com](https://www.pint.com/) and [zingchart.com](https://www.zingchart.com/)) - try styling yours

## Submission

Submit the link to your GitHub repository containing your code and relevant screenshots. Publish your site through Github Pages and include the published URL in a README.md file to facilitate grading.