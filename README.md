# Springboot CICD 

## Step-by-Step Deployment

#### Step 1: Set up Springboot Application
Ensure you have a working springboot application that you want to containerize and deploy. 

#### Step 2: Adding Dockerfile and Buildspec.yaml files

##### 2.1. Add Dockerfile to the Project
The Dockerfile defines how to package your springboot application into Docker Container. 

##### Note: 
Make sure to build the springboot JAR File before this step is running. 

```bash
mvn clean package
```

##### 2.2. Add buildspec.yaml file for CodeBuild

The buildspec.yaml file contains the instructions that the CodeBuild will use to build and deploy your application.

CICD - flow
![Screenshot 2024-07-11 at 5 23 56 PM](https://github.com/basahota/aws-cicd/assets/25712816/342e97bf-5fbe-490f-bf76-b5bdd33ce415)
