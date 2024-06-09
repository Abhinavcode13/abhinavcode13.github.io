---
layout: post
title:  "C4GT '24 with Mifos Initiative"
date:   2024-06-09 18:10:45
tags: c4gt
---



This post mostly discusses the Code for GovTech initiative, going over my process of applying for and developing my proposal for C4GT ‘24. It also talks about the program’s affiliate organization, which I selected to work with.

## Code 4 GovTech

**Code for GovTech (C4GT)** is an ecosystem initiative to build an open-source community of contributors, mentors, and organizations around Digital Public Goods (DPG), Digital Public Infrastructure (DPI), and Tech for Good products. These innovations are shaping the technological revolution globally to drive the mission of DPG/DPI in attaining the Sustainable Development Goals (SDGs).

C4GT conducts a Dedicated Mentoring Program (DMP) annually wherein select contributors (students or working professionals) work on open-source projects in the DPG/DPI/Tech for Good domain with 1:1 mentorship from domain experts. It is a 3-month long coding program offering a generous stipend to the contributor at the end of the program. The Dedicated Mentoring Program 2024 saw participation from 90+ organizations, listing 100+ problem statements spanning across 45+ different open-source products.

## My journey in Mifos Initiative

I first discovered the **Mifos Initiative** while applying for GSoC 2024. I found some interesting project ideas and created a proposal, getting feedback from the mentors. However, I wasn’t selected. When the organization joined the 2024 Code for GovTech program, I decided to apply again. This time, I was better prepared, having learned from my previous mistakes. Finally, I got selected for one of the projects in the Code for GovTech 2024 program.

The Mifos Initiative community is incredibly supportive. They maintain comprehensive documentation about the organization and its projects, conduct weekly squad calls, and utilize JIRA for effective issue tracking.

# About the project that I work on this summer

This summer, I’ll be working on **Project Mojafos Version 2** — a DaaS providing a deployable package of Mifos/Fineract, Mojaloop, and Payment Hub EE DaaS.

*Mifos & Fineract* integrated with *Mojaloop* via *Payment Hub EE* offers a complete open-source architecture for digital financial services. This setup allows for managing wallets and value stores in Mifos and Fineract, and initiating real-time payments through Mojaloop APIs with the Payment Hub EE orchestration engine. However, deploying these components, each with various microservices, libraries, and dependencies, is time-consuming and complex, posing a barrier for fintech's and financial institutions.

The **Mojafos project** aims to simplify this process by maintaining and enhancing a deployable package. In its second year, the focus will be on creating storyboards to help developers rapidly deploy the full environment. Various deployment options, such as infrastructure as code, Docker images, Helm charts, and Terraform scripts, will be provided to streamline cloud deployment and make the stack more accessible.

## Objectives of this project

1. Update Mojafos to deploy the latest version of Mojaloop.
2. Update Mojafos to deploy the latest version of Fineract.
3. Update Mojafos to deploy the latest version of Mifos X Web App.
4. Update Mojafos to deploy the latest version of Payment Hub EE.
5. Improve resource consumption of Mojafos Deployable Package.
6. With upgraded versions and improved consumption of resources, Mojafos should be closer to production-quality.

## How did I write the proposal

A template provided by **Code for GovTech** included sections for the title, summary, project details, and open-source contributions to Mifos. Additionally, there was a section for solving the GitHub Classroom assignment, which accounted for 25% of the selection weightage based on the DMP points earned. The remaining 75% of the weightage was based on how well the proposal was written and aligned with the project requirements.

### Sections in the proposal:

- **Title:** The title section typically includes the project name and a brief, descriptive overview of the project’s main objective.
- **Project details:** Explains what the project is about, how it will be done, when it will be completed, what will be achieved, and what is needed to make it happen.
- **Implementation details:** Describe how something will be done or executed, providing specific steps or methods in simple terms.
- **Timeline:** Lays out when each part of the project will happen, from start to finish.
- **Previous experience/open-source projects:** Refers to any involvement or contributions made to freely accessible software initiatives.

[Link to my C4GT proposal](https://docs.google.com/document/d/1lOLnKjNyyxnanvGzgBx4b4Z2uaXLzrk0oFnW1neMVwY/edit)

The project is mentored by **Elijah Okello**. I am really excited to work on this project.

To everyone who was chosen for **Code for GovTech 2024**, best wishes. This blog should help you understand more about C4GT and open source.
