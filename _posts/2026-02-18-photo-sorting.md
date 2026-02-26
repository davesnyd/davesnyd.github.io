---
layout: default
title: "Photo Sorting"
date: 2026-02-18
---

# Photo Sorting Application
## Second Claude-created application: submit, organize, and display photographs
### Overview
For a second application, I wanted to experiment with an approach to allow users to submit files, remotely, using the Git application. I also wanted to begin a process of creating an application that would allow me to categorize and organize photographs in a searchable fashion so that I could better locate a specific image or set of images.

The goal was to allow images to be submitted remotely, analyzed with an AI-enabled script to determine information about their contents, extract EXIF information when present, store the photographs in a common directory, and put all available metadata in a database with a link to the photograph.

I also wanted to experiment with both some of the techniques I had read about for interacting with Claude as well as some ideas I had had for improving the Claude interaction when I worked with it, previously, to create the recipe database application.

### Approach
I created a specification file. Although it was a text file, I gave it the MD suffix of a markdown file, because Claude seems to prefer to use markdown files as their input. IIRC, I wrote a few hundred lines. 

I also created a CLAUDE.md file, which is the preferred way of providing Claude with instructions about how to work. It was about one hundred lines.

The specification file started with non-functional requirements, including scalability and security, with specific instructions to use Google OAuth for logging in. It also had a list of components to use. I specified a PostgreSQL database, Java Spring Boot backend with Hibernate ORM to connect to the database, React JavaScript frontend, STAG Python package for analyzing photographs, and Git for file transport.

There was a section for color scheme and a description of the step-by-step workflow. Also, the standard interface components for each page were described.

As with the <a href="https://davesnyd.github.io/2026/02/16/recipe-database.html" target="_blank">recipe database</a>, the API endpoints of the backend were listed.

Finally, the specification then continued about fourteen blocks of functionality to develop, in an iterative fashion. It started with a description of the database tables and columns and then contained a list of each web page in the application with details of what was on it, what the components would do, and, when appropriate, how they would interact with the backend.

Most importantly, each block of functionality contained a list of test cases to verify correct working of the code implemented as part of this piece of implementation.

That's the "what" of the development. But the "how" is contained in the CLAUDE.md file.

The CLAUDE file contained an overview to set context: that development would occur in an iterated fashion, rather than all at once, the name of the specification file, and a brief rundown (briefer than above!) about what each step in the specification contained.

It then described some files to be maintained by Claude during development: a worklog (to allow for resumption of effort if it was interrupted), a learnings file (to help improve future development), and documentation.

I then used some ideas I had culled from reading about other users' CLAUDE files: focused Claude on writing a robust application, not breaking existing functionality while creating new functionality, discussed the components for the different tiers of the application, discussed the importance of testing, and instructed it to use meaningful names for fields and methods— to make it easier for developers to work with the code.

Then, came the heart of the document: step-by-step instructions for implementing each chunk of development. While you can read the full document in the <a href="https://github.com/davesnyd/PhotoSort-V1" target="_blank">Git repository</a>, in short: focus on testing; plan, discuss with me, implement, and add to the test cases; enter a test-and-fix cycle until all of the current tests are successful and then do the same with previous tests; update the documentation; and push the code to Git.

Git is being used to transport files because it's a readily available system that is good at working across networks, through firewalls, with secure connections, and maintains context for the files.

By extracting EXIF information, we can include date and place and other information about how the image was taken.

The <a href="https://github.com/DIVISIO-AI/stag" target="_blank">STAG package</a> is an openly available Python script that uses a custom AI tool to analyze photographs for content. Currently, it's limited to detecting broad brush strokes of what's in a photo— a person, or a specific object. But it can't recognize individuals. That's the eventual goal for this application; STAG is a placeholder until that's available.

### Process
Write the specification and implementation guide (Claude.MD) markdown files.

Discuss both with Claude. Have Claude rewrite them. In doing so, Claude increased the size of both files by factors of five-to-ten. It added details to both documents (for example, specific versions of the infrastructure frameworks), made them more specific, reorganized them (the specification, for instance, went from primarily paragraphs to an organized outline). 

It reorganized the table specification from a rough list to a field-by-field specification. It added specifics about the API endpoints. It started listing specific classes to create. And so on.

To the Claude.MD, it added infrastructure specifics. It detailed the code directory hierarchy. It gave specifics about how to build the solution, and it provided details about its output files.

Then, I told it to start.

The primary insight I had before starting was to instruct it to enter a fix-test cycle after implementing code. In short, I wanted it to make sure that the set of tests to run were as complete as possible as part of the implementation and that coding wasn't complete until all of the tests passed. Plus, all previous tests— to make sure the "new" development hadn't broken any of the "existing" functionality.

I've since learned that pattern has a name—<a href="https://paddo.dev/blog/ralph-wiggum-autonomous-loops/" target="_blank">"Ralph Wiggum"</a>. In short: keep entering fix-test cycles until the tests pass.

In practice, Claude didn't always follow this instruction. True RW implementations— as opposed to my ad-hoc approach— work one of two ways: using a skill added to Claude to guide it, or using an external shell script to do so.

My understanding is that the external shell script is much preferred— it helps to force Claude to have a clean context each time. My admittedly lightweight request to implement something like RW likely has problems similar to (and maybe more so) the internal skill extension.

In the end, I felt that there was still significant need for me to "hold Claude's hand" and instruct it to keep working until it had fixed obvious errors I encountered during cursory testing. I don't think that should have been necessary, had Claude really performed in the fix-test cycle mode I had requested (the ad-hoc RW).

But converge we did— in about ten-to-twenty hours, including design and planning.

As with the <a href="https://davesnyd.github.io/2026/02/16/recipe-database.html" target="_blank">Recipe database</a>, I'm impressed with how much it was able to implement in a short time. My best guess is, again, that it would take me weeks-to-months to do this on my own.

### Results

The application works, it works well, and it is visually attractive.

It has all of the pages I had requested and all of the user components. It uses the color palette I had requested.

Logging in uses OAuth in Google— so any user with a Gmail account can log in. Interestingly, it implemented a login screen set that was somewhat different. Recipe has a popup window; Photo just goes page-to-page.

Unlike with the Recipe application, Claude didn't automatically containerize the solution. That required an additional request.

### Rolling it all together...

In the end— I think this is another success. For much less time than it would have taken me to build and get this application working, I had a functional, attractive application.

The solution is fully documented, there are scripts to build and deploy it, and it was iteratively stored in GitHub.

What I think I learned was:
* The specification is key. The better the specification, the more complete the output.
* Include more details that are desired— specification of the OAuth login and creation of containerized installation artifacts— in the specification.
* The largest area for improvement is the fix-test cycle loop. Since I have subsequently learned of the Ralph Wiggum methodology, it's clear that I need to formally incorporate that in future development cycles.

In the end though, even without those improvements, I'm seeing a significantly useful workflow emerging from these application creations.


