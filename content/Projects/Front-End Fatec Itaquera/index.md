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


# Result


