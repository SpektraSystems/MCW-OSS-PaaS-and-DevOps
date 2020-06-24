
# OSS PaaS and DevOps hands-on lab step-by-step

## Abstract and learning objectives

In this hands-on lab, you implement a solution for integrating and deploying complex open-source software (OSS) workloads into Azure PaaS. You migrate an existing MERN (MongoDB, Express.js, React.js, Node.js) stack application from a hosted environment into Azure Web App for Containers, migrate a MongoDB instance into Cosmos DB, enhance application functionality using serverless technologies, and fully embrace modern DevOps tools.

At the end of this hands-on lab, you will be better able to migrate and deploy OSS applications into Azure PaaS using modern DevOps methodologies and Docker containers.

## Overview

Best For You Organics Company is one of the leading online health food suppliers in North America, serving customers in Canada, Mexico, and the United States. They launched their highly-successful e-commerce website, which sells subscriptions to their meal service, in 2016, and have been steadily increasing their subscriber-base since. Their service targets working professionals looking for convenient, reliable access to healthy meal choices, and pre-packaged recipes without having to spend too much time preparing the meals.

Their CIO is a big proponent of open-source software, and the development of their web application was done using the MERN stack (MongoDB, Express.js, React.JS, Node.js). They host their code in a private GitHub repository. They currently have a continuous integration workflow, triggered by each code check-in/commit in GitHub, using Jenkins.

As their service has grown, they have found that the management of VM and server infrastructure is a real challenge. They want to learn more about how Platform as a Service (PaaS) solutions for OSS applications on Azure might be able to help. Their goal is to focus their expenditures and efforts on their core business, rather than infrastructure. The development team at Best For You Organics has indicated they have some experience with Docker. They are interested in what options might be available for using containers to deploy their application into a cloud environment. They are also interested in learning more about identity management.

The development team has also expressed that they would like to continue using GitHub as their code repository but is interested in improving upon their DevOps pipeline. They currently use Jenkins for their builds and are interested in any tools available in a cloud offering that could help with release management, or other aspects of a fully-integrated, modern DevOps pipeline. Ultimately, their goal is to automate and simplify deployments through CI/CD capabilities and deliver updates faster and more reliably.

## Solution architecture

Below is a diagram of the solution architecture you will build in this lab. Please study this carefully, so you understand the whole of the solution as you are working on the various components.

![This diagram consists of icons that are connected by arrows. On the left, the Developer icon (VS Code) points linearly to the GitHub Repo and Jenkins icons. The previous two icons are enclosed in a box labeled CI/CD Pipeline. Jenkins points to Web App for Containers on the right. Various arrows point from Web App for Container to: Azure Container Registry (a double-sided arrow); Logic Apps (a linear arrow that also points from Logic Apps to Customers); Customers (a linear arrow); and Azure Cosmos DB (a double-sided arrow that also points from Azure Cosmos DB to Azure Functions with another double-sided arrow).](media/solution-architecture-diagram.png "Solution architecture diagram")

The solution begins with developers using Visual Studio Code (VS Code) as their code editor. In VS Code, they can leverage rich integrations with GitHub, Docker, and Azure. From a high level, developers will package the entire OSS application inside a custom Docker container using the Docker extension in VS Code. The image will be pushed to an Azure Container Registry as part of a continuous integration/continuous delivery (CI/CD) pipeline using GitHub and Jenkins. This Docker image will then be deployed to a Web App for Containers instance, as part of their continuous delivery process using The Azure App Service Jenkins plugin.

The MongoDB database will be imported into Azure Cosmos DB, using mongoimport.exe, and access the database from the application will continue to use the MongoDB APIs. The database connection string in the application will be updated to point to the new Cosmos DB.

A serverless architecture will be applied to order processing and customer notifications. Azure Functions will be used to automate the processing of orders. Logic Apps will be applied to send SMS notifications via a Twilio connector to customers informing them that their order has been processed and shipped.

In this hands-on lab, you will assist them with completing the OSS application and database migrations into Azure. You will implement a containerized solution. For this, you will create a custom Docker image and push it to an Azure Container Registry. You will then configure a CI/CD pipeline to deploy the application to a Web App for Containers instance. You will also help them implement functionality enhancements using serverless architecture services in Azure.

## Requirements

1. Microsoft Azure subscription must be pay-as-you-go or MSDN
    - Trial subscriptions will *not* work.
2. Linux virtual machine configured with:
    - Visual Studio Code
    - Azure CLI
    - Docker
    - Node.js and npm
    - MongoDB Community Edition

## **Azure subscription and OSS-PaaS-and-DevOps environment** ##
Once the environment is provisioned, a virtual machine and labguide will get loaded in your browser. For getting the lab environment details you can select Lab Environment tab. Additionally, The credentials will also be emailed to the email address entered at registration.
(media/)
