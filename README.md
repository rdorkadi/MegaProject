# Springboot CICD 

## CICD - Architecture 
![Screenshot 2024-07-11 at 5 23 56 PM](https://github.com/basahota/aws-cicd/assets/25712816/342e97bf-5fbe-490f-bf76-b5bdd33ce415)


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

#### Step 3: Create an ECS Cluster

In AWS Console ECS, create a new cluster with Fargate as the launch type.

#### Step 4: Define a Task Definition

Specify Docker Container details and ensure the cotainer port(8080) matches your Springboot app.

#### Step 5: Set up GitHub repository

Use GitHub for your code repository.

#### Step 6: Set up AWS CodeBuild

1. AWS CodeBuild will build your project based on the buildspec.yml instructions.
2. The Docker image is built, tagged, and pushed to Amazon ECR.

#### Step 7: Set Up AWS CodePipeline

1. In AWS CodePipeline, create a pipeline.
2. Set the source as your repository. (i.e. Git Repo)
3. Add the CodeBuild for step 2 in the Pipeline to build the application.
4. After the build stage, we need to add a deploy stage i.e. use Amazon ECS as the deploy provider and choose your ECS cluster, service, and task definition.

#### Step 8: Trigger the Pipeline

Push any code changes to your repository, and CodePipeline will automatically build and deploy your Spring Boot app.

#### Step 9: Access the Spring Boot Application

Voila! Now you can access your app via the the public IP of the ECS task.