# DevSecOps for DoD Workloads on Azure

This article defines DoD DevSecOps (DSOP) architectural and container maturity requirements and how Azure addresses and accounts for them with unique platform capabilities and solutions.

## DoD Area Requirements
Here are some key DoD cloud-native requirements areas that Azure capabilities map against.

* *Platform*. The container hosting/orchestration okay coplatform which leverages Kubernetes. Mapped Azure services include: AKS (Azure Kubernetes Service), ARO (Azure RedHat OpenShift), and ECP (Edge Container Platform).
* *Secure Zero Trust Infrastructure*. The networking layer of the DevSecOps ecosystem that handles requests securely. Mapped Azure services include: N/A as Azure Native Service Mesh in progress.
* *Containers*. This is the actual container atomic component of the architecture - down to the actual container image leveraged, a DoD application must have a high level of security. Mapped Azure services include: MCR (Microsoft Container Registry) or N/A as secure MSFT container images will be hosted in [Repo One](https://repo1.dsop.io).
* *CI/CD*. The DevOps pipeline that helps developers write new code, build new app images, and push new updates to your application workload. Mapped Azure services include: Azure DevOps and GitHub.
* *Supporting Tools and Services*. This encompasses all of the tools and services that help maintain the DevSecOps architecture circled around DoD principles like continous defensibility and observability. Mapped Azure services include: ACR (Azure Container Registry), Azure Securiy Center, Azure Policy, Container Insights, Log Analytics, Application Insights.

## Platform (Container Hosting Platform)
Platform use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.

* *I want to run a cluster with least-privilege access*. 
    * AKS: supported. Azure AKS provides all of the capabilities to run Kubernetes clusters with least privilege. Customer will have to deploy an AKS cluster with RBAC enabled and create the linkage between an AAD group, Kubernetes namespace and Kubernetes roles and binding.
    * ARO: supported. ARO provides all of the capabilities to run Kubernetes clusters with least privilege. Customer will have to deploy an AKS cluster with RBAC enabled and create the linkage between an AAD group, Kubernetes namespace and Kubernetes roles and binding.

## Secure Infrastructure (Zero Trust)
Networking with Kubernetes use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.


* *I want to have the ability to encrypt (mTLS), isolate and control service-to-service traffice natively within the Kubernetes context*. 
    * AKS: not supported, in progress. This is currently a user responsibility to install. A service mesh is not installed natively as a part of deploying a AKS cluster today but any service mesh (Istio, LinkerD, Consul) can be deployed and leveraged by the cluster administrator. Several existing Helm charts simplify the deployment of a service mesh to a AKS cluster. The Azure Networking team is actively working on a native service mesh that AKS will leverage.
    * ARO: supported. ARO can leverage the OpenShift native servicemesh that is based off Istio. In addition, other servicemesh’s can be installed in the cluster by the cluster administrator. This is auto-installed.
    
## Containers
Container image use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.

* *I want to deploy my cloud native application from a set of trusted and validated container images (that exist on a DoD repo)*. 
    * MCR (Microsoft Container Registry): not supported, in progress. Official Microsoft MCR images have not been run through the DoD hardening pipeline. Microsoft engineering are actively working to drive the Windows Server and SQL Server container through the DoD hardening process and merge into DoD Repo One. The longer term goal is that Microsoft will develop an automated process that periodically pulls from the MCR repo into the DoD hardening pipeline for scan and remediation.

## CI/CD
DevOps pipeline use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.

* *I want to secure the image supply chain by securing app code vulnerabilities, insecure version control, tainted base images, insure build automation environments, and insecure private image repos.*. 
    * GHES (GitHub Enterprise Server): not supported, in progress. GitHub Enterprise Server supports the use of actions to ensure on a regular basis as defined by the DoD new container images are pulled from vendor sources and deployed to repo one in a completely automated fashion.
    
## Supporting Tools and Services
Additional tools of the ecosystem use case requirements from the DoD, against Azure Platform (container/Kubernetes platform) capabilities and solutions.

* *I want to adopt container-specific vulnerability management tools and processes for images and prevent compromises (at build time)*. 
    * ACR (Azure Container Registry): supported. Azure Container Registry provides the ability to scan containers natively with ACR supplying container build time scanning and remediation. This is actively being expanded to include DoD recommended build time scanners (e.g. Twistlock).

## Deploying a starting point automated DevSecOps solution
Azure Global has developed an automated deployable DevSeCOps ecosystem that meets many of the DoD high defensibility and observability requirements listed above. The solution leverages Azure technologies like Azure Blueprint and RedHat OpenShift containers. 

Here are the architectural components of the automated DevSecOps ecosystem. Read more [here](https://github.com/Azure/ato-toolkit/tree/master/automation/openshift)

* *Secure infrastructure*. Use the [Zero Trust Blueprint](https://github.com/Azure/ato-toolkit/automation/zero-trust-architecture) to setup strongly governed components like networking, storage, and monitoring that abide by the Zero Trust "never trust, always verify" philosophy on Azure.
* *Container orchestration*. Use the [secure OpenShift deployment](https://github.com/Azure/ato-toolkit/tree/master/automation/openshift/ocp3.11) to deploy a functional OpenShift 3.11 cluster.
* *Workload*. Use the [Iron Bank verification script](xxx) to ensure you're using a secure Docker image. 

> [!NOTE]
> For a full end-to-end tutorial of the solution [see demo video here](https://www.youtube.com/watch?v=gntpwbeWbak).
> 
> 
