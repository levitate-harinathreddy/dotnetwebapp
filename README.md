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
