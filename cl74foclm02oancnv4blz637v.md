## Demystifying Azure Kubernetes Service with Github Actions from Scratch

#### **Github Action**
GitHub Actions gives developers the ability to automate their workflows across issues, pull
requests, and more with cloud-native CI/CD functionality

![actions.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660677791325/Grvhd5IRi.png align="left")

#### Azure Kubernetes Service
Azure Kubernetes Service is a managed container orchestration service based on the open source Kubernetes ecosystem, which is available on the Microsoft Azure public cloud.

![azure-kubernetes-service.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660711449117/2yq8dx3HE.png align="left")

#### **Github Workflow**

- Github Workflow Automate Test, Build, and Deployment, Also they execute on hosted virtual environment 

#### Github Action with Azure Kubernetes Service

- AKS Action allows developers to interact with the Kubernetes clusters from GitHub Workflow easily, they can be used alone or together. It makes them very reusable and modular.

- Azure starter workflow provides templates for getting started with deploying to AKS or any Kubernetes cluster

- Workflows run in response to events such as pushing to a branch, adding a tag, and making a pull request. They can be run at Cronjob and also by the user itself with a workflow dispatch. 

 ![Git And Github Version Control.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660628648057/TV_DO0dQK.png align="left")

Too much theory it's time for Demo

### Demo

#### Step 1:- Create a New Azure Kubernetes service Cluster from Scratch 

- First, log in to [Azure Portal](https://portal.azure.com/#home)

- On the Azure portal menu or from the Home page, select **Create a resource**.

- Select Containers > **Kubernetes Service**.

- On the Basics page, configure the following options:

![create-cluster-basics.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660670230848/OuqrdwA7n.png align="left")

- Select Next: Node pools when complete.

- Keep the thing's default and click Review+Create

- It takes a few minutes to create the AKS cluster. When your deployment is complete then navigate to Resources. Here you can see your Kubernetes cluster like this.

![aks-portal-dashboard.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660670559903/Vuqh8AscE.png align="left")

- After that connect your cluster simply by clicking the Connect button on the top of the resource and just follow the instruction.

#### Step 2:- Get the Repo and add Azure Workflow 

- Now it's time to move to [Github Repository](https://github.com/Aditya-Narayan-Nayak/AKS-GitHub-Actions-Demo) and fork this Repository. Basically, it's a Demo Python voting app.

- Then go to "Action" and create your own workflow by simply clicking "New Workflow" at the top of the page

![Screenshot (360).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1660672594214/O7TrjBcuH.jpg align="left")
- There you can search "**AKS**" and Click on "**Deploy to AKS**"


![Screenshot (361).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1660673587664/6NE7E7wXB.jpg align="left")

#### Step 3:- Configure
Now it's time to configure. To configure this workflow:

1. Set the following secrets in your repository (instructions for getting these can be found at https://docs.microsoft.com/en-us/azure/developer/github/connect-from-azure?tabs=azure-cli%2Clinux):
    - AZURE_CLIENT_ID
    - AZURE_TENANT_ID
    - AZURE_SUBSCRIPTION_ID
2. Set the following environment variables (or replace the values in workflow):
    - AZURE_CONTAINER_REGISTRY (name of your container registry / ACR)
    - RESOURCE_GROUP (where your cluster is deployed)
    - CLUSTER_NAME (name of your AKS cluster)
    - CONTAINER_NAME (name of the container image you would like to push up to your ACR)
    - IMAGE_PULL_SECRET_NAME (name of the ImagePullSecret that will be created to pull your ACR image)
    - DEPLOYMENT_MANIFEST_PATH (path to the manifest yaml for your deployment) 
3. 
    - For more information on GitHub Actions for Azure, refer to (https://github.com/Azure/Actions)
    - For more samples to get started with GitHub Action workflows to deploy to Azure, refer to 
       (https://github.com/Azure/actions-workflow-samples)
    - For more options with the actions used below please refer to https://github.com/Azure/login

#### Step 4:- Run the workflow

![Screenshot (363).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660674213041/Uc4Mj7399.png align="left")

Now commit the changes

#### Step 5:- check pod  
- Wait for confirmation In the meantime you can go to https://shell.azure.com and Run the command 
```
kubectl get po
``` 
```
kubectl get svc
``` 
- There you can see External IP, If it's pending just run the below command again 
```
kubectl get svc
```

![Screenshot (364).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660710375693/ye8sYva1f.png align="left")

- To see the Azure Vote app in action, open a web browser to the external IP address of your service.

![azure-voting-application.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660710631220/Zj6TezOzq.png align="left")

- If you want to change the app then navigate to Repo -> Azure vote -> Azure-vote -> config_file.cfg -> change the values and commit the changes

- Then In Action Again Run the Workflow and Refresh the browser 

Official Docs Azure Kubernetes Service deployment pipeline and GitHub Actions Link:- (https://docs.microsoft.com/en-us/learn/modules/aks-deployment-pipeline-github-actions/)

#### Hurray we got our web app 🎉🎉🥂

### Summary:-
> As we can see, we can directly interact with the Azure Kubernetes cluster completely from Github
> 
> Also, Github Action has so many options you can add more steps in the Job 
> 
> In deploy, GitHub Action has many strategic options like Canary Deployment including service mesh interface or Kubernetes only and blue-green deployment.

Thank you for reading. Have a great day 


