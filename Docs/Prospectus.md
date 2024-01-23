# Project Prospectus:

### Team Name: DevGru

### Team Members:
* Paul Estipona ([pve19@fsu.edu](mailto:pve19@fsu.edu))
* Kathryn Carey ([kmc19k@fsu.edu](mailto:kmc19k@fsu.edu))
* Jarrod Daniels ([jkd21c@fsu.edu](mailto:jkd21c@fsu.edu))
* Adam Brown ([ab13ac@fsu.edu](mailto:ab13ac@fsu.edu))
* Serena Seegert ([sds21l@fsu.edu](mailto:ab13ac@fsu.edu))

## Problem Statement:

The need for a pet boarding facility has been increasing over the past years. Pet owners have been looking for ways to provide boarding for their pets when they are away from home and can’t bring their pets with them. Currently a handful of pet boarding facilities don’t have an existing web page to make reservations and a way for customers to inquire information about their services online. Most of the time, reservations are made over the phone or by personally going to the location.

## Project Overview:

Due to the need for an **e-commerce website** for a **pet boarding facility**, our team (DevGru) proposes to build a **full-stack web application** that allows customers to book reservations for a pet boarding facility, as well as a couple of services such as pet *grooming, training, veterinary care, and adoption*.

The **web application** will consist of **multiple web pages** where the **main page** showcases the brand (logo), a short description of the pet boarding facility, essential information such as hours of operation, FAQ and a contacts section. There will also be a **Navbar** at the top of the main page that contains **menu items** for the different services offered, as well as a section to sign-in or create a user account.

When the user selects any of the menu items from the Navbar in the main page, the user will be routed to another page that will be specific to the type of service the user selected. There will be a separate page for each of the services such as pet grooming, training, veterinary care, and adoption. Each page will also have a Navbar that allows the user to go back to the main menu or logout from their session.
To confirm a reservation the user will have a shopping cart that will be tracked where the user can add the types of services they would like to purchase and a payment will be required to confirm the booking.

## Goals:

1.	Develop the **front-end web user interface (UI)** using a styling framework called [Bootstrap](https://getbootstrap.com/).
2.	Develop the **client-side logic** using [React](https://react.dev/learn) to provide functionality for the web components.
3.	Develop the **back-end logic** using [Java](https://dev.java/) and set up [Spring Boot](https://spring.io/projects/spring-boot/) to manage the RESTful API endpoints.
4.	Develop the **database** using [MongoDB](https://www.mongodb.com/developer/).
5.	Perform **end-to-end testing** locally using [Postman](https://www.postman.com/product/what-is-postman/) to make sure data is flowing from the front-end to the back end and to confirm the API endpoints are working.
6.	Setup [Google Firebase](https://firebase.google.com/docs) for **user authentication** and [Stripe](https://stripe.com/docs) to simulate **online payments**.
7.	Repeat **end-to-end testing** to make sure the application works seamlessly with *user authentication* and *online payments*.
8.	**Register a domain** for the web application via [AWS Route 53](https://aws.amazon.com/route53/).
9.	**Build** the **remote environment** in the cloud that will host the **web application** by creating [EC2 instances](https://aws.amazon.com/pm/ec2/?gclid=Cj0KCQiAwbitBhDIARIsABfFYIJDboNwzLsDmtl9BaOQ2Z50RNKO86j_2_rKcDpO-daarpRKDUu4-1YaAnTAEALw_wcB&trk=9cd376cd-1c18-46f2-9f75-0e1cdbca94c5&sc_channel=ps&ef_id=Cj0KCQiAwbitBhDIARIsABfFYIJDboNwzLsDmtl9BaOQ2Z50RNKO86j_2_rKcDpO-daarpRKDUu4-1YaAnTAEALw_wcB:G:s&s_kwcid=AL!4422!3!651751059324!p!!g!!amazon%20web%20services%20ec2!19852662176!145019190137) in AWS, and installing the **required services** needed for the application to run.
10.	**Deploy the application** to the **cloud** in the remote environment.
11.	Perform **functional testing** to make sure the application works as intended.

## Stretch Goals:

1.	Setup **CI/CD pipelines** using [GitHub Actions](https://github.blog/2022-02-02-build-ci-cd-pipeline-github-actions-four-steps/) to perform **automated testing** when updates are made to the web application.

## Specifications:

The **front-end** will be developed using [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) and a styling framework called [bootstrap](https://getbootstrap.com/) which uses html & CSS. For the client-side logic our team will be using a front-end framework called [React](https://react.dev/learn) to handle user interactions, and dynamic updating of the DOM (Document Object Model).

The **back-end** will be developed using [Java](https://dev.java/), and to handle the server-side logic which we will be using a back-end framework called [Spring Boot](https://spring.io/projects/spring-boot/). This will expose RESTful API endpoints in the server-side that our React front-end components can call to perform HTTP requests. Spring Boot will also be used to perform CRUD (Create, Read, Update, Delete) operations to the database server.

For the **datastore** we will be using [MongoDB](https://www.mongodb.com/developer/) a NoSQL database that uses JSON to store data in a document-oriented structure. Our team will also be using [Google Firebase](https://firebase.google.com/docs) to handle user authentication to provide security for the web application. Since this would be a fully functional web application, we will be using [Stripe](https://stripe.com/docs) to process and simulate payments from customers.

For **testing** the API endpoints we will be using a tool called [Postman](https://www.postman.com/product/what-is-postman/) to perform HTTP requests to the API endpoints and verify the information that is being returned.

Finally, we will be **deploying** our full-stack web application to the Cloud on an AWS [EC2 Instance](https://aws.amazon.com/pm/ec2/?gclid=Cj0KCQiAwbitBhDIARIsABfFYIJDboNwzLsDmtl9BaOQ2Z50RNKO86j_2_rKcDpO-daarpRKDUu4-1YaAnTAEALw_wcB&trk=9cd376cd-1c18-46f2-9f75-0e1cdbca94c5&sc_channel=ps&ef_id=Cj0KCQiAwbitBhDIARIsABfFYIJDboNwzLsDmtl9BaOQ2Z50RNKO86j_2_rKcDpO-daarpRKDUu4-1YaAnTAEALw_wcB:G:s&s_kwcid=AL!4422!3!651751059324!p!!g!!amazon%20web%20services%20ec2!19852662176!145019190137). Our team will register a fully functional domain via AWS’s DNS service called [Route 53](https://aws.amazon.com/route53/). We will be using reverse proxy handled by [NGINX](https://www.nginx.com/resources/glossary/nginx/) to handle incoming user requests. We will be employing DevOps practices such as Continuous Integration (CI) and Continuous Deployment (CD) in a CI/CD Pipeline using [GitHub Actions](https://github.blog/2022-02-02-build-ci-cd-pipeline-github-actions-four-steps/).
