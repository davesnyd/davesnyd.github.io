---
layout: default
title: "How does AI Create Software?"
date: 2026-02-15
---

# How does AI Create Software?

## AI code generation tools are changing the way that software is developed— but how does it all work?

### What are AI code generation tools?

It seems like there are an infinite number of different AI code generation tools out there. Every one of the AI model creating companies seems to have their own tool— or set of tools to enable generation of software.

But, largely, there are two-ish categories of AI code generation tools and how they're used.

There are the integrated assistants. They live in the developer's code editing software— the Integrated Development Environment. Since the most used IDE is Visual Studio Code— followed by Visual Studio— it makes sense that Copilot, the Microsoft AI digital assistant which integrates directly into VS Code is the most common form of IDE integrated AI assistant. Other IDEs often have their own AI assistants, though Copilot is available in many of them as well.

Copilot is also available in other Microsoft software. The AI that it uses out of the box is OpenAI's GPT model, the same technology behind the commonly used ChatGPT.

The other broad category is stand-alone AI. The one that seems to have captured the most mind share of developers is Anthropic's Claude Code— but Codex (also from OpenAI) and the Gemini CLI (from Google) are other examples.

These tools start up from a terminal's command line (which could be embedded inside an IDE) and can create, write, edit, move, and delete files; as well as commit them to Git.

There are also stand alone tools in web or desktop interface that handle soup-to-nuts code generation. Cursor, Windsurf, and Bolt are examples.

### How are AI code generation tools created?

So, like other AI applications, code generation pulls together an engine (a Large Language Model or LLM) with a natural language interface and knowledge of how to read, write, test, and debug software. *See, for example:* <a href="https://davesnyd.github.io/2026/02/15/what-is-ai.html" target="_blank">AI primer</a>

If you want an AI that will predict weather, you train it on a dataset of all the weather encountered everywhere— so that it can predict tomorrow's weather from the weather it sees today. You then add in rules of the physics of meteorology.

But if you want AI that can generate software, you train it on a dataset of every software code file to which you have access. Primarily, that's software stored in openly browsable repositories like GitHub and any open source software for which the source code has been posted to the internet.

There's a lot of code out there. But it's worth realizing that it's... a lot of similar code? If you've used open source applications— that's a lot of what's there. But the really specialized applications? The ones, at work, that do something specific in your domain of expertise? Not so much, most likely.

That's relevant because AI code generation is going to be best when generating code that's like the code in its training set. So if it is asked to generate something like the 8,000 TODO application websites that it was trained with— it's going to nail it. But if you ask it to do the specialized analysis of your corporate restocking approach— then it's going to require significant hand holding.

Also, AI systems, in general, aren't perfect. For code generation, they won't get it right— developers experience significant need for rework in order to make the output work correctly.

They also have nature-of-the-beast issues. The most prominent is what's called "hallucination", when they make up answers and solutions that have no basis in reality. That can lead to nonsense code that uses nonexistent components and calls software functions that either don't exist or don't work the way the AI claims.

That leads to an expectation that developers will test, review, and verify the output of the AI generation.

### How are AI code generation tools used and how do they work?

The in-IDE tools act as immediate assistants. They perform auto complete of code as the developer types. They can be triggered to do specific tasks— sometimes by menu selection ("refactor the code base" or "generate test cases") or by making comments that the IDE interprets as directives.

The stand alone tools are used in a more conversational, interactive fashion. The developer provides the tool with files that define the way it is supposed to work and details for how it is to do its development. Then, they engage in a back-and-forth about what to do. The tool will then edit the current code base or create a new one. 

They work by using their language processor to understand what the developer is requesting. Then, based on the information in their training data, they predict the output— code, tests, or investigation, that is the best fit to meet the request. That's what people mean when they say that AI systems are glorified "auto complete". It isn't accurate— but it sums up the concept that the AI system is using inputs and training to predict an appropriate output.

### What are they good at and what are their limits?

The AI code generation tools are really good at generating code that's like code they've encountered in their training.

They're also good with generating code in languages which were well represented in the training data.

Where they don't have experience, they don't do as good a job at generating code.

If you're working with a very specific application— data analysis, communicating with an embedded hardware system, or interpreting the results of a communication that they haven't been exposed to— a developer ought to anticipate having to be more involved in the writing of the code.

AI tools are novel, powerful, awesome, terrifying, and game-changing. 

They lead to a new way of developing applications. Developers can do that development faster than before, with languages they don't know in detail, and using frameworks that they aren't expert in. But the development can also go off the rails. And it requires a completely new way of working— changing the roles and responsibilities of the developers.

The tools aren't perfect— but what they're capable of, even at this early stage, is awe inspiring. Everyone involved in software development needs to adapt as they evolve and change the process of development.

