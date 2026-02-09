# Introduction 
This project is on the "Azure DevOps: Zero to Hero Course" Available [here.](https://aka.ms/AzureDevOps/ZeroToHero)

## Prerequisites

<details><summary>Create a new Azure DevOps Organization (i.e. MyflOrg, name must be unique)</summary></details><p></p>
<details><summary>Create a new Project (i.e ADODemo)</summary></details><p></p>

<details><summary>Go to Project Settings / General / Overwiew - Use Agile Process for the new Project</summary></details><p></p>


<details><summary>Optional, Go to Boards / Project Config - Create Sprints & Areas</summary>

<p></p>

![alt text](image.png)![alt text](image-1.png)

<p></p>
</details><p></p>



<details><summary>Create a Self-Hosted Agent.</summary>

Microsoft stopped automatically granting free compute time (parallelism) to new Azure DevOps organizations to prevent crypto-mining abuse and you will get [error]No hosted parallelism has been purchased or granted. 

Solution

- Request Microsoft to enable your free tier.(2-5 business days) or
- Create a Self-Hosted Agent

</details> <p></p>

<details><summary>Step 1: Create a Personal Access Token (PAT)</summary>

- In Azure DevOps, click the User Settings icon (top right, next to your avatar) and select Personal access tokens.
- Click + New Token.
- Name: AgentToken
- Scope: Select Custom defined and then click Show all scopes at the bottom.
- Find Agent Pools and select Read & manage.
- Click Create and copy the token immediately (you won't see it again).</details> <p></p>

<details><summary>Step 2: Register the Agent</summary>

- Go to Project Settings (bottom left) > Agent pools.
- Click on the Default pool.
- Click the New agent button at the top.
- Select your OS (Windows, macOS, or Linux).
- Follow the Download and Configure commands provided in the popup.
- When it asks for Server URL: Use https://dev.azure.com/{your-organization-name}
- When it asks for Authentication type: Press Enter for PAT, then paste your token.
- When it asks for Agent Pool: Press Enter to use Default.
- Run as service: Say Yes (if on Windows/Linux) so it starts automatically.
</details> <p></p>
<details><summary>Create container registry</summary>

- ![alt text](image-2.png)!![alt text](image-4.png)

</details> <p></p>

<details><summary>Create Service Connection</summary>

- Go to Project Settings / Pipelines / Service Connections 
- Add New service Connection - Type Docker registry 
![alt text](image-5.png)

</details><p></p>

<details><summary>Create App Service</summary>


- Go to Azure - App Services
- Create - Web App
![alt text](image-6.png)![alt text](image-7.png)
- Create another 2 web apps for test and prod named ADODemo-Test & ADODemo-prod

</details><p></p>

<details><summary>Upload ssh-key to Deploy to external environment (aws/on-prem)</summary>
- Go to  Pipelines / Library / Secure files and upload the SSH-Key file needed by the script used in DeployProdAWS Stage.

![alt text](image-8.png)

</details><p></p>

CLONING THE REPO & RUN THE PIPELINE

<details><summary>Go to Repo / Files and Clone this github<summary>
</details><p></p>
<details><summary>Go to Pipelines and open the azure-pipelines.yml<summary>
</details><p></p>
<details><summary>Run the Pipeline (manually approve the Deployprod stage)<summary>
</details><p></p>