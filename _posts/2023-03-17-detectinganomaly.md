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

At first, it seems as though it's an impossible task given the open nature of the problem. There was little to no guidance where to start. Given that the entire project is newly hired, each of us has our struggles. No matter who you tried to ask, you realise that they know as little as you do. 

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
3. What are business operations and processes and whether there is any documentations for reading and reference?
4. Is there any upstream or downstream dependencies of the data? If so, how the process flow looks like?

Of course, the questions above are non-exhaustive as it is highly dependent on your industry and area of work. However, it is a good starting point. 

Once you have gotten access to the data, you can give it your best attempt to extract the data from the systems or databases for your analysis. However, that is not an easy task by itself. Depending on your organisation setup, you might need to find out the data connection configuration to establish the connection for data extraction or find out the production url of the application where you could access the data. For certain industries, you might only be able to extract the data via a VPN or secured connection to prevent any unauthorised disclosure of the organisation's proprietary information.

So, now you should have access to extract the data. But should you dive right into it? I have tried doing so. Only to find out that the size of the data that I am dealing with is massive. Millions of records with over hundreds of columns. Where and how should I start? 

Start with understanding the business operations that the data represents and get hold of the metadata (which is data that describes data). This would help you get a sense of what type of data you are dealing with and what are some of the underlying assumptions that you need to be aware of (especially when working on the analysis). For instance, *start_time* can have multiple meaning in different contexts. In the context of a time-series, *start_time* might represent the start of the window. In the context of a calls dataset, it might represent the start of a call. With an understanding of the business and help of metadata, you get a better idea of what is the data you are dealing with. And this will help you to push your exploration deeper. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_work_1_4.jpg" title="forest" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image credits: <a href="https://pixabay.com/">Pixabay</a>
</div>

Now, there is finally some light sipping through at the end of the dark tunnel. We can dive deeper into a subset of the large dataset to answer some fundamental questions relating to the business. When dealing with a massive dataset, it is important to ask targeted and focused questions relating to the business problems that we might want to solve. For example, instead of looking through the entire data, we just want to know how the business has been doing in the recent quarter (i.e., 3 months). By asking targeted and focused question, it helps us to increase the speed and effectiveness of the data extraction and analysis process. With targeted scope, it's also easier to spot any anomalies that might be of interest to the business users. For instance, when querying the data for the latest query, you might find that the data is missing for the last month which might be an anomaly or a sudden dip in the revnenue which was not expected given your domain knowledge. That'd be a starting point to dive deeper using data or effective collaboration with the relevant stakeholders to find out the root cause. 

Yet, it's ironic that understanding the business and have the awareness of potential anomaly (i.e., able to identify them from the data) have to come before even starting the actual work. This might be challenging especially when you are new to an industry without much domain knwoledge in the area of business that you are dealing with. However, challenge can always be overcome by proactively searching and reading through relevant documentation, talking to the right people about their business processes and keeping your ears and mind open during meetings with the keystakeholders. Information comes from anywhere. The more you expose yourself to different channels and platforms, the more you'll learn.
