---
layout: post
title:  "Puppet Code Quality Survey: Results"
date:   2016-01-28 09:57:21
categories: puppet
---

The subject of my master's thesis is code quality in puppet. As a part of our investigation of puppet code quality, we decided to hold a survey under the puppet programming community to ask them about their opinion on code quality. I promised everyone who answered this survey that I would publish the results, which I am doing by means of this post.

For this survey, I approached around 250 recently active puppet programmers on GitHub. The survey lasted from 14 to 24 december. I got 40 responses.
In the processing of the answers, I added two complete answers from an earlier pilot. This puts the amount of analyzed responses at 42. The survey consisted of a question to indicate the experience of the programmer, and was followed by 5 open questions. I processed the answers by identifying the keywords they mentioned and the concepts they referred to and categorizing the answers accordingly.

![this space for rent](/assets/q2.png)

Looking at the top 5, code quality in puppet is not very different from normal programming languages. Testing, documentation, code style and linting are common to other languages as well. More interesting is the program structure - examples here are proper usage of the Package, Config, Service design pattern, and making use of params.pp. The exec resource is also frequently mentioned, and specific to puppet. Other interesting aspects are whether the program is cross-platform, data is separated from code, and what is done with resources - which kinds are used and what their relations are.

![this space for rent](/assets/q3.png)

The leading bad practice here is the improper usage of exec. Some other puppet-specific bad practices are having a lacking program structure (no PCS / params.pp for instance), hardcoded variables, having too many dependencies (or too little), non-idempotence and having too many or too few parameters. Also failing to use hiera when this is needed is considered a bad practice.

![this space for rent](/assets/q4.png)

The answers to this question are not specifically related to puppet code quality. The most mentioned metric here is activity. After this comes documentation, popularity and the author. The documentation here differs from Q2 - specific examples of documentation mentioned here are parameter documentation, and whether the documentation mentions use cases.

![this space for rent](/assets/q5.png)

An explanation of the above chart: Hiera: xyz means that xyz goes into hiera. Puppet: abc means that abc goes into puppet.

A lot of slightly different answers were given to this question. The gist of it is this: In hiera goes varying data: things that are site-specific, node-specific, company-specific, non-generic, but also data that changes a lot. Secrets (such as passwords, ssh, &c.) go into hiera as well. To finish this list I would add data that overwrites parameters. What do users put into puppet code? Distro-specific information, static data, global variables and parameter defaults. 

Respondent #11 summarizes the above quite well: "A class should usually "just work" when using something like "include <classname>". Data necessary to make it work should be included as defaults, data that is adjusting for non-generic use case should be in Hiera."

What is interesting in this question is that there are a lot of very different ways of deciding what to put into hiera, and a lot of respondents have reported their way of deciding, which sometimes can be quite unique. The differences in answering this question most likely indicate a lack of consensus among respondents about what data to put into hiera.

![this space for rent](/assets/q6.png)

Answers to this question were quite unique and hard to analyze/group, but we managed to figure it out. Where needed I will explain the categories. Most reported problems are related to puppet design. The problems in this category are related to the way that puppet is designed. Examples are snowflake servers, the limitations on a single node, and nondeterminism. After that comes third party modules: "We don't have many problems. The biggest problem we've run into is relying on a third-party module from puppet forge or puppet-labs.    We've eventually had to either:  - make forks of some modules to include some of the features we need (or fix a bug)  - switch to another module". The poor quality of third-party modules was also mentioned. Testing was also mentioned quite often, especially writing good tests. The puppet documentation was mentioned - especially for the types and providers API. We assigned all answers that wanted a feature added to puppet that was not there to Missing Functionality. The quality of the error messages (both puppet & ruby based errors) was mentioned. I'd like to conclude with the lack of best practices. One respondent mentioned a lack of best practices for the toolset, another mentioned a lack of a best practice for module organisation. I guess what most people have is a /modules folder, but if that is filled with over 200 modules, that can get quite full and hard to navigate.

I'd like to thank everyone who filled in my survey, you've been a big help with my research.

This is an initial version of the results, a more detailed version will be published in my master's thesis. If you have any questions or comments, feel free to leave a comment below.

If you read up to here, you must be interested in my research topic of Puppet code quality. If you are a Puppet developer, you might be able to help me in the next step in my research, where I will build a quality evaluation model and validate it with experts and case studies. Contact me if you can help me out!

{% if post.comments %} hoi {% endif %}
