## Comprehensive configuration for Devtron with Azure Kubernetes Service From Scratch. (wiki how)

### What is Devtron?
- Devtron is a tool integration platform that allows you to add all your DevSecOps tools in one place when you do not need to open multiple tabs. 
- In devtron, you can manage the lifecycle of microservices, CI, CD, security, cost, debugging, and observability using a user-friendly web interface.

![readme-comic.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662460858198/lt269Kt9R.png align="left")

### Why Devtron!
While Working in a small company/ Medium sized there is always been a problem that
- There are so many Open source Tools for Kubernetes, But Which one to choose
- It's always difficult to configure 
- So many problems 1 Solution

### What is AKS?
Azure Kubernetes Service is a managed container orchestration service based on the open-source Kubernetes ecosystem, which is available on the Microsoft Azure public cloud.

![okkkk.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1662461410002/GYmF5lFxm.jpg align="left")

### Demo
Create and set up the new Azure Kubernetes Cluster service from Scratch

-  First, log in to [Azure Portal](https://portal.azure.com/#home)

- On the **Azure portal** menu or from the **Home page**, Search **Azure Kubernetes Service**

- Under **Service** Section > Select **Kubernetes Service**.

![search dark.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662529262694/AtmjhqEDR.png align="left")

Then click on **Create a Kubernetes cluster** 


![create kubernetes service dark.png .png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662529121356/IdEJUt7Pw.png align="left")


After That Create a New Resource Group as **Devtron**

Give Kubernetes cluster name as **Devtron**



![aks config 1 dark.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662528995478/FWZ-rSzEy.png align="left")


Go to  **Primary node pool** > Select **Node Size** As **D2s V3** 

> For Devtron It required a Minimum 8GB Ram and 2 core CPU Which is ideal for testing purposes 

After that Set **Scale mode** to **Manual** and set **node count** to 2


![aks config 2 dark.png .png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662529010852/xF7oe7ZnF.png align="left")

Keep the thing's default and click **Review+Create**. 

It takes a few minutes to create the AKS cluster. When your deployment is complete then navigate to **Resources**. Here you can see your Kubernetes cluster like this not exact.

![Vuqh8AscE.avif](https://cdn.hashnode.com/res/hashnode/image/upload/v1662529624430/wv7pcw8YN.avif align="left")

After that connect your cluster simply by clicking the **Connect** button on the top of the resource and just follow the instruction. If you get stuck Feel free to ping me(https://linktr.ee/AdityaNarayan.N)

### Install Devtron on AKS  using Helm
![okkkk.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1662569690445/OgJWt38BW.jpg align="left")

copy the following command and run it in the Azure CLI
    
```
helm repo add devtron https://helm.devtron.ai

helm install devtron devtron/devtron-operator \
--create-namespace --namespace devtroncd \
--set installer.modules={cicd}
``` 
The install commands start Devtron-operator, which takes about 20 minutes to spin up all of the Devtron microservices one by one

In the meantime run the following command to check the installation status.
```
kubectl -n devtroncd get installers installer-devtron -o jsonpath='{.status.sync.status}'
```
The command executes with one of the following output messages.

Downloaded (It means The installer has downloaded all the manifests, and the installation is in progress)

![helm and check.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662615016229/gpX06qV4p.png align="left")

Applied (The installer has successfully applied all the manifests, and the installation is complete.)

![status.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662614804761/ysfv2FWok.png align="left")

### Now Get the Dashboard

Run the Following Command to get the Dashboard
```
kubectl get svc -n devtroncd devtron-service \
-o jsonpath='{.status.loadBalancer.ingress}'
``` 
Here you can get output something like this 

![ip.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662615361737/OXWgbbFjn.png align="left")

Now copy the IP and Paste it into the browser and you can see Devtron DashBoard

![dash.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662615854462/92FcoIxok.png align="left")

Run the following credential to get a password 
```
kubectl -n devtroncd get secret devtron-secret -o jsonpath='{.data.ACD_PASSWORD}' | base64 -d
```
>leave Admin as Admin proceed for login

 Hurray, We got our Dashboard 🎉😉

### Set Global Configuration

1. #### Host URL

    - First We have to add the **host URL** but by default Devtron already detects the Host URL from the browser you just have to save it. 

        ![global configuration.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662633282449/VWT-gji4A.png align="left")

2. #### GitOps

    - Now If you have **GitHub Organization** that's great neither you have to create an organization in GitHub.
    - In the **Git Host section** Don't put Your whole Github URL Just leave it as it is.  
    - Give your **Github Organization name** under GitHub Organisation Name
    - Give your **GitHub Account username** username under GitHub Username
    - Now give your personal GitHub token
       - for getting a personal GitHub token move to GitHub **Setting** > **Developer Setting** > **personal 
          access token**
    - At last, Don't forget to save the setting. 

![gitops.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662638686508/Mzg9lK9CE.png align="left")
3. #### Container Registries
    - Here Select **Azure Container Registry** because I want to save my image file in ACR.
    - If you don't have "ACR" you can create one in the Azure portal. 
    - Now give all the information. 
    - if you need a username and password you can find them on the Lefthand side **Access key** 
    
![access key.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662638648602/47ov97-IQ.png align="left")

### 2nd Part is coming Soon where I will show you how you can set up CI/CD in AKS. if you have Any Doubts feel free to connect neither soon I'm coming up with the next blog. 

Make sure to Subscribe to my blog for 2nd blog. 

 ### Summary:-
> - As we can see, How we can Install Devtron in Azure Kubernetes Service
> - Also, Devtron has so many options you can add configuration

### Thank you for reading. Have a great day🤩🥂













