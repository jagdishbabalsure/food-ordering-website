# Foodies CI/CD Walkthrough

This document explains the architecture and automated deployment process for the Foodies Landing Page.

## Architecture Explanation
The application follows a cloud-native CI/CD architecture on AWS. The source code is maintained in a Git repository, which triggers an automated pipeline upon every push. The pipeline builds the application and deploys it to a fleet of EC2 instances running Nginx.

## Pipeline Stages
1. **Source**: AWS CodePipeline detects changes in the repository.
2. **Build**: AWS CodeBuild runs the `buildspec.yml` to package files and prepare artifacts.
3. **Deploy**: AWS CodeDeploy uses `appspec.yml` to install the latest files on EC2 and restart the server.

## Build Process
During the build phase, CodeBuild:
- Provisioning a build environment.
- Installing necessary CLI tools.
- Validation of project structure.
- Archiving the files for the deployment stage.

## Deployment Process
The deployment phase on the EC2 instance involves:
- Stopping the current Nginx traffic if necessary.
- Copying new files to `/var/www/html/`.
- Running `scripts/start_server.sh` to restart the service and set permissions.
- Verifying the health of the application.

## Required Screenshots Section
*Include documentation of the following AWS console views:*
- CodePipeline Dashboard: Success status for all stages.
- CodeBuild Logs: Output showing "Build completed successfully".
- CodeDeploy Deployment Group: Targeted EC2 instances.
- EC2 Instance Details: Running state and security groups.

## Final Website Output Section
The final result is a publicly accessible, highly performant landing page.
- URL: `http://<ec2-public-ip>`
- Expected Result: A fully interactive food ordering site with animations and smooth navigation.

---
*Created by Antigravity*
