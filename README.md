# Foodies Landing Page

A modern, responsive food ordering landing page powered by an automated AWS CI/CD pipeline.

## Project Structure
- `index.html`: Main structure and SEO metadata.
- `style.css`: Modern design and animations.
- `script.js`: Interactive scroll and form logic.
- `images/`: High-quality food assets.
- `buildspec.yml`: Build configuration for AWS CodeBuild.
- `appspec.yml`: Deployment configuration for AWS CodeDeploy.
- `scripts/`: Deployment scripts.

## CI/CD Workflow
The project uses a complete automated pipeline to ensure that every change pushed to the repository is automatically built, tested, and deployed to a live AWS EC2 instance.

## AWS Services Used
- **AWS CodePipeline**: Orchestrates the entire workflow from source to deployment.
- **AWS CodeBuild**: Compiles any necessary assets and packages the project.
- **AWS CodeDeploy**: Automates the deployment of the build artifacts to EC2.
- **Amazon EC2**: The server hosting the Nginx website.
- **Amazon S3**: Stores the intermediate build artifacts.

## Deployment Steps

### 1. Setup Amazon EC2
- Launch an EC2 instance with Ubuntu or Amazon Linux.
- Install Nginx: `sudo apt install nginx -y`.
- Install the CodeDeploy Agent on the instance.
- Attach an IAM role with `AmazonS3ReadOnlyAccess` and `CloudWatchAgentServerPolicy`.

### 2. Configure AWS CodeBuild
- Create a new project in CodeBuild.
- Connect your source repository (GitHub/S3).
- Select the `buildspec.yml` file in the project root.
- Configure the environment to use an Ubuntu/Amazon Linux runtime.

### 3. Configure AWS CodeDeploy
- Create an application in CodeDeploy.
- Create a Deployment Group.
- Select your EC2 instance by its tag.
- Specify the `appspec.yml` file behavior (overwrite files on `/var/www/html`).

### 4. Create AWS CodePipeline
- Create a pipeline that connects the Source (GitHub), Build (CodeBuild), and Deploy (CodeDeploy) stages.
- Once configured, any code push will trigger an automatic update on your live server.

## Local Development
- Open `index.html` in any modern web browser.
- Ensure `style.css` and `script.js` are in the same directory.
- Images should be placed in the `images/` subfolder.
