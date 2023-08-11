# Dotnet-sample-webapp
ASP.NET Web application deployment on Azure Kubernetes Services

Azure Kubernetes Services:
Agenda:
- ASP.NET Web application deployment on Azure Kubernetes Services through Azure DevOps CI/CD

Flow:
- ASP.NET Web application creation
- DockerFile creation - Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. 
- Push changes in Azure Repos (Along with DockerFile)
- Build and Push Image (ACR Repository)
- Deploy (AKS)
- Creation of deployment.yml and service.yml files

Steps:
1. Import the code from github to Azure repo.
2. Make sure you have Dockerfile, Manifest files(deployment.yml, service.yml)
3. Remove azure-pipelines.yml and create Manually for better understanding.
4. Create build pipeline (azure-pipelines.yml), select new pipeline --> Azure repo --> select your repo --> choose Azure kubernetes one and provide the details and create it.
5. Before deploying you need to modify one thing.. update the yml files as below.
<img width="257" alt="image" src="https://github.com/levitate-harinathreddy/dotnetwebapp/assets/121453003/6cd8c6fb-0b06-4e6d-91f0-60a4b04077c0">
<img width="278" alt="image" src="https://github.com/levitate-harinathreddy/dotnetwebapp/assets/121453003/303d1d8e-21f0-4d91-9b30-d3440b3f4cd4">
<img width="278" alt="image" src="https://github.com/levitate-harinathreddy/dotnetwebapp/assets/121453003/862c4c0a-cd8e-4a89-889e-bb5700881ec6">
<img width="341" alt="image" src="https://github.com/levitate-harinathreddy/dotnetwebapp/assets/121453003/a6237064-207e-4f8f-b4c2-6ea034b8777b">
6. Add Publish after copy files
7. Run the pipeline
8. Install the Docker
   https://docs.docker.com/engine/install/ubuntu/
9. Go to manifests in repo and change the ACR name and your repo names in both deployment.yml & service.yml files
   


Commands:
// This will allow to track new POD creation

kubectl get pods --watch

// We will then install the kubectl tool

az aks install-cli --install-location=./kubectl

// This allows kubectl to connect to the Kubernetes cluster

az aks get-credentials --resource-group devopsmela-rg --name devopsmelaAKS 

Pre-defined Variables:

$(Pipeline.Workspace)
- The local path on the agent where all folders for a given build pipeline are created.
