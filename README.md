# **Project documentation**

Our main idea of how ideas get to reality through the platform is that we put the whole thing into a process. The process is well defined and has all necessary steps to give the innovator the best support.
<br><br>

## **User roles in the system**

**Innovator:**<br>
Person who has an idea, but needs help to format it properly and figure out the details to make it a reality.

**Innovation support**<br>
Non-profit organisations whose main goal is to help new innovations become a reality, they have the knowledge how to format and present the idea, but do not have deeper expertise in the given field.

**Expert**<br>
People who are top specialists in their field and are willing to give their advice and suggestions to the innovator.

**Funding**<br>
These are different companies and investors who are looking to provide funding for new innovative ideas. They do not provide any support or consulting, they only review the documented report and decide whether it is worth their money or not.

**Manager**<br>
Person who wants to see the list of ongoing processes and add or remove expert/innovation support people's accounts when new people come and go. Additionally the manager collects the reporting data to take care of the payments.

---
<br>

## **Process**
As time is the most valuable asset, the goal of the process is to make every support person's work as effective as possible. For example, if the idea lands on some expert's table, they can quickly read and understand what state the idea is in and what they can help with.

This said, here is a brief description about specific steps in the process. Detailed model is included with images. 

[Process model image](./assets/process_img.png)

**Step 1 - submitting the idea**

After the innovator has created an account and logged in, they can see a list of submitted ideas (which is, of course, empty for new user) and can select to submit new idea. We have defined a well structured form to document the idea with certain required parameters. We call it the first (automatic) filter. The point of it is to give first feedback to the innovator. If they can not fill all the required fields, then probably they are not far enough with their idea and it would be waste of time for the supporting staff.

**Step 2 - review by the innovation support**

When the innovator has filled all the required fields, they can send it to the innovation support for review. The author can pick desired person from the list or let the system pick one who is available for the given category. The assigned reviewer then reviews the submitted form and can decide whether it has all necessary parts and is detailed enough to move forward. If the reviewer thinks it has some missing parts they can send it back to the author for improvements, otherwise they can accept it and make it possible to move forward to the expert review. The idea is that the innovator can not move forward before getting an accept from the innovation support. This said - they always have the option to change the reviewer or discard the whole idea.

**Step 3 - suggestions from the expert**

Once the author has received accept from the innovation support, they can decide to get another review from some innovation support person or move on to get help from some expert. They are free to choose the person from the list or they can just pick a field and the person is assigned to them by the system. Before initially sending the report to the expert, the author can write initial questions, if they have any. Also the expert can see the previous feedback given by the innovation support. Once again, the innovator can not move forward before the expert gives their approval, but they also have the option to change the expert or discard the whole idea, if needed.

**Step 4 - funding**

After receiving final accept from the expert, the author can again choose to get another review from some expert or send the idea to funding. At this point, the idea should be well thought-out and properly described. This means they now have good chances to receive funding from the investors. Now it's all down to investors and companies to look at the ideas submitted for funding and pick the ones they want to support.

<br>

The manager part is deliberately left out from this description, because it should not be part of the "Turning an idea into innovation" process. It is a separate side functionality to help Kesksintösäätiö manage their work and finances.

---
<br>

## **Technical implementation**

In this section we provide suggestions and thoughts about how we think the system should be implemented. The platform is a web based application that can be conveniently used from the browser on any device - desktop, tablet or smartphone.

**Frontend**

We provide a Figma (FIGMA LINK) prototype with the submission, so this should be the initial input for frontend development. The frontend should be implmented in one of the currently popular Javascript frameworks - React, Angular or Vue. These frameworks provide good performance on all devices and development functionalities for making intuitive and smooth design.

**Backend**

Backend (server) application is mainly needed for data storage and process management. It has several REST API endpoints for frontend to receive certain data. All endpoints are secured with JWT token authorization. This makes it easy to determine whether the user has access to the data requested. For logging in we would implement 2-factor authentication using Google Authenticator.

Our tech stack suggestion:
- Java 17
- Spring Boot
- Spring Security for securing API endpoints
- Liquibase for database structure management
- Camunda BPM for process management

We propose using Camunda BPM, because it is possible to integrate the same BPMN 2.0 process model linked to our submission to it. After integrating Camunda with the Spring Boot application, it provides a separate admin page, where for example Manager can see right on the model how many processes are ongoing and in which state they are in.

**Database**

Postgres relational database is perfectly suitable for this kind of application. With the wide range of functionalities and good performance, it provides everything we need.

**Version management**

For version management Git should be used. For storing the code there are two popular options - Gitlab or Github. Both of them provide CI/CD pipelines, container registry for storing images, merge requests, Kubernetes integration and so on.

---
<br>

## **Development plan**

For development, the Scrum methodology is proven to produce best results in large scale projects like this one. The main goal would be to prioritize the user stories and start to deliver little pieces of functionality right after some user story is completed. This way it is possible to already start gathering feedback from users and make improvements.