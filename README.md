# CEN4090L Capstone Project:

## Description:

This project is a **full-stack web application**. It uses some of the **latest technologies** in **web application development**, **cloud computing**, and **DevOps practices**. To see a list of all technologies used refer to the **technology section** of this ReadMe.

This **application** is a simple demonstration of an **e-commerce website** for a **pet boarding facility** where a user can create their own account, book reservations for their pets, avail of services such as pet **grooming, training, veterinary care**, and **adoption**.

It should be noted that this application simulates how a real **commercial web application** functions, it is simply used to **demonstrate** the **concept** of how a **full-stack application** works, and how the **different parts** of the **stack** work together to form a fully functional web application from the **front-end**, to the **back-end server**, and to the **data store**. It also shows how different technologies work together.

## II. Installation Guidelines:

There are two ways to **install** this **application**, the **first-being** the simplest one which is to install this application on your **localhost** machine, and ignore any instructions regarding the cloud. The **second** is to deploy this application to a **Cloud Service Provider** such as via `AWS`, `Azure`, or `Google Cloud`.

### 2.1. Frontend & Backend (Web Server):

To deploy to an AWS EC2 instance sign up for an AWS account, and navigate to EC2. Create and run an instance preferably the Amazon Linux AMI. Once that is running SSH into the instance and create a project folder, do a git clone to copy all the files or do it localy on your localhost machine.

One of the requirements of the application is being able to use Google's **Firebase** Authentication Service. Sign up for a Google Firebase account, and start by creating a project. Once the project setup is complete, build the authentication service. To use the service just import the SDK and authentication library in the `index.html` file, and copy-pasted the firebase configuration in each JavaScript file.

Follow the steps in this detailed process [Building the Backend](/Docs/References/Building_The_Backend.md) for more information.

* [Nginx Back-end Server Notes](/Docs/Backend/nginx_backend_server_notes.md)
* [pm2 Back-end Server Notes](/Docs/Backend/pm2_Backend_Server_Notes.md)

### 2.2. Mongo Database:

To build the mongo database first deploy a Linux EC2 instance in AWS. Once this is deployed follow the next steps to setup the **EC2 instance** & **MongoDB**.

* Install **Node.js** and **npm**, and verify that **npm** is installed
* Install **Docker engine** in EC2 instance
* Start the **Docker service** and **enable** it to start on boot
* **Create** a **mongo database** inside a **docker container** called `afcu-bank`
* Install **mongodb** should be `version 3.6.2` for this exercise to work

To get a more detailed list of steps with commands follow this detailed guide [Building the Database](/Docs/References/Building_The_Database.md). 