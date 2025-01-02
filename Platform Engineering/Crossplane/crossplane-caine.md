# How to Design a Platform Engineering Capability to Deliver Hybrid Cloud Value at Scale

## The Rise of New Technical Debt
The heart of ensuring value from adopting hybrid cloud is “Build Once, Deploy Anywhere, Manage Consistently”. In any large enterprise IT organisation, the value is measured as cost savings and enabling the business to be agile. This basically means increasing developer productivity and release agility with people spending less effort on mechanical, repeatable tasks and more on co-creating innovative solutions to business problems and opportunities.

With the continued rise of technology varieties that the multi-cloud world brings there is a danger of more effort spent on building and maintaining the environments that applications run in, compared to innovating, and improving the applications that power the transactions of a company’s business model. In the Cloud Engagement Hub we research and assess any emerging technology that can contribute to achieving value from cloud — especially innovative open source projects relevant to hybrid cloud capabilities.

In this article we will explore the emerging trends in software delivery lifecycle design and engineering technologies to contain the unchecked evolution of new technical debt and in particular look at the emerging open source project Crossplane.

The modern multi-cloud technology landscape is overly complex by necessity. The capabilities of public cloud hyperscalers and their continual rapid innovation has given rise to many fantastic and foundational technologies. Application developers and platform engineers are contending with multiple inter-related technology stacks e.g., orchestration, registry, service mesh, event streaming and so on. It is further compounded by designing and operating applications to use these stacks in multiple opinionated ways prescribed by the public cloud hyperscalers.

The value of Hybrid Cloud consumption over multi-clouds puts emphasis on a service consumption model against a single standard and consistent, yet flexible, platform. Such platforms are often open-source based and overlay value-add solutions compared to simply consuming the raw piece parts of cloud provider native offerings e.g., build management, container deployment, image management, security hardening.

## The Convergence of Engineering Models
In any complex organisation, the role of standards should support creativity whilst ensuring consistency and responsibility. When you establish an enterprise application and platform architecture inextricably linked to cloud technologies and cloud-native approaches at scale then that standardisation needs to be designed.

We can greatly increase the standardisation of Build AND Run for both Applications AND the Platforms they depend on.

Let’s look at the supply chain of components to build and run a modern cloud native application.

lifecycle of component development needed to build an enterprise cloud native application

DevOps has become a well-trodden approach to standardise the automation and integration of the processes of application development and platform operations. The early days of cloud native delivery and innovation connected the DevOps lifecycle teams directly to the public cloud provider’s sweet shop of services. Once enterprises moved beyond simple digital front ends, they realised the greater accountability and rigour associated with operating complex systems on the cloud.

This gave rise to enterprise Platform Engineering Teams. Their goal is to direct and create the platform services that are right for the enterprises to be using.

1. First the team adopt a subset of services from the various public cloud provider catalogues. The adoption certifies each service against the enterprise control framework (risk, security, resilience, recovery planning etc).
2. The enterprise must then manage those services for consumption. The enterprise catalogue can add role-based access controls as to which teams can use which services and which versions (without stagnating and ensure continuous delivery)
3. Base services can be consumed directly or composed into groups (e.g., a database and a firewall rule) to be consumed. Additionally, only the provider settings relevant to the enterprise can be exposed all geared to hide complexity and implement policy guardrails.

This pipeline converges to an enterprise catalogue of application deployment and composite platform services into “stacks” that DevOps project teams consume as part of their “you build it, you run it” role delivering the application to the business.

##  The Significance of the Control Loop
There are hundreds of articles about how Kubernetes is an extensible platform for managing containerised workloads and services. It is much more than this and one of its most powerful features is as a control plane. Kubernetes manages resources through their APIs, and the control loop continually reconciles drift from the specification in effect e.g., if a pod dies it will be restarted.

It is the extensible nature of Kubernetes and the use of this control loop that means it is not just container deployments that can be described and managed. If a service is accessible and managed through an API the Kubernetes can manage it as a resource and ensure it continually exists according to a desired state. There has been an evolution of various Custom Resource Definitions (including those from the Red Hat OpenShift Container Platform) that enhance developer and platform engineering capabilities. We are now seeing ones that can define, compose and lifecycle cloud platform services.

## Platform as a Product — Introducing Crossplane
Crossplane is an open-source Kubernetes add-on that can define and compose platform services. It can be used to implement a self-service enterprise version of underlying platform services from cloud providers, abstracting away any unnecessary platform provider specifics the enterprise doesn’t need to or want to expose. For example the cloud provider might offer v9, 10, 11 and 12 of PostgreSQL in their database service offerings, but the enterprise only exposes v11 and v12 as possible options at provision time.

Crossplane has parallels to Terraform but surpasses it by nature that it is a control plane. They are both modular and declarative, but Crossplane delivers both configuration and access control abstraction. Terraform needs to be invoked to apply an update, and that invocation almost always has to re-run the configuration to the stack ‘all or nothing’. As a control plane, Crossplane avoid this with isolated control loops each continually ensuring each component of the platform stack is at a particular state.

Crossplane is an enabler for Platform Engineering Teams to create opinionated “stacks” declaratively. They can create consistent developer-oriented abstractions that can be self-service consumed by DevOps teams. They create and use instances of these platform abstractions with the same configuration parameters, but different underlying provider instances (e.g., local Postgres service or public cloud Postgres) depending on which stage of the lifecycle (development through to production) the project is at. From their self-served stack the DevOps teams build and deploy their application onto them, bringing automatic adherence to consistent security, access control and other enterprise guard rails.

## Standardising the application deployment — the OpenShift model
The Red Hat OpenShift ecosystem brings a programming model that is geared to the least number of moving parts at the point of consumption by an application builder and deployer. This means less lines of code and instructions to manage, meaning scalable repeatability with less room for error.

In an enterprise’s adoption of the OpenShift lifecycle there will evolve a standard set of patterns for build and deployment of applications. These are codified through reusable templates that tools such as `oc new app` and `odo` use. A DevOps project team can now build pipelines that automates their creation and management of infrastructure services controlled by Crossplane, and application build and deploy actions that consume those services.
Exploring the Crossplane and OpenShift engineering model

In this walkthrough here I show how Crossplane and OpenShift can work together, and an application consumes cloud services that are under Crossplane management.
screenshot of https://github.com/jeremycaine/crossplane-with-openshift github page where crossplane and openshift together is explored

It takes you through an installation of Crossplane and cloud provider on OpenShift and then how enterprise specific compositions of cloud services are represented and used by an application deployed in an OpenShift cluster.

## Crossplane and OpenShift
Technology serves an enterprise to achieve its business outcomes. Applications need to be always on and adaptable to execute the business model (e.g., sell product; service customer; report to regulator etc). Agile and DevOps approaches in delivering those applications address those business needs. To scale a business and its applications on the cloud we introduce a hybrid cloud platform and operating model irrespective of which public cloud provider or infrastructure location the application might run on.

With the OpenShift application deployment model and Crossplane composite platform services and configurations, the DevOps lifecycle is executed across one opinionated “full stack” right-sized for the enterprise within known guard rails. This contributes to achieving value from hybrid cloud by standardising the technical execution model and operating model of Build and Run, for both the Application and its Platform.