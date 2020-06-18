# DevSecOps for DoD Workloads on Azure

This article defines DoD DevSecOps (DSOP) architectural requirements and how Azure addresses and accounts for them with unique platform capabilities.

## DoD Area Requirements
Here are some key DoD cloud-native requirements areas that Azure capabilities map against.
* *Platform*. The container hosting/orchestration platform which leverages Kubernetes. Mapped Azure services include: AKS (Azure Kubernetes Service), ARO (Azure RedHat OpenShift), and ECP (Edge Container Platform).
* *Secure Zero Trust Architecture*. The networking layer of the DevSecOps ecosystem that handles requests securely. Mapped Azure services include: N/A (Azure Native Service Mesh in progress).
* *Containers*. This is the actual container atomic component of the architecture - down to the actual container image leveraged, a DoD application must have a high level of security. Mapped Azure services include: N/A (secure MSFT container images will be hosted in [Repo One](https://repo1.dsop.io)).
* *CI/CD*. The DevOps pipeline that helps developers write new code, build new app images, and push new updates to your application workload. Mapped Azure services include: Azure DevOps and GitHub.
* *Supporting Tools and Services*. This encompasses all of the tools and services that help maintain the DevSecOps architecture circled around DoD principles like continous defensibility and observability. Mapped Azure services include: Azure Securiy Center, Azure Policy, Container Insights, Log Analytics, Application Insights.

## Platform (Container Hosting Platform)
Platform use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.

* *I want to run a cluster with least-privilege access*. 
    * AKS: supported. Azure AKS provides all of the capabilities to run Kubernetes clusters with least privilege. Customer will have to deploy an AKS cluster with RBAC enabled and create the linkage between an AAD group, Kubernetes namespace and Kubernetes roles and binding.
    * ARO: supported. ARO provides all of the capabilities to run Kubernetes clusters with least privilege. Customer will have to deploy an AKS cluster with RBAC enabled and create the linkage between an AAD group, Kubernetes namespace and Kubernetes roles and binding.

## Deploying a starting point automated DevSecOps solution
Azure Global has developed an automated deployable DevSeCOps ecosystem that meets many of the DoD high defensibility and observability requirements listed above. The solution leverages Azure technologies like Azure Blueprint and RedHat OpenShift containers. 

Here are the architectural components of the automated DevSecOps ecosystem. Read more [here](https://github.com/Azure/ato-toolkit/tree/master/automation/openshift)

* *Secure infrastructure*. Use the [Zero Trust Blueprint](https://github.com/Azure/ato-toolkit/automation/zero-trust-architecture) to setup strongly governed components like networking, storage, and monitoring that abide by the Zero Trust "never trust, always verify" philosophy on Azure
* *Container orchestration*. Use the [secure OpenShift deployment](https://github.com/Azure/ato-toolkit/tree/master/automation/openshift/ocp3.11) to deploy a functional OpenShift 3.11 cluster
* *Workload*. Use the [Iron Bank verification script](xxx) to ensure you're using a secure Docker image 

> [!NOTE]
> For a full end-to-end tutorial of the solution [see demo video here](https://www.youtube.com/watch?v=gntpwbeWbak).
> 
> 
