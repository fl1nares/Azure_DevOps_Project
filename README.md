## Introduction 

This project is based on the "Azure DevOps: Zero to Hero Course" Available [here.](https://aka.ms/AzureDevOps/ZeroToHero)

## Preparation

<details><summary>Create a new Azure DevOps Organization (i.e. MyflOrg, name must be unique)</summary></details>
<p></p>
<details><summary>Create a new Project (i.e ADODemo)</summary></details>
<p></p>

<details><summary>Go to Project Settings / General / Overwiew - Use Agile Process for the new Project</summary></details>
<p></p>


<details><summary>Optional, Go to Boards / Project Config - Create Sprints & Areas</summary>

<p></p>


<img src="images/0.png" width="70%" />
<img src="images/1.png" width="70%" />

<p></p>
</details><p></p>



<details><summary>Create a Self-Hosted Agent.</summary>
<p></p>
Microsoft stopped automatically granting free compute time (parallelism) to new Azure DevOps organizations to prevent crypto-mining abuse and you will get [error]No hosted parallelism has been purchased or granted. 

Solution

- Request Microsoft to enable your free tier.(2-5 business days) or
- Create a Self-Hosted Agent

</details> <p></p>

<details><summary>Step 1: Create a Personal Access Token (PAT)</summary><p></p>

- In Azure DevOps, click the User Settings icon (top right, next to your avatar) and select Personal access tokens.
- Click + New Token.
- Name: AgentToken
- Scope: Select Custom defined and then click Show all scopes at the bottom.
- Find Agent Pools and select Read & manage.
- Click Create and copy the token immediately (you won't see it again).</details> <p></p>

<details><summary>Step 2: Register the Agent</summary><p></p>

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
<details><summary>Create container registry</summary><p></p>


<img src="images/2.png" width="70%" /> <p></p>
<img src="images/4.png" width="70%" />

</details> <p></p>

<details><summary>Create Service Connection</summary><p></p>

- Go to Project Settings / Pipelines / Service Connections 
- Add New service Connection - Type Docker registry 

<img src="images/5.png" width="70%" />

</details><p></p>

<details><summary>Create App Service</summary><p></p>


- Go to Azure - App Services
- Create - Web App

<img src="images/6.png" width="70%" /><p></p>
<img src="images/7.png" width="70%" />
- Create another 2 web apps for test and prod named ADODemo-Test & ADODemo-prod

</details><p></p>

<details><summary>Upload ssh-key to Deploy to external environment (aws/on-prem)</summary><p></p>
- Go to  Pipelines / Library / Secure files and upload the SSH-Key file needed by the script used in DeployProdAWS Stage.<p></p>


<img src="images/8.png" width="70%" />

</details><p></p>

## Cloning the Repo & Run the Pipeline

<details><summary>Go to Repo / Files and Clone this github<summary></details>
<p></p>

<details><summary>Go to Pipelines and open the azure-pipelines.yml<summary></details>
<p></p>

<details><summary>Run the Pipeline (manually approve the DeployProdAzure & DeployProdAWS stages)</summary><p></p>
<img src="images/9.png" width="70%" /><p></p>
<img src="images/10.png" width="70%" />
</details>
<p></p>

<details><summary>Go to Azure App Services and open the deployed app by clicking on Default domain url</summary><p></p>

<img src="images/11.png" width="70%" /><p></p>
<img src="images/12.png" width="70%" />
</details><p></p>
