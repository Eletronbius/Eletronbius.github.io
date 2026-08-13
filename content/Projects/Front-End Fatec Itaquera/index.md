+++
authors = ["Davi Almeida"]
title = "Front-End Fatec Itaquera"
description = "Project Where I worked as Front-End Intern Developer"
date = 2026-06-29
[taxonomies]
tags = ["Front-End", "SPA", "JavaScript", "Performance", "Internship","SDLC"]
+++

# Situation

This project was proposed with the idea of modernizing the institution's website. The old website was outdated, and new information was thrown into it without any organization or information architecture. This led to some pieces of information being hard to find, lost, or placed in sections where they shouldn't be. Furthermore, some pages of the website were broken and showing the contents of entirely different pages, several components weren't working as they should, and the navigation bar was broken.

Those are some, but not all, of the problems the website was suffering from. Then, the idea came about to start a project in the institution where students would develop a new and modern website.


# Task

We were given the **task** to modernize the website. But ***how?***

### Tech Stack

You may wonder what technology this project used. Our biggest constraint was that we had to develop everything from scratch without using any libraries or frameworks. One reason for this constraint was the idea that future students could help add features and perform maintenance, <span class="spoiler">which was a good idea but didn't happen</span>. So the technology used was pure HTML, CSS, and JavaScript.

For storage, at first we wouldn't use any type of database because it would be developed in a future project specifically for back-end development, which you can read more about [here](@/Projects/Back-End%20Fatec%20Itaquera/index.md). So, keep that in mind as you read this.

# Action

Given the Task and our constraints and reasons. What was the approach to **solve the problem?**

As we analyzed the website and designed the information architecture we found to be the most usable, we developed our first prototype and set how our navigation bar would look like (at least how we would organize the information).

<figure>
{{ image(url="firstprototype.PNG", alt="This is an image") }}
  <figcaption>What the homepage of our first prototype looked like</figcaption>
</figure>

After we were done with the prototype and gotten the approval of all stakeholders, we began the implementation phase of our <abbr title="Software Development Life Cycle"> SDLC </abbr>.

## A new problem emerged!

As a result of our analysis we found that it would be unreasonable that we create a single HTML and CSS for each page of this project because we would have easily more than 20 pairs of files to manage with a team of 3, so we talked with our supervisor at the time to gather new ideas on how to approach this problem and he suggested that we used a <abbr title="Single-Page Application"> SPA </abbr> framework to develop the website.

Some of the main pros of this approach are that we could have an application that's fast and it could work offline through the use of local cache; some of the main cons would be a slower first load and the potential complexity of managing state and memory, as everything would be managed dynamically. Balancing out our pros and cons, we chose to develop a <abbr title="Single-Page Application"> SPA </abbr> framework. With that, the problem was **solved!**

## My role at the project 

While my colleagues worked on stylization and gathering the information from the old website, my role at the project was to develop the core functions of the framework while assuring that it was performant and could run smoothly.

The solution was based on the [hashchange](https://developer.mozilla.org/en-US/docs/Web/API/Window/hashchange_event) event of the browser which works better than detecting [urlChange](https://developer.mozilla.org/en-US/docs/Web/API/Navigation/navigate_event). So the navigation was based off hashchange, when the user clicks to navigate to other page the browser would only change its hash then it would get detected by the framework and it would change its content.

<figure>
{{ image(url="example.png", alt="visual representation") }}
  <figcaption>A visual representation of how it would look like</figcaption>
</figure>

To get things clearer only the content(green area) is the are where content will be replaced the orange areas are fixed they wouldn't change as the User navigates through the website. 

As now you might understand the solution and I'd hope I got my point across and you understood it, but now **how and where I would store this information?** Simple! Using <abbr title="JavaScript Object Notation">JSON</abbr>!

### Managing storage and dealing with dynamic change

The content of the pages was stored in JSON files, each JSON representing a single page. Once the hashchange is detected, the framework would grab the JSON and pass it to the Page Object, where it would contain all the information from the JSON and would also construct and return the HTML content of the page to replace the older one and show it to the user. Think of it as a kind of a [Factory Pattern](https://refactoring.guru/design-patterns/factory-method). After the Page object initializes, the object would keep the HTML content cached under the object's hood for more performant navigation if the user decides to return to that page, and the JSON would be cached in local storage.

Using that strategy, the main concern of this approach would be, as previously stated, that the first time loading all of the JSON files would take longer

# Result

TL;DR

If you're a nerd about <abbr title="Core Web Vitals">CWV</abbr> we've improved all of those metrics some by a great amount, which you can look below at the images. 
More statistics for nerds:
- `Loading time` became 31% even on the first load of the website before content was cached
- `Navigation between pages` with the use of the techniques mentioned above the navigation was on average and on most cases less than 100ms
- `Speed Index` increased by 47% which improves User Experience leading to better Bounce Rates on Users
- <span class="spoiler solid">due to bad documentation on perfomance tests thats the information I had documented but I've tested exhaustively perfomance</span>

Well due to all constraints and challenges the project was a success and was successful implemented as the new version of the website(<span class="spoiler solid">unfortunately due to lack of maintaners to the project the website was again replaced by a simple template </span>). We've achieved way better results than expected, here are some of them: 

### Core Web Vitals

<abbr title="Core Web Vitals">CWV</abbr> were one of the metrics used for measuring performance:

### Before
<figure>
{{ image(url="CWVold.png", alt="old website", no_hover=true) }}
  <figcaption>CWV of the old website</figcaption>
</figure>

### After
<figure>
{{ image(url="CWVnew.png", alt="old website", no_hover=true) }}
  <figcaption>CWV of the new website</figcaption>
</figure>

I will not walk through each one of those in this article because I don't think that at this point you're someone who neve heard about those metrics, but If you're not familiar with <abbr title="Core Web Vitals">CWV</abbr> don't worry, here are the links you need if you're interested on what those metrics mean:

- [First Contentful Paint(FCP)](https://web.dev/articles/fcp)

- [Total Blocking Time(TBT)](https://web.dev/articles/tbt)

- [Speed Index(SI)](https://developer.chrome.com/docs/lighthouse/performance/speed-index)

- [Largest Contentful Paint (LCP)](https://web.dev/articles/lcp)

- [Cumulative Layout Shift(CLS)](https://web.dev/articles/cls)

### Overrall

Due to bad documentation many of the test results we're not documented properly and ended up being lost at the moment I'm writing this article but the results documented were basically about navigation time and loading time I mention those on the TL;DR paragraph.

If you have any questions about this project or any feedback to give about this article feel free to talk to me on [LinkedIn](https://www.linkedin.com/in/davialp/).