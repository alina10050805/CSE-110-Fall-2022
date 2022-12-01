# Lab Week 7 - Fetch API & ServiceWorkers

## Introduction

🛠**Today, we'll be learning the basics of network requests, and how to use them efficiently**

In the previous lab we learned how to create reusable web components so that we can dynamically create interactable UIs from raw data. We also learned how to read and write data to local storage so that we can store user changes across page visits. In this lab we'll be adding a little bit of networking on top of that so that we can request data from servers. To keep things local-first though, we'll be managing our own response caches.

Then, we'll learn how to make our website work entirely offline using ServiceWorkers.

## Resources
We will only be linking to more academically minded resources here as they are more likely to have accurate information, but if you find the concept of custom elements a bit confusing there are tons of other resources and videos you’re free to look up and use.

* https://developer.mozilla.org/en-US/docs/Web/API/fetch
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await
* https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers
* https://developer.chrome.com/docs/workbox/caching-strategies-overview/
 
## Set Up

* Join the #lab7 channel on Slack to ask or help answer your classmates' questions
* For this weeks repo to get the starter code
    * https://github.com/CSE110-FA22/Lab7_Starter
 
## Part 1 - Expose (8 points)

### assets/scripts/main.js
**modify this file.**

For this section we highly recommend that you read the resources above regarding **fetch, Promise, async**, and **await**

For this section the initial page load should request the JSON files from the server, but every subsequent page load should read the data from localStorage.

The expose section starts on line **67** with **A1**. The final product should look like the image below:

**NOTE: It is OK if the order is not the same, it can even change in between page reloads. Network requests don't always finish in the order they started in.**

![](./Image/Screen%20Shot%202022-11-08%20at%2011.27.17%20AM.png)

## Part 2 - Explore (2 points)

### Service Workers

Based on the last exercise in part 1, we run into a little issue when building web apps: they are nearly completely reliant on having a network connection. Although we saved the recipe JSON to localStorage, the HTML, CSS, JS, and Image files all came from the network. Actually, based on the principles of RAIL we learned in lecture (and the impatience of humans), we aren’t even off the hook if we have a slow network connection.

This poses a huge problem, since the network capacity of our users is not something we can control as developers, especially with mobile devices that have a much more expensive and slower network capacity than desktop computers. It seems nonsensical for our applications to be 100% dependent on a resource that we 1) cannot control, and 2) fails a lot. 

We can’t fix the internet, so we have to figure out how we can make our apps network resistant, or at least less network dependent. In order to work around this issue, we will introduce some tools that will help us have more control over what our app is able to do when there is no internet connection. These tools are called service workers. 

**In part 2 you will utilize service workers to help your app you made in part 1 function without an internet connection.** 

### Service Workers 👷🏼‍♀️🏗

So JavaScript is single-threaded meaning that any process you want to run has to run one at a time, whether that be synchronously or asynchronously. Many issues can come up when you have intensive tasks that take up a lot of time, this can block the thread and prevent JS from manipulating UI or other things. Service Workers work in the background, separately from the DOM, and allow you to have multithreaded programming. Along with this, they have a functionality we are much more interested in - they can intercept network requests and manage our cache for us without us having to deal with it.

What does this mean?

It means that Service Workers listen in the background for whenever our code makes a request to the internet, and they store that request and its corresponding response inside of your browser. This effectively saves the data on your computer. This means that the next time your code makes the same call to the internet, (i.e. a call for recipes) your service worker is able to remember that this same internet call was made earlier, and can grab the response stored locally in your browser before going to ask the internet for the same data. You can have one simple Service Worker that will act as a guard for any network request and check to see if there’s a version of that data on your computer first. 

### Service Workers are located within the browser

This means that even if your airplane mode is turned on, your service workers will be able to receive the network requests you send out from your web app because those requests don’t need to go over a network in order to reach your service workers. Hypothetically speaking, do you think you could code an entire backend strictly inside service workers and have a full application (frontend and backend) that runs through your browser? (O.o)

### Service Workers are located outside your web app

Service Workers are standalone scripts that are not a part of your actual web application. The only time they appear in your application code is when you register them into your browser when your web app starts up. This is helpful because it allows your web app to continue executing code while the service workers can be designated to handle the slow jobs of making network requests. 

 

### assets/scripts/main.js
### sw.js
**modify these files.**

You will need to begin with **initializeServiceWorker()** in **main.js** before continuing to **sw.js**. All of the Explore numbers start with **B**.

🚀Cool right? Want to know what other real-world web apps out there use service workers? Your browser usually keeps a list, so look up how to find service workers for your browser type (for Chrome, type this in as a URL: chrome://serviceworker-internals/?devtools)

📱You’ll recognize a lot of apps like Google Drive, Google Maps, Facebook, Pinterest, some browser extensions, and others depending on what websites you usually visit. Try turning off your Wifi connection the next time you’re on these sites and explore what happens!

Your final product should look like this:

![](./Image/t-28efsKrN8VYnmboGqkNz8ZKuLgpPs5GX.mp4)

## Part 3 - Expand (No points)

Here are some ideas to expand on this lab that could come in handy based on what application you are building for your project. Feel free to implement any or all of the following:

* Add a **Manifest.json** file to make the application installable with icons and a splash screen
    * Show you accomplish this by taking a screenshot / picture
* Package your application in a desktop app wrapper such as Electron.js
* Integrate with the Web Share API
    * https://web.dev/web-share/
* Once you've made your app installable, try adding some app shortcuts to it
    * https://web.dev/app-shortcuts/
* Generate a PDF from the recipe that users can easily download
 
## Submission Instructions:

Submit a link to your Lab7 GitHub repository on Canvas with the following content:

* Your forked lab7 repo
* README.md in that repo containing:
    * Names of lab partner(s)
    * Deployed GitHub Pages URL