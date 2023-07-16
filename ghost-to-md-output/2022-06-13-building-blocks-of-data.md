---
title: "xUnfolded #1: The Building Blocks Of Data"
slug: building-blocks-of-data
date_published: 2022-06-13T05:13:57.000Z
date_updated: 2022-06-13T05:13:57.000Z
tags: Newsletter, Blog
---

Good morning,

This is the first newsletter of***xUnfolded*** (short for *Experiments Unfolded*). I'll be researching and experimenting with tech and this newsletter will be the central source I share the results to. If you find yourself enjoying what you read, share for others to be a part of it :)

---

Richard Feynman was a scientist involved with the Manhattan Project. 40 years after the atomic bomb was launched in Japan, he gave a talk in Tokyo about "[Computing Machines In The Future](http://cse.unl.edu/~seth/434/Web%20Links%20and%20Docs/Feynman-future%20computing%20machines.pdf) (1985)." In his lecture, he mentions a great deal of work to develop smarter machines that have better relationships with humans. Where computers with inputs and outputs can be made with less effort than the complexity required back then. 
![](__GHOST_URL__/content/images/2022/06/image-1.png)
One core topic he speaks about is Parallel Computing, where large amounts of data can be split and processed by computers connected by specific design patterns. Each machine working independently to solve separate parts of the problem and transfer information as needed. The architectural discussion was meant to fix efficiency problems that come with processing memory in one central computing model. 

It's been four decades since the invention of the microprocessor and two decades into the rise of cloud computing. Feynman's principles in his lecture have held to be true. 

While the topic of Parallel Computing screams blockchains, this newsletter will explain the fundamentals of how data works with today's cloud computing (*parallel* to Feynman's idea. Ha ha get it?). 

This is my high-level summary to refine what I know on data architecture in traditional computing. I'll be using this to build upon my research with blockchains. It's also an excuse to study for my Microsoft Azure [certification](https://docs.microsoft.com/en-us/learn/certifications/exams/dp-900). 

## What Cloud?

Let's define "the cloud" for those of us who are like Sylvester Stallone:

Cloud computing is renting hardware services like servers, storage, databases, networks, and software over the internet. Most internet platforms host their applications on cloud architecture. This saves the trouble of buying and maintaining the computing machines necessary to run their online service. Most importantly, it allows for the computing efficiency that Feynman mentions in his lecture.

## Hacking The Database

You can classify data as structured, semi-structured, or unstructured. Most computing today involves taking data from external sources, structuring it, and moving it internally for analytical use. The typical process is to extract raw data, load it into a database to structure it logically, and transform it into useful information. As Feynman mentions, software is responsible to handle such transfers. There's a lot more complexity involved in the backend.

The most common way of storing data is in table form like excel:
![](__GHOST_URL__/content/images/2022/06/image.png)
Relational data like this is structured in columns and rows. Each table has attributes such as the order number, ID, emails, and name. Tables are meant to separate types of data. Every table must have a unique key that can be used to map between them. This creates a logical sequence of data based on how entities relate to each other. When people in movies "hack the database," they basically have access to the keys that map to the information stored in the machines. 

Of course, storing large chunks of information inside a computer isn't that useful for humans. Structuring the data into logical tables has been most efficient method for people and computers. This doesn't mean unstructured/semi-structured data is useless. They help separate signal from noise through a standard of computing languages.

## Data Definition Language

Universality is the quality of being appropriate for all situations. Feynman critiques the standardization of programming by saying there should just be one type of language for computing. 

While a physicist like Feynman would appreciate single universality between programming languages, this wouldn't work today. However, there are standards for how to define data, despite the many computing languages available. Data Definition Language (DDL) creates a standard for the commands used to create, modify, and remove database objects.

For example, the most dominant programming language for browsers today is JavaScript. A native way to transfer and handle data between clients and servers can be done through JavaScript Object Notation (JSON) or Extensible Markup Language (XML). These are simple open text formats to represent the unstructured data that moves between computing machines.

While Feynman may have wanted a universal computing language, cloud computing today has standards that mimic his predictions. It does this by sending and retrieving data between computers through defined languages like JSON and XML to be processed through different programming languages such as SQL, JavaScript, and C#.

## Parallel Computing

Feynman mentions computing designs that work towards a common process, but independently solving problems by separating its computation. Computing today manages to achieve this despite its central architecture. It does this through the interplay between separate cloud services available on a given platform. 

Data should be looked as a symphony. You have the conductor at the front directing the orchestra. Multiple instruments play different sounds to create music. 

There are computing models that act as the conductor by bringing data from external sources, transforming the structure, and storing it as information. The cloud definitions in place transfer data between computing machines. This is known as data pipelines. They logically group data activities through a series of sequential or parallel computing tasks. 

Again, this is all a high level overview of how data is processed in traditional computing models. There is much much more to it, but it was fun seeing the relevance of Feynman's explanations of [computing in the future](http://cse.unl.edu/~seth/434/Web%20Links%20and%20Docs/Feynman-future%20computing%20machines.pdf). Especially after seeing how true some of his predictions turned out.

I plan to experiment with decentralized data structures to give a similar explanation on blockchains in the future. We'll see how that goes. 

Till then, more xUnfolded newsletters to come,

-rushil :)

## SHARE SHARE SHARE

### Spread this email to your dog, cat, aunt, or uncle so they can get smarter.
[COPY AND SEND LINK TO ANYONE SMART ENOUGH TO READ xUNFOLDED](__GHOST_URL__/#/portal/signup/free)

If you were sent this email by your owner, niece or nephew:
