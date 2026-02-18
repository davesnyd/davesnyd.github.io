---
layout: default
title: "Recipe Database"
date: 2026-02-16
---

# Recipe Database
## First application: web-based cookbook application 
### Overview
This is the first in a series intended to explore the approaches, mistakes, and corrections I've encountered while using Claude to do things.

There are many cookbook applications on the internet. Many of them allow for users to enter their own recipes and search and find them.

But I've long wanted one that was simpler, easy to use, and had functionality including import and export of recipes, creation of cookbooks, and improved searching. Plus, eventually, built-in detailed nutritional information.

I wanted to experiment with having Claude create an application using the approaches I had chosen; understand how to interact with Claude; and learn more about what its capabilities are.

### Approach
I created a specification text file. It contained four blocks:

  * Architecture: applications to use: a PostgreSQL database, with a Java Spring business layer and a rich web GUI using the React JavaScript framework
  * Database specification
  * Backend architecture
  * Front end: look-and-feel plus pages to display

It also contained details about what searches and other operations would be supported by the back end.

For the front end, it discussed colors and interface elements. Authentication using Google was specified. It described what fields would appear and where on each page. It listed buttons and what actions they would perform.

I started Claude and asked it to read the specification and flesh it out. What has become apparent is that one of the areas where Claude is especially skilled is in writing documentation, adding details, and fleshing out specifications.

Claude added details, including: how the backend operations are configured, how the information exchange with and within the application occurs, how the containerization of the solution is performed, testing approach, and authentication.

### Process

The implementation process involved a back-and-forth with Claude to get the application developed, have Claude perform whatever testing it was capable of, and manually testing— and finding significant shortcomings that Claude should have found and corrected.

Claude had a compilable prototype complete fairly quickly. Implementing authentication via Google's OAuth was thorny but doable— because it involved integration with an external system, there was a fair amount of back-and-forth to set up accounts, configure the interaction, populate keys, and the like. It seemed like some of the difficulties were due to Claude juggling knowledge of multiple versions of the Google OAuth approach. I think that's a category of problems that is to be expected with Claude. It has learned from a multitude of sources and is trying to find a kind of average approach to performing the task. 

But now, the application allows a user to log in by selecting their Google account. Mostly, I wanted to check how well Claude could handle third-party authentication; I also did not want the application to be responsible for maintaining passwords.

At first, most features didn't work. It required significant feedback to Claude to get it to make the application work. Claude does not do testing of what it writes without specific instructions to do so— but there will be an update on that in the blog post about the photograph application.

Claude also, like all developers, has a tendency to break "that" when it fixes "this". Moving forward, my intent is to have Claude make all changes in a context of test-and-fix, both of the immediate functionality and more globally.

It did many things that I hadn't asked for— mostly, improvements. But it also had some limitations that I had to explicitly request that it remove— for instance, the central text block was limited in width; I asked it, instead, to make it a minimum width but increase up to a fraction of the screen.

I also found myself increasing scope as the process went along— implementing export and import of XML and JSON and also the ability to create PDF of one or more recipes.

Claude can create and run automated test cases. As the development process unfolded, that was a command that I provided it. Claude is also good— scarily good!— at creating documentation. Given that pretty much every human developer with whom I've worked doesn't like doing that, it's clear that one of the huge advantages of working with Claude will be the creation of full documentation of how the application is constructed, how a user should run it and use it, and how to test it. That should be beneficial to developers who manually implement features (if that occurs), users who need to learn and run the application, and support personnel who assist the users.

The project now has documentation for the API, the application's architecture, the database, developers working with the code base, and the components in the interface.

Claude is also supremely good at creating installation packages. Specifically, without being asked, Claude created Docker containers of the three layers in this application (database, backend, and frontend). That will make installing in another system or in the cloud fairly trivial.

### Results

What's the end product? A pretty usable, attractive, functional application.

The user logs in with their Google account. As mentioned previously, that means the application doesn't own authentication and maintaining passwords in its database— which helps decrease its exposure surface.

Once the user logs in, they see a list of the recipes they've added. They can add a new recipe, import from JSON or XML, export to JSON or XML or PDF (the export can be of one or more recipes). For each recipe, they can view, edit, or delete it. They can also import the HTML of a recipe created by the recipe site that I have been using for storing recipes previously— I had Claude implement that so that I can more easily migrate the recipes I've stored in that site.

The recipe viewing is functional and attractive. Ingredients on the right-hand side, steps on the left. An Edit button up top, and the ability to create PDF, export, or share at the bottom.

There are still holes. The creation date on the recipes is not being saved correctly. I need to specify a better way to handle ingredients and nutrition. But, generally, it's functional and useful; it meets the goals I had of creating a recipe application that I could use for my own purposes.

### Putting it all together...

The process— from start to finish— took about 15 hours. It used some technologies that I've used before (Java, Spring, PostgreSQL, Docker) but which I often find it hard to configure and make work correctly. It also uses React— with which I don't have experience. I think if I knew all of these technologies well and had been using them on a regular basis, it would have taken me a few weeks to get this all done. With my lack of deep experience with them, I would budget more like two months.

And the documentation! If you're not a software developer, maybe it isn't clear how beneficial it is to have a dedicated assistant to create complete and useful documentation.

The learnings I took from this were:

  * Rather than have it create the entire application in one pass, write the specification as a list of pieces to have it implement and get working
  * Give it instructions that cause it to work in a more efficient manner and lead to a better, more reliable product
  * Incorporate Claude more tightly in the planning process

I tried to do all of that in the subsequent application (see the upcoming photo blog).

Me? I was pleased with both the process and the outcome. The process— the back and forth with Claude— was painful; but it was short. And the final product is pretty impressive.

