# Lab Week 5 - JavaScript DOM Basics and GitHub Actions

The previous lab had you learn the basics of JavaScript as a programming language, but as we know, JavaScript does not live in an isolated environment. In this week’s lab we are going to dive into how JavaScript intersects with HTML in what is referred to as the  DOM (Document Object Model). With this knowledge we’ll finally be able to add some interactivity to our websites! Then we’ll briefly touch on GitHub actions, a topic that should directly aid you in your projects. 

For this lab, it will be important that you have a general idea of what the DOM (Document Object Model) is and how it operates. On a basic level it is an object-oriented abstraction that the browser builds from the HTML that allows you to interact with the document programmatically, but you can read up more about an introduction to the DOM [here](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

 

## Resources
* Audio Element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio
* Audio Element Volume: https://www.w3schools.com/tags/av_prop_volume.asp
* Get Element by ID: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById
* Creating a DOM Tree: https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/How_to_create_a_DOM_tree
* Range Input Element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/range
* Dom Event Listeners: https://www.w3schools.com/js/js_htmldom_eventlistener.asp
* Radio Input Element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio
* GitHub Actions: https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions
 
## Set Up

1. [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) the Lab5 repository: https://github.com/CSE110-FA22/Lab5_Starter
2. Clone your forked repository to your local machine.
3. In your **README.md** add your name and the names of your lab partner(s). See the **Lab 5 Logistics** section above on restrictions regarding choosing your lab partners.
 

## Expose - Party Horn (8 points)

### Instructions

For this part of the lab, you will be implementing a “Party Horn” - a small application that will display a photo and let you play a sound for the party horn that you select. Luckily for you, all of the static HTML, CSS, and Assets have already been created and can be accessed from this repo [here](https://github.com/CSE110-FA22/Lab5_Starter). It is up to you to implement the functionality that we’ve specified below using JavaScript. You can fork our repo or clone it and set up one of your own manually.

Some Ground Rules:

* Do **NOT** modify any of the HTML/CSS files we give you, the lab is entirely possible to be completed without doing so
* You **MUST** use only vanilla JavaScript, no libraries (that we haven’t included for you) allowed
* **ALL** of your JavaScript must be placed within the **expose.js** and **explore.js**  files in **assets/scripts**
 

### Introduction

For Lab5 part 1 we are introducing some basic browser APIs to help you get comfortable with using JavaScript to modify your HTML document based on user actions. Every web browser provides developers with the same standard core of APIs which you will be working with here. The main three we will focus on in this lab are **document selectors, event listeners, and canvas**.

### Document selectors:

Your web browsers offer you the global **document** object so that you can interact with your HTML using javascript. Think of it as the translator between your javascript and HTML, allowing you to read the properties of your HTML elements and update them with JavaScript code. The most common way to interact with your HTML document is through document selectors that allow you to access your HTML elements as JavaScript objects. Here are a few functions that you would find helpful for this lab. 

* [document.getElementById(“id-of-your-element”)](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
    * Returns an html element reference that contains an id attribute that matches the string you passed in
* [document.getElementsByClassName(“class-of-your-elements”)](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
    * Returns a list of element references where each element contains a class attribute that matches the string passed in 
* [document.querySelector("css-selector")](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
    * A very powerful way to use this is to use the attribute selector you used in the CSS lab "['attributeName'='attributeValue']".
    * EX) document.querySelector("[type='radio']") will select an element like `<input type="radio"/>`
    * A pretty diverse selector that selects an element in the same way that you select an element in css. For example passing in "#cool-thing" will select an element with the id "cool-thing".

These are obviously not the only ways to select elements in JavaScript, so if you feel more comfortable using a different syntax you are welcome to. However the functions listed here will take care of everything you need to complete this lab. 

** a helpful tip for document selectors is using **console.log()** to view what was returned by your document selection. These selectors will usually return **null** (instead of an error) when the selector can’t find a matching element, so make sure to check just in case. In addition to that you can also view the properties of that element in order to determine which fields you should be reading and editing. If you look carefully at the object properties can you find anything similar between an element’s JS properties and its HTML definition? **

 

### Event Listeners

Like many other programming languages, JavaScript uses event listeners to conditionally run code based on system events and user actions. In order to define an event listener, you must bind it to an HTML element that is present in your markup. There are a variety of different event listeners that vary from element to element so utilize the documentation we provided via links to help you out. The common syntax for general event handling is as follows:

```
htmlElement.addEventListener(‘event type’, function() {

  // code to run when the event is triggered

}) 
```

Obviously there are other ways to define events and you are free to use them if you are comfortable with other syntaxes. However the one listed here will take care of everything you need to complete this lab. 

There are a wide variety of event types that listen for different events. Some that you might find helpful for this lab are:

* [‘input’](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event)
* [‘click’](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event)
* [‘load’](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Using_images#creating_an_image_from_scratch)
* [‘change’](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/change_event)
 
### Implementation

You may notice an “**init()**” function in your JS files - this is an initialize function. It isn’t called until the whole DOM has been parsed, so it’s a good idea to have your functions / element queries stem from this init() function, otherwise you run the risk of trying to query an element that hasn’t loaded yet.

Requirements:

* When you select a horn from the drop down menu, the following should occur:
    * The correct image should display
    * The correct audio sound file should be set
* When you change the volume on the slider, the following should occur:
    * At zero volume, the mute icon (level 0) should be displayed
    * From 1 to < 33 volume the first volume level should be displayed
    * From 33 to < 67 volume the second volume level should be displayed
    * From 67 and up the third volume level should be displayed
    * The correct volume icon should be set
    * The corresponding volume should be set for the audio element (note: this element’s volume is not out of 100)
* When you click the “Play Sound” button the following should occur:
    * The corresponding sound for the horn selected should play out loud at the specified volume
    * If the Party Horn is selected, confetti should shoot out out, as shown in the video
        * A library has been included for you to accomplish this, more on how to use it here https://github.com/loonywizard/js-confetti
        * Do not run the installation steps, or include the import statement as we have already installed and imported the confetti library for you 
 

## Explore - 2 Points

### Pt 1. Speech Synthesis

For the first part of Explore for this lab, we will be checking out the [SpeechSynthesis](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis) interface of the Web Speech API. We will be making our smiling faced friend on the **explore.html** page talk to us.

### Implementation

Requirements:

* On page load, all of the available voices that you can use for your SpeechSynthesizer should be loaded and populate the “Select Voice” dropdown. (These are browser specific, so you might get different ones browser to browser).
* When you click the “Press to Talk” button, the following should happen:
    * The text that you have typed into the “Text to speak here” textarea should be spoken out loud using the voice that you have selected
* Only while the synthesizer is speaking, the face should swap to being open mouthed (included in the images folder)

### Pt 2. GitHub Actions

#### Introduction to Actions

GitHub offers so many different features for building and managing your codebase. However, as we've seen in previous labs, working with github can get pretty tedious and repetitive, especially when you have many branches, issues, pull requests (PRs), etc. This is where Github Actions come in handy. 

GitHub Actions allows you to automate specific GitHub tasks when something happens to your repository. It’s helpful to think of Github actions as event listeners, but for your Github repository. Events like adding a PR, pushing code, and creating issues can trigger specific processes that makes working with a large GitHub codebase a breeze. 🌬 

#### Instructions

Complete the following course on [Continuous Integration with Github Actions](https://github.com/skills/continuous-integration). 

CAUTION: For the above tutorial, on step 18 (the last step) do not create a pull request and merge your branch until all the bullet point tasks are completed. Once you finish step 18 then you can create a pull request and merge normally. If you merge before finishing step 18 then you won’t be able to complete the tutorial without having the restart it

By following these steps, you should be working in a new repository called **introduction-to-github** (or whatever you decided to name it), automatically created under your GitHub account by GitHub. Make sure to make your repository **public** so it can be graded. Once completed, **add the link to introduction-to-github repository in your README.md file from your Lab5 repository**.

 

Let’s start!

https://lab.github.com/githubtraining/github-actions:-continuous-integration

## Expand - No points

Answer the following questions to the best of your abilities, please write complete answers with adequate detail. Put these in a file titled **expand.md** and place it in the root of your repo.

1. Why is it important to put thought into your IDs & Classes when it comes to technology intersections? (e.g. how HTML, CSS, and JS intersect)
2. What are Data attributes? Why might they be useful? How do you access them? What are the implications of using Data attributes when it comes to things like microdata?
3. What is a DOM fragment? Why are they powerful?
4. What is the point of a “Virtual DOM”? What do you gain? What do you lose?
5. In JavaScript, usually you can reference every attribute of an element with a dot selector followed by the attribute name, except for the class attribute, which is className. Why is this so?
6. What is the difference between using addEventListener() and something like onClick() ? What are the advantages / disadvantages of both?
 

## Canvas Submission:

Note: Before turning in your submission, enable GitHub pages for your repo so that we can test your code. Instructions for where to include the link to that pages site below.

One submission per lab group. Submit a link to your Lab 5 public repository containing:

* Your forked / cloned repo of ours with your modified expose.js and explore.js files (no other files should be modified, explore.js is optionally modified)
* expand.md in the root of your repo (if completed)
* README.md with:
    * names of you and your lab partner(s)
    * link to your Continuous Integration introduction-to-github repo
    * link to your github pages site expose.html page (as well as the link to explore.html if completed)
    