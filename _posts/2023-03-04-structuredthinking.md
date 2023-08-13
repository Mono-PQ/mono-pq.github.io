---
layout: post
title: Structured thinking for the role of data analyst
date: 2023-03-04 17:00:00
description: Ability to think through problem, break them down and figure out a way to find out more and understand them using data. 
tags: structured-thinking 
categories: soft-skills
giscus_comments: true
related_posts: false
---

Structured thinking is one of the basic skills that data analyst needs to be equipped with. It helps you recognise the problem or situation, organise information, identify gaps and opportunities, and brainstorm potential options available. 

In an ideal world, perfect information and data could be available for each problem or task assigned. However, in practice, that wouldn't be the case. For instance, you might be assigned a task with limited information such as **"provide me with the accuracy of email alert received by users from the control tower by tomorrow".** Some might dive straight into the problem with an inherent assumptions of the type of email alert, period which the email alert was sent, and the control tower that is involved. Yet, all of these were not clearly specified in the instruction. If any of the assumptions are wrong, time and effort will be wasted on rework. 

In such situration, structured thinking can help you clarify the scope of work before starting on the task. It also helps align the expectations with your manager or stakeholder(s) who assigned the task to you. 

### 1. Clarify the context based on the limited information available 
Context is important especially when you are working with data. It's easy to go down a rabbit hole with endless possibilities and options based on the data. Hence, without understanding the context, you'll often find it difficult to provide a reasonable recommendation to the stakeholders. 

In the above example, the context that needs to be clarify is as follows: 
* What's the underlying reason behind the analysis? Have our stakeholders flagged out problems relating to the alert accruacy of the control tower? 
* If there is more than one control tower, which control tower should we focus on? 
* Which email alert should we focus on? 
* How is the email alert triggered? What's the underlying logic for the trigger?
* Which period should we look back at (e.g., past week, past month, past 3 month, past year)?
* If you are dealing with multiple regions/countries, is there a specific region/country to focus on? 
* In terms of alert accuracy, are we looking at whether the alert is valid based on the logic and data or are we looking at whether the potential missing alert that wasn't flagged when the data reflects an incident/risk or something else? 
* Is the request urgent? Is deadline negotiable? (This is especially important if you are already preoccupied with other tasks.)
* Is there any specified format of sharing the findings with the stakeholders?

By asking some of these questions, you'll be able to understand the context of the task, find out the relevant stakeholders who are involved and interested in your findings, and  clarify the scope of the task. These information can help you better manage the expectations of your manager and the stakeholders and estimate the amount of work required for this task.  

Now that you have a better understanding of the problem and context, you'll need to figure out what are the data and tools you require for your analysis, and whether you have access to these data and tools. 

### 2. Availability of information, data and tools 
It is not rare for you not to have access to the information, data tools required for the task. Furthermore, you might not even receive them at the point when the task was assigned to you. In this case, you'll need to list of the data and platforms you require for the analysis and work with the administrator to obtain access to them. First information required is definitely the email alerts sent via the control tower during the stipulated period. If data is appended in the email alert, you might also require the attachment(s) as well. Depending on how long you've been with the team and organisation, you may or may not know who to reach out to. Hence, there is a need to clarify with your manager or senior(s) who have previous experience working on similar analysis. 

You would also need access to the data sources of the control tower in question. This is so that you can extract, transform and analyse the underlying data in order to assess the accuracy of the alerts. If you don't already have access, then you might need to find a channel that could grant access to the data sources, or help in extracting the relevant data points for your analysis. 

Depending on the size of the data, you may want to choose an appropriate platform for data cleaning and analysis. In most established organisation, this might also require approval to run analysis and allocation of compute resources. 

### 3. Analysis
Finally, you've reached the part on analysis - the bread and butter of a data analyst role. However, you find yourself questioning what each of the attribute in the data really mean. This is especially true when you are working in an unfamiliar domain area. Perhaps, it good to ask whether there is a channel where you can find relevant metadata information? 

In the event if data points don't tally, what are some of the possible reasons? Is there additional filter or exceptions that should be considered? Further clarification with the stakeholders might be required to deep dive into the initial design and objective of the alerts, and clarify if there is any subsequent change to the logic of triggering the alert. Sometimes there are just too much unknown and uncertainty for you to come to a conclusion with the available data. There could be blind spots that you are just not aware of. However, close communications and collaboration with the stakeholders would ensure that most of the uncertainties are clarified and addressed during the analysis phase. 

If the data couldn't tell a conclusive story, you may want to highlight that the current data is insufficient to provide conclusive evidence for the problem and suggest ways or additional data points that could be collected for the analysis to proceed further. 

### Summary
Each task and problem is unique in nature. The steps to take may differ from problem to problem. However, one can certainly build up experience in structured thinking over time and start asking the right questions after thinking through the problem. This would save so much time and effort that could be a result of misaligned expectations and insufficient communications and collaboration with the relevant parties.
