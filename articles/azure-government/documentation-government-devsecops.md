# DevSecOps for DoD Workloads on Azure

This article defines DoD DevSecOps (DSOP) architectural requirements and how Azure addresses and accounts for them with unique platform capabilities.

## DoD Area Requirements
Here are some key DoD cloud-native requirements areas that Azure capabilities map against.
* *Platform*. The container orchestration platform which leverages Kubernetes. Mapped Azure services include: AKS (Azure Kubernetes Service), ARO (Azure RedHat OpenShift), and ECP (Edge Container Platform).
* *Secure Zero Trust Architecture*. The networking layer of the DevSecOps ecosystem that handles requests securely. Mapped Azure services include: N/A (Azure Native Service Mesh in progress).
* *Containers*. This is the actual container atomic component of the architecture - down to the actual container image leveraged, a DoD application must have a high level of security. Mapped Azure services include: N/A (secure MSFT container images will be hosted in [Repo One](https://repo1.dsop.io)).
* *CI/CD*. The DevOps pipeline that helps developers write new code, build new app images, and push new updates to your application workload. Mapped Azure services include: Azure DevOps and GitHub.
* *Supporting Tools and Services*. This encompasses all of the tools and services that help maintain the DevSecOps architecture circled around DoD principles like continous defensibility and observability. Mapped Azure services include: Azure Securiy Center, Azure Policy, Container Insights, Log Analytics, Application Insights.

## Components of the solution
Here are the architectural components of the solution.

* *Secure infrastructure*. This layer is secure infrastructure. Developers and security admins need strongly governed components like networking, storage, and monitoring, that abide by the Zero Trust “never trust, always verify” philosophy. When you leverage a Zero Trust model it becomes possible to ensure every request is authenticated, authorized, and inspected before granting access.
* *Container orchestration*. This layer is the container orchestration part of the architecture that deploys and manages Kubernetes nodes. Your compute solution also should be setup and leveraged in a secure way. This is a secure deployment of RedHat OpenShift on Azure. The deployment is unique as it’s (1) fully automated and runs quickly with close to 1-click and (2) has hardening baked-in, including a script that STIGs all host OSes. All of this neatly deploys on top of the Zero Trust Blueprint – inheriting and building on its security and allowing your architecture to remain compliant.
* *Workload*. Lastly, we have the top layer - deploying your application workload! Here you pull a trusted container image from [Iron Bank](https://ironbank.dsop.io), which is the DoD’s central repository for hardened Docker images, and use it to seamlessly deploy a basic web app.

## Deploying the solution
* *Secure infrastructure*. Use the [Zero Trust Blueprint](https://github.com/Azure/ato-toolkit/automation/zero-trust-architecture) to setup strongly governed components like networking, storage, and monitoring that abide by the Zero Trust "never trust, always verify" philosophy on Azure
* *Container orchestration*. Use the [secure OpenShift deployment](https://github.com/Azure/ato-toolkit/tree/master/automation/openshift/ocp3.11) to deploy a functional OpenShift 3.11 cluster
* *Workload*. Use the [Iron Bank verification script](xxx) to ensure you're using a secure Docker image 

> [!NOTE]
> For more information on Parts 2 and 3 of solution deployment, e.g. Container Orchestration and Workload, please [contact Microsoft-trusted partner CloudFit](https://www.cloudfitsoftware.com/contact-us/)
> 
> 

For a full end-to-end tutorial of the solution [see demo video here](https://www.youtube.com/watch?v=gntpwbeWbak).
