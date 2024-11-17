# code-quality-security-pipeline
This project automates code quality analysis and security vulnerability scanning for code repositories, providing real-time feedback on code health and compliance. The pipeline uses Jenkins to trigger scans and orchestrate tools such as Snyk and Bandit (for security). The results are automatically aggregated into comprehensive reports and notifications to support informed, immediate action on issues.

# Jenkins Setup:
1. Setup Docker, WSL2, and Jenkins (WSL 2 is not important if you arent using windows)
2. Pull docker image for Jenkins on docker hub (Ensure that WSL 2 based engine is checked for docker; this is to ensure that we can run linux based containers on a windows environment)
3. Create bridge network in Docker for Jenkins and run a docker-in-docker image
4. Using blue ocean, run a dockerfile at your chosen port
5. Unlock Jenkins, download recommended plugins, create admin user

Running builds directly on the jenkins controller can pose security risks and impact system stability.
Some Risks might include:
- Security Vulnerabilities - Potentially expose sensitive data
- Resource Contention - CPU and memory resources could affect performance when building
- Stability Concerns - Could lead to system crashes, unintended behavior, or a full compromise of the jenkins controller

In order to mitigate this, I chose to create an agent using Microsoft Azure DevOps. 

# Azure DevOps VM Agent Hosting Setup
1. Create Azure DevOps Account
2. Using Jenkins, install the "Azure VM Agents" plugin
3. configure an Azure Service Principle credential in "Manage Jenkins" > "Credentials"
4. In Azure Entra settings, find the subscription ID
5. Create a new application in app registrations in order to get your client ID, client secret and tenant ID


# Notes
First Version
- Ran into local security compatibility issues with Windows, switched to using docker to run my pipeline. 
- Tools used: Git, Docker, WSL 2, Jenkins, bash, powershell...

Open Source
- Bandit
- Azure DevOps VM

Closed Source Tools
- Synk (enterprise)
- Sonarqube (enterprise; 14-day trial)



# Future Additions
- Compatibility with SVN
- Automatic remediation
- Enhanced reporting with visualization (Matlab or Power BI)
- Code Coverage Analysis
- Code style reinforcements
- Fine-Grained notifications
- User Role-Based access and customized reports
