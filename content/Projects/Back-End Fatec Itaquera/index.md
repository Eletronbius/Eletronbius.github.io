+++
authors = ["Davi Almeida"]
title = "Back-End Fatec Itaquera"
description = "Project Where I worked as Back-End Intern Developer"
date = 2026-06-29
[taxonomies]
tags = ["Back-End", "PHP", "Microservice","MySQL","Internship","SDLC"]
+++

# Situation

This project starts after [this](@/Projects/Front-End%20Fatec%20Itaquera/index.md) project so for more information you should check the Situation on that project.

This project was scoped for a larger team where the approach would be to develop the back-end service for managing the content of the [front-end](@/Projects/Front-End%20Fatec%20Itaquera/index.md).

With a larger team the dynamics would be different we're designed to work on a Pair-Programming style, each pair responsible for a microservice of the website. 

# Task

As previously stated this project is a kind of sequel of another [project](@/Projects/Front-End%20Fatec%20Itaquera/index.md) I worked in.

The task was to create a back-end service for managing the content of the front-end, essentially an admin panel where professors and staff could interact with and update the website content as needed. This was otherwise the responsibility of a single non-technical person, who would work with a WordPress template and add content on top of it, which was becoming progressively messy. 

With this context described, let's get to solution proposed for the project.


# Action

## Architectural approach

Our approach was one of combining [Microservices](https://cloud.google.com/learn/what-is-microservices-architecture) with Replicated Databases using the technique of [Master-Slave](https://dev.mysql.com/doc/refman/9.7/en/replication.html) or Primary-Secondary or Source-Replica depends on which nomeclature you're familiar with, where we divided each microservice as a section of the website, like the Section containing all the content about the Academic Programs offered by the college, this section would be a single microservice responsible for dealing with the information about this topic.

### What's the role of replication in this scenario?

The usage of this technique serves as a two-factor authentication mechanism for content delivered to the main website, where each microservice would have a replica of the main database. Changes would be made on the admin panel and sent to the corresponding microservice, which would then write them on the replica. After the changes had been approved, they would be sent to the main database, which is read by the main application on the front end and displayed to the user.

For example, imagine that a professor changes the description of a class he teaches by adding more information and then chooses to commit those changes. The changes will be held as “To Be Approved” by a system administrator, or whatever you want to call it. This person would be responsible for validating whether the change was made correctly and did not damage any of the website’s content. Once approved, the changes held in the corresponding microservice’s database will have their status changed to approved and be sent to the main database, which contains the website’s current information.

## My role at the project

I developed the microservice responsible for managing the Extensions section of the website, a section which displays information about extracurricular courses taught at the college, free for everyone, including non-students.

The stack used in development was pure PHP due to some constraints <span class="spoiler">(if you're curious about them, I suggest checking out [this](@/Projects/Front-End%20Fatec%20Itaquera/index.md) project)</span>; simplifying a diagram of what this type of communication looks like would be:

<figure>
{{ image(url="diagram.png", alt="simple diagram", no_hover=true) }}
  <figcaption>A simple diagram representing an overview of how things look</figcaption>
</figure>

# Result

Although this was a short project, lasting a couple of months, it was successful and met the provided deadline. We provided a satisfactory foundation for the website with this back-end project, which could be improved further with more time and a team to maintain it in the long term <span class="spoiler">(which did not happen)</span>, creating a kind of micro PHP framework in the long run.

If you have any questions about this project or any feedback to give about this article feel free to talk to me on [LinkedIn](https://www.linkedin.com/in/davialp/).

