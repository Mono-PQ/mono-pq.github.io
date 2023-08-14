---
layout: post
title: Identifying data anomalies
date: 2023-03-17 17:00:00
description: Illustrates how it is possible to identify data anomalies via data analysis
tags: datascience
categories: datascience
giscus_comments: true
related_posts: false
---

One of my very first tasks as a data analyst was to familiarise myself with the data which the business is concerned about and try to observe if there is any data anomalies associated with them. This couldn't be done without understanding the business processes and operations that the data is representing. 

At first, it seems as though it's an impossible task given the open nature of the problem. There was little to no guidance where to start. Given that the entire project team is newly hired, each of us has our struggles. No matter who you tried to ask, you realise that they know as little as you do. 

So how should I complete this task? 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_work_1_1.jpg" title="data analytics" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_work_1_2.jpg" title="website" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_work_1_3.jpg" title="feedback" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image credits: <a href="https://www.freepik.com">Freepik</a> and <a href="https://pixabay.com/">Pixabay </a>
</div>

The most obvious one is to find out how to obtain access to the data which the business users depend on. Some questions that you could ask include: 

1. What type of data does the business generate and where is the data stored? 
2. Is there any data warehouse available where access could be granted for analysis purposes?
3. What are business operations and processes and whether there is any documentation for reference?
4. Is there any upstream or downstream dependencies of the data? If so, is the data lineage diagram available?

Of course, the questions above are non-exhaustive. The questions to ask highly depend on the business problem and the industry that you're in. 

Once you have gotten access to the data, you can give it your best attempt to extract the data from the files,systems or databases for your analysis. Depending on the organisation's tech stack and setup, you might need to scramble and speak to multiple individuals before getting the right credentials and configurations to establish a connection for data extraction. In the midst of all the emails and messages, you could realise that the data can only be extracted via a VPN or secured connection to prevent any unauthorised disclosure of the organisation's proprietary information. Perhaps, you could only work on the dataset within a sandbox with limited tools available for your analysis. Depending on your past experience and exposure, you might not have used these tools before. Before you know it, you probably need to learn on the fly while getting the analysis done within the stipulated timeframe.

So, now you should have access to extract the data. But should you dive right into it? I have tried doing so. Only to find out that the size of the data that I am dealing with is massive. Millions of records with over hundreds of columns. Where and how should I start? 

Start with understanding the business meaning that the data represents and get hold of the metadata, if available. This would help you get a sense of what type of data you are dealing with and what are some of the underlying assumptions that you need to be aware of while working on the analysis. For instance, *start_time* can have multiple meanings in different contexts. Hence, it's always useful to clarify any doubts or uncertainties with the business owners or relevant stakeholders so that you have a concrete idea of what the data represents. This also prevents unwarranted mistakes during the analysis. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_work_1_4.jpg" title="forest" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image credits: <a href="https://pixabay.com/">Pixabay</a>
</div>

When dealing with a massive dataset, it is important to ask targeted questions relating to the business problem that we are trying to solve. For example, instead of looking through the entire data, we could explore a subset of the data that the business has concerns about in the recent quarter. This helps us to finalise our analysis and findings in a shorter time period allowing the business owners to take timely action(s) to address their concerns. With targeted scope, it's also easier to spot any anomalies that might be of interest to the business. 

It could be a daunting task for a data analyst (who is just starting out) to have a substantial understanding of the business domain and ability to familiarise and pick up proprietary tools used for analysis at the organisation before the actual work starts. That's why we hear about people working as data analyst, data scientist, software engineers and other similar technical roles suffer from imposter syndrome. There is just so much to learn, so much we assume we need to know, and so much we just don't know. 

Looking on the bright side, a challenge can always be overcome by proactively searching and reading through relevant documentation, talking to the right person and keeping your ears and mind open. It's also only when we're challenged that we learn the most.
