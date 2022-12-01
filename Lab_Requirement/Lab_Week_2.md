# Lab Week 2 - HTML and DevTools

This is to be completed as a solo assignment.

The previous lab assignment had you creating a GitHub User Page using Markdown. For this week’s lab assignment, you’ll be exploring the basics of HTML and Chrome DevTools. The purpose of the first part of this lab is to get you familiar with the basics of HTML, as well as some of the lesser known parts. Your primary goal will be to explore and practice correct syntax and usage of tags, properties, links, etc. over visual execution. The second part of this lab will acquaint you with the Chrome DevTools by going on a scavenger hunt through a site that we’ve set up to find some hidden secrets. You may technically use any browsers’ DevTools for this section, but this lab will be written with Chrome DevTools in mind.

 

## What Do I Learn? Why Do I Care?
Objectives:

* Learn HTML
    * HTML is the foundation of both your documentation and your application
    * HTML is a core technology in web development - in fact, it is what JavaScript tends to emit / manipulate
* Learn DevTools
    * Debugging anything on the web requires using the browser's Developer Tools
* Proper Web Dev foundation
    * Learning advanced or resume specific things is much easier + faster if you have learned the foundational skills first
 

## WARNING:

Read the write up thoroughly before asking any questions!

Also make sure to check out the Q&A section down below.

 

## Resources
[HTML Basics](https://www.freecodecamp.org/news/html-basics-for-beginners/)

[Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

[Official HTML Specification](https://html.spec.whatwg.org/multipage/)

[W3C's HTML Validator](https://validator.w3.org/)

 

## Getting Started: Intro to HTML/DevTools

 

Disclaimer: The intro videos for the following labs should be a little shorter as this week's intro includes a general intro for the next few labs.

 

### Set Up
1. [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) the starter repository for Lab 2 here: https://github.com/CSE110-FA22/Lab2_Starter (only follow the tutorial through step 2. You don't need to sync your repo with the starter repo).
    * **NOTE:**  If you forked the repo properly, you should now have a copy on your GitHub account. If you attempt to push changes to the original lab repo we will close the pull request without saving and you will lose your progress.
2. You might find the VSCode extension [LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) useful for this and future labs. You can use this to open your html file while editing and see live changes.
 

## Part 1. Intro to HTML - Meeting Minutes

In this section, you will be building a simple webpage representing the meeting minutes for a sample team. When building this, your site must use valid semantic and structural HTML. You should be handcrafting your site and **not using** [Cascading Style Sheets (CSS)](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS), [JavaScript (JS)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript), or any [frameworks](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks). Don't worry if you haven't used HTML before; use the links from the **Resources** section above and the web to your advantage. 

**Why are we writing the minutes with HTML (.html) instead of Markdown (.md)?** In your normal teams you will be writing these with markdown, but for this lab since we want you to learn HTML you will be using it for this lab.

**What do we mean by meeting minutes?** Meeting minutes are notes recorded during a meeting so that anyone who missed the meeting can easily catch up, or if someone needs to reference back to a meeting that happened a little while ago they can jog their memory.

There is no one true way that we want you to write your meeting minutes. Find one that you like that meets the criteria below and go from there.

**NOTE:**  The use of CSS or JavaScript in this lab is **strictly prohibited**. Yes, this includes using the style attribute, any of the on___ attributes (e.g. onClick), the style tag, and the script tag.

Traditionally, a meeting note includes:

* a title (e.g. "Pomodoro Timer First Brainstorm")
* subtitle for the meeting section/the topic of the meeting (e.g. "brainstorming", "check-ins", "documentation")
* subtitle for the date
* attendance list
* agenda of what the meeting will cover
* things that were unfinished business from last meeting
* things that are new business that need to be talked about
* any miscellaneous comments / questions / concerns that anyone would like to bring up
* pictures of any diagrams / architecture / things that were presented
    * SWE meetings often have people diagram things on a whiteboard so we want those captured as well
* For the following two, you can simply take a 30 second pretend audio recording & video recording to use, we are just trying to get you familiar with the `<audio>` and `<video>` elements. Yes, you must have **both** audio and video elements, and yes, you can use the audio from the video you took for the audio element, it just has to be in a separate audio file.
    * audio recording the meeting
    * video recording of the meeting

## Creating an HTML Document

Here is a simple basic skeleton for you to start off your HTML document with.

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title></title>
  </head>
  <body>
  </body>
</html>
```

**Key Terms:**

1. **`<!DOCTYPE html>`** : all HTML documents must start with a document type declaration
2. **`<html lang="en"></html>`** : the HTML document starts and ends with the `<html>` element, also known as the root element. The lang attribute declares the language of the page.
3. **`<head></head>`** : contains the document metadata, which is not displayed to the users.
4. **`<body></body>`** : contains the content of the page that is visible to users.
 

## HTML Basics

HTML files are composed of HTML elements.

HTML elements are composed of 3 parts:

* **tag**: the specifier for which element is being used, enclosed in <> symbols. 
    * Header1: `<h1></h1>`
    * Paragraph:` <p></p>`
* **content**: the content within an HTML element, can be text content or other HTML tags
    * `<h1>This is the main header content for my page</h1>`
    * `<ol>    <li>list item</li></ol>`
* **attributes**: used to further differentiate elements from one another/adds additional functionality to an element
    * `<div class="main-container"></div>`
        * allows you to select this element by its classname
    * `<img src="path/to/image.jpg" alt="describes the image being shown for screen readers, or if the image can't be displayed"/>`
        * specifies a path to the image and alternative text if the image cannot be displayed or if a screen reader is used
 

## Common Useful HTML Elements

Your website needs to include **at least one of each of the following HTML elements -- one of each that are explicitly listed, not just one from each section** (you are allowed to use other elements not listed here as well).

Note that you must use these elements properly on top of them being valid, such as making sure that your header element goes at the top of your page and similarly making sure that your footer element goes at the bottom of your page. Be creative with your usage of the elements to make this exercise more enjoyable. 

 

### Document metadata

Metadata elements are not rendered to your webpage, rather they are used by the browser to provide extra information to your webpage like a title and icon in the browser tab bar or a description of your website

* title
* meta
* link (usually `<link>` is used to link a stylesheet, but since we're not using CSS, you can use it to link a favicon instead)
 

### Content sectioning

Sectioning tags are necessary for your browser to correctly understand the structure of your webpage. Correct webpage sectioning helps in areas like Search Engine Optimization. Note that the way that you section your webpage does NOT have to be exactly how the webpage is structured visually, rather think of your section elements as a guide to your web browser on how your page should be interpreted.

* main
* header, footer
* nav
* h1, h2, h3
* section
 

### Text content

Text elements help you format your text content allowing you to add styles and structure to how your text is rendered to the screen. A lot of these elements will produce the same effect visually, however remember that we are writing our HTML for the web browser so make sure to check out the Mozilla documentation to understand when to use each element. Your visual aesthetic can be developed using CSS - but we won't be using CSS for this lab :)

* div, span (these elements may not be too useful without CSS / JavaScript, but are too important to leave out, so just include them somewhere in your document. It’s okay if they aren’t useful)
* hr
* p
* ul
* ol
* li
 

### Inline text semantics

Inline text elements are used inline with your text to provide meaning to specific parts of a text section.

* b
* strong (know the differences between b and strong)
* i
* em (know the differences between i and em)
* a
* br
 

### Images and multimedia

* img
* audio
* video
 

### Interactive Elements

Interactive elements provides your webpage with some basic interactive functionality without the use of Javascript. 

* details
* summary
 

### Forms

This isn't really related to the concept of meeting minutes, but we want you to include it anyways as forms are a crucial aspect of HTML. The form itself doesn't have to be related to your meeting minutes at all and can be about whatever you like. Create a simple (non-functional since we're not using JavaScript) form at the bottom of your page. Use the following elements:

* form
* fieldset
* input (of types checkbox, radio, text, and date)*
* textarea
* datalist
* select
* option
* button

*You need to have at least one input of each type specified. 

 

## Wrapping Up
Finally, **publish your site** to GitHub Pages and run your site through the [W3 validator](https://validator.w3.org/). You must pass the validation - warnings are fine but errors are not.

** **Include the screenshot of the W3 markup validation report in your submission.**

**NOTE:** DO NOT unpublish your previous lab, just create this lab as a new URL on your GitHub Pages (this should happen automatically based on the name of your new repository). Your new URL will be in the format: `https://<username>.github.io/<repository-name>`.

OPTIONAL: If you find yourself wanting to go above and beyond, here are some things you can do:

* HTML Minification
* Accessibility check and report
 

## Part 2. Exploring the Browser Developer Tools
For this part, you’ll be conducting a simple scavenger hunt to find passphrases on a website that we’ve hosted on the following URL: https://cse110-fa22.github.io/Lab2_ScavengerHunt/

The site contains a total of 12 hidden passphrases. Simply find the corresponding passphrase with your [Browser Developer Tools](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools) and record them in the part2.txt file. While you’re looking at this page, know that all of the HTML is valid, nothing you see is disallowed.

**Hint:** Not every solution is hidden in the same spot, explore the DevTools and look at different tabs such as Console, Elements, Sources, Network, etc...

## Canvas Submission:
* Submit a **link to your Github repository**. Your repository should include:
    * a **screenshot** of the W3 validation report inside the screenshots directory
    * an **index.html** file with your completed work for Part 1
    * a **part2.txt** file with your answers for Part 2
    * a **README.md** file with the URL to your published site
    * any other assets for part 1
 

## Questions & Answers
#### Q: Is there a specific meeting minutes format that I need to adhere to?
A: No, so long as it includes the information that we specified above, you're free to go find a format you like online or create your own. The key is consistency, it's important that all of your meeting minutes follow the same format so they're easy to read and understand.

#### Q: Is it ok if my assignment looks bad?
A: Yes! HTML is about the content of the website, assignment semantic meaning and structure to the raw text. It is NOT about visual rendering, that is the job of CSS. So do not fret about looks yet.

#### Q: Is there a specific final product my assignment should look like?
A: Nope, don't worry about trying to fit some mystical perfect assignment, everyone's will look different and that's ok.