🎯 Project Title (use this)

End-to-End CI/CD Pipeline for Containerized Node.js Application on AWS

🧠 What this project actually does

This project implements a fully automated deployment pipeline where:

Every time you push code → application is built → containerized → pushed → deployed → and served via a load balancer

⚙️ Architecture Components

You used:

AWS CodePipeline → Orchestrates CI/CD
AWS CodeBuild → Builds Docker image
Amazon ECR → Stores container images
Amazon ECS → Runs containers
Application Load Balancer → Exposes app publicly
(GitHub → source trigger)
🔄 End-to-End Flow (this is the core)
1. Code Push
Developer pushes code to GitHub
2. Pipeline Trigger
AWS CodePipeline detects change
3. Build Phase
AWS CodeBuild:
Builds Docker image
Tags image
Pushes to ECR
Generates imagedefinitions.json
4. Artifact Handoff
imagedefinitions.json tells ECS:
Which container
Which image to deploy
5. Deployment Phase
Amazon ECS:
Creates new task definition revision
Pulls latest image from ECR
Replaces running containers
6. Traffic Routing
Application Load Balancer:
Routes user requests to ECS tasks
Ensures high availability
7. Final Output
Application accessible via Load Balancer URL
