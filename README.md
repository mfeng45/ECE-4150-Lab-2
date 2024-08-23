# Serverless Photo Gallery Application - Lab 2

This repository contains the code and instructions to create a serverless Photo Gallery application using AWS Lambda, API Gateway, S3, DynamoDB, and Cognito. In this lab, we will expand the application to include albums and photos, using a NoSQL variation to store photos. The application is implemented in Python using the Flask web framework and will be deployed on an Amazon EC2 instance.

## Overview

The application utilizes the following AWS services:

- **EC2**: To host the web application and resources.
- **S3**: For storing photos.
- **API Gateway**: To expose endpoints for backend services.
- **Lambda**: To handle backend business logic.
- **DynamoDB**: For storing records of photos.
- **IAM**: For managing permissions and roles.

## Setup Instructions

Follow the steps below to set up the Photo Gallery application in your AWS account.

### 1. Create EC2 Instance

- Launch an EC2 instance to host the static website and resources.

### 2. Create Security Group

- Set up a Security Group to allow access to your EC2 instance from specific locations.

### 3. Create DynamoDB Table

- Create a DynamoDB table to store metadata and records of photos.

### 4. Create S3 Bucket

- Create an S3 bucket to store photos uploaded by users.

### 5. Create IAM User

- Create an IAM user with the necessary permissions to access the S3 buckets, DynamoDB table, and other AWS resources.

### 6. Update `env.py` Script

- Update the `env.py` script with your configurations and transfer the entire codebase to the EC2 instance.

### 7. Transfer Files to EC2 Instance

- Use a tool like FileZilla to transfer files from your local machine to the EC2 instance.

### 8. Install Necessary Libraries

- Install the required libraries inside the EC2 instance to run the application.

## Photo Gallery using NoSQL

The following exercises will help you implement user management, authentication, and other CRUD operations to support the Photo Gallery.

### Exercise 1: User Management and Authentication

1. **Design and Implement User Management and Authentication:**
   - Allow users to create an account (sign up) and sign in (log in) through the website.
   - Store user information in a new table called `PhotoGalleryUser`.

   **Requirements:**
   - Use password hashing when signing up (see Appendix C).
   - The `userID` should be a universally unique identifier (UUID).
   - Both `userID` and email must be unique. A user cannot sign up multiple times with the same email.
   - To log in, the user should use their email and password.

2. **Email Confirmation:**
   - Send an email with a confirmation token (including the `userID`) to validate new accounts. 
   - The token should last for 10 minutes. If the user does not click the link within that time, the token becomes invalid.
   - The resource should redirect the user to the login page upon confirmation.
   - The user cannot use the website until they are verified.

3. **Session Management:**
   - When a user logs in, store a session token in their browser.
   - The token should be used to validate user navigation on the website.
   - The token should expire after 5 minutes, redirecting the user to the login page upon expiration.

### Exercise 2: Cancel User Account

1. **Account Cancellation:**
   - Implement a method to allow users to cancel their account.
   - Remove all albums created by the user upon account cancellation.

   **Requirements:**
   - Attach an attribute to each album identifying its creator.

### Exercise 3: Delete Photo

- Implement a method to delete a photo from the Photo Gallery.

### Exercise 4: Delete Album

- Implement a method to delete an entire album from the Photo Gallery, including all photos inside the album.

### Exercise 5: Update Photo Information

- Implement a method to update the title, description, and tags of a photo.
- Ensure the `updatedAt` attribute is updated whenever a photo is modified.

## License

This project belongs to Georgia Institute of Technology 

## Video Demonstration of the Final Product 
Youtube Link: https://youtu.be/iqKdcEg3gNE
