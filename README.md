 # Setting Up Jenkins for CI/CD with GitHub and Git Flow

## Introduction

This document provides a comprehensive guide on setting up Jenkins for continuous integration (CI) with a GitHub repository using the Git Flow branching model. It includes step-by-step instructions for configuring Jenkins, installing necessary plugins, and creating a Jenkinsfile to automate the build process.

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Prerequisites](#2-prerequisites)
3. [Configuration Steps](#3-configuration-steps)
 - 3.1. [Install Necessary Plugins in Jenkins](#31-install-necessary-plugins-in-jenkins)
- 3.2. [Configure Jenkins to Connect to GitHub](#32-configure-jenkins-to-connect-to-github)
- 3.3. [Create a New Pipeline Job](#33-create-a-new-pipeline-job)
- 3.4. [Implement Webhooks for Continuous Integration](#34-implement-webhooks-for-continuous-integration)
4. [Setting Up Git Flow](#4-setting-up-git-flow)
- 4.1. [Install Git Flow Tools](#41-install-git-flow-tools)
 - 4.2. [Initialize Git Flow in the Repository](#42-initialize-git-flow-in-the-repository)
5. [Creating Jenkinsfile](#5-creating-jenkinsfile)
6. [Testing and Validation](#6-testing-and-validation)
7. [Conclusion](#7-conclusion)

## 1. Project Overview

The project aims to set up Jenkins, a popular automation server, to automate the build and test process of code changes pushed to a GitHub repository. The Git Flow branching model is applied to manage the development process effectively. A Jenkinsfile is used to define the pipeline stages for building, testing, and deploying the code.

## 2. Prerequisites

Before starting the configuration process, ensure the following prerequisites are met:

- Access to a Jenkins server.
- A GitHub account with the repository where the code will be hosted.
- Git installed on the Jenkins server.
- Necessary permissions to install plugins in Jenkins.

## 3. Configuration Steps

### 3.1. Install Necessary Plugins in Jenkins

- Navigate to "Manage Jenkins" > "Manage Plugins" > "Available".
- Install the following plugins:
    - Git Plugin
    - Pipeline Plugin
    - GitHub Integration Plugin

### 3.2. Configure Jenkins to Connect to GitHub

- Go to "Manage Jenkins" > "Manage Credentials".
- Add GitHub credentials with your username and token.
- Ensure GitHub Integration Plugin is installed.
- Configure GitHub webhook for Jenkins integration.

### 3.3. Create a New Pipeline Job

- Click on "New Item" in Jenkins.
- Name your pipeline job (e.g., "GitHub Pipeline") and choose "Pipeline" as the type.
- Configure the pipeline script from SCM (choose Git).
- Enter the repository URL, credentials, and specify the branch to build (e.g., `*/develop`).

### 3.4. Implement Webhooks for Continuous Integration

To ensure that Jenkins automatically triggers a new build every time changes are pushed to the connected branch in the GitHub repository, follow these steps to set up webhooks:

1. **GitHub Repository Settings:**

   - Go to your GitHub repository settings.
   - Select "Webhooks" from the options.

2. **Add a New Webhook:**

   - Click on "Add webhook" or "Create webhook".
   - Enter the Payload URL: `http://<your-jenkins-url>/github-webhook/`
   - Set the Content type to `application/json`.
   - Select the events to trigger the webhook (e.g., "Just the push event").
   - Ensure the webhook is active.
   
![2](https://github.com/Mohab-Hesham/Jenkins_Pipeline/assets/161193942/5ff25b3a-405e-4351-affa-8a9cfb39a543)

3. **Jenkins Configuration:**

   - Ensure the GitHub Integration Plugin is installed in Jenkins.
   - Create a new Pipeline job in Jenkins as described in step 3.3.
   - In the Pipeline configuration, select "Pipeline script from SCM" and choose "Git" as the SCM.
   - Enter the repository URL, credentials, and specify the branch to build (e.g., `*/develop`).

4. **Configure Jenkins API Endpoint:**

   - Go to "Manage Jenkins" > "Configure Global Security".
   - Scroll down to "CSRF Protection" and uncheck "Prevent Cross Site Request Forgery exploits".
   - Save the changes.

With the webhook configured, changes pushed to the GitHub repository will trigger Jenkins to automatically initiate a new build of the pipeline configured in step 3.3.

## 4. Setting Up Git Flow

### 4.1. Install Git Flow Tools

- Install Git Flow tools on the Jenkins server.
- Use appropriate commands to install Git Flow based on your operating system.

### 4.2. Initialize Git Flow in the Repository

- Navigate to the repository directory.
- Initialize Git Flow using the command: `git flow init`.
- Follow the prompts to set up default branch names for development and production releases.

## 5. Creating Jenkinsfile

- Create a Jenkinsfile in the root directory of the repository.
- Define pipeline stages for building, testing, and deploying the code changes.
- Customize the Jenkinsfile according to project requirements.

## 6. Testing and Validation

- Push code changes to the develop branch of the GitHub repository.
- Verify that Jenkins automatically triggers a build.
- Check the Jenkins console output to ensure successful execution of build and test stages defined in the Jenkinsfile.
  
 ![1](https://github.com/Mohab-Hesham/Jenkins_Pipeline/assets/161193942/cd4e111f-a1fe-40df-9520-54a9ee1590f7)

## 7. Conclusion

In conclusion, setting up Jenkins for CI/CD with GitHub using the Git Flow branching model
