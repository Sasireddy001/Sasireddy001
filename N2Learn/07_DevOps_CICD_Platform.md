# DevOps / CI-CD / Platform Flash Cards

## Core Concepts

**Q: What is DevOps?**  
**A:** DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle and deliver high-quality software continuously.

**Q: What is CI/CD?**  
**A:** CI (Continuous Integration) is the practice of merging code changes frequently and running automated tests. CD (Continuous Delivery/Deployment) automates the release process to production.

**Q: What is the difference between Continuous Delivery and Continuous Deployment?**  
**A:** Continuous Delivery means code is always deployable but requires manual approval. Continuous Deployment deploys automatically without manual intervention.

**Q: What is Infrastructure as Code (IaC)?**  
**A:** IaC is the practice of managing infrastructure using code (e.g., Terraform, CloudFormation) instead of manual processes, enabling version control and reproducibility.

**Q: What is a container?**  
**A:** A container is a lightweight, standalone package that includes everything needed to run an application (code, libraries, dependencies). Docker is the most popular containerization platform.

## Docker

**Q: What is Docker?**  
**A:** Docker is a platform for building, shipping, and running applications in containers. It uses OS-level virtualization for efficiency.

**Q: What is the difference between a container and a VM?**  
**A:** A container shares the host OS kernel and is lightweight. A VM has its own OS kernel and is heavier. Containers start faster and use fewer resources.

**Q: What is a Dockerfile?**  
**A:** A Dockerfile is a text file that contains instructions to build a Docker image. It specifies the base image, dependencies, and commands to run.

**Q: What is a Docker image?**  
**A:** A Docker image is a read-only template with instructions to create a container. Images are built from Dockerfiles and stored in registries.

**Q: What is a Docker container?**  
**A:** A Docker container is a running instance of a Docker image. It is an isolated environment where the application runs.

**Q: What is the difference between `docker run` and `docker start`?**  
**A:** `docker run` creates and starts a new container from an image. `docker start` starts an existing stopped container.

**Q: What is the difference between `docker exec` and `docker attach`?**  
**A:** `docker exec` runs a new command in a running container. `docker attach` attaches to the main process of a running container.

**Q: What is a Docker Compose?**  
**A:** Docker Compose is a tool for defining and running multi-container applications using YAML files. It simplifies orchestrating containers.

**Q: What is the difference between `COPY` and `ADD` in Dockerfile?**  
**A:** `COPY` copies files from the host to the image. `ADD` can also copy from URLs and automatically extract tar files. Prefer `COPY` for simplicity.

## Kubernetes

**Q: What is Kubernetes?**  
**A:** Kubernetes (K8s) is an open-source container orchestration platform for automating deployment, scaling, and management of containerized applications.

**Q: What is a Pod in Kubernetes?**  
**A:** A Pod is the smallest deployable unit in Kubernetes, containing one or more containers that share the same network and storage.

**Q: What is a Deployment in Kubernetes?**  
**A:** A Deployment manages a set of Pods, ensuring the desired number of replicas are running and handling rolling updates and rollbacks.

**Q: What is a Service in Kubernetes?**  
**A:** A Service exposes a set of Pods as a network service, providing stable networking and load balancing.

**Q: What is the difference between a Deployment and a StatefulSet?**  
**A:** Deployments are for stateless applications with interchangeable Pods. StatefulSets are for stateful applications with unique identities and stable storage.

**Q: What is a ConfigMap in Kubernetes?**  
**A:** A ConfigMap stores configuration data as key-value pairs, used to inject configuration into Pods without hardcoding.

**Q: What is a Secret in Kubernetes?**  
**A:** A Secret stores sensitive data (passwords, tokens, keys) in an encoded form, used to inject credentials into Pods.

**Q: What is the difference between a ConfigMap and a Secret?**  
**A:** ConfigMaps store non-sensitive configuration. Secrets store sensitive data and are base64-encoded. Secrets can be encrypted at rest.

**Q: What is a Namespace in Kubernetes?**  
**A:** A Namespace is a logical partition within a cluster, used to organize resources and isolate teams or environments.

**Q: What is a Helm chart?**  
**A:** A Helm chart is a package of Kubernetes manifests (YAML files) that defines a set of resources. Helm is a package manager for Kubernetes.

## CI/CD Tools

**Q: What is Jenkins?**  
**A:** Jenkins is an open-source automation server for CI/CD. It supports plugins for various tools and allows pipeline as code with Jenkinsfile.

**Q: What is a Jenkinsfile?**  
**A:** A Jenkinsfile is a text file that defines a Jenkins pipeline using Groovy syntax. It is stored in the repository for version control.

**Q: What is GitHub Actions?**  
**A:** GitHub Actions is a CI/CD platform integrated with GitHub, allowing you to define workflows in YAML files stored in the repository.

**Q: What is the difference between GitHub Actions and Jenkins?**  
**A:** GitHub Actions is tightly integrated with GitHub and simpler to set up. Jenkins is more flexible and has a larger plugin ecosystem.

**Q: What is GitLab CI/CD?**  
**A:** GitLab CI/CD is an integrated CI/CD platform in GitLab, using `.gitlab-ci.yml` files to define pipelines with stages and jobs.

**Q: What is a pipeline stage?**  
**A:** A pipeline stage is a logical grouping of jobs that run in sequence (e.g., build, test, deploy). Stages ensure dependencies are met.

**Q: What is a pipeline job?**  
**A:** A pipeline job is a unit of work that executes a script or command. Jobs can run in parallel within a stage if there are no dependencies.

**Q: What is a runner in CI/CD?**  
**A:** A runner is a server that executes pipeline jobs. Runners can be hosted or self-hosted, providing the environment for job execution.

**Q: What is the difference between a hosted and self-hosted runner?**  
**A:** Hosted runners are managed by the CI/CD provider (e.g., GitHub Actions). Self-hosted runners are managed by you, offering more control and custom environments.

## Terraform

**Q: What is Terraform?**  
**A:** Terraform is an IaC tool for defining and provisioning infrastructure across multiple cloud providers using declarative configuration files.

**Q: What is a Terraform provider?**  
**A:** A Terraform provider is a plugin that interacts with a specific cloud provider (e.g., AWS, Azure, GCP) or service (e.g., Kubernetes, Docker).

**Q: What is a Terraform resource?**  
**A:** A Terraform resource defines a piece of infrastructure (e.g., AWS EC2 instance, Azure VM). Resources are defined in `.tf` files.

**Q: What is a Terraform module?**  
**A:** A Terraform module is a reusable collection of resources, organized for reuse. Modules can be local or remote (from the Terraform Registry or Git).

**Q: What is the difference between `terraform init`, `plan`, and `apply`?**  
**A:** `init` initializes the working directory and downloads providers. `plan` shows what changes will be made. `apply` applies the changes to infrastructure.

**Q: What is a Terraform state file?**  
**A:** The state file (`terraform.tfstate`) tracks the current state of infrastructure. It is used by Terraform to determine what changes to apply.

**Q: Where should you store the Terraform state file?**  
**A:** In a remote backend (e.g., S3, Azure Storage, Terraform Cloud) for collaboration, locking, and security. Avoid local storage for teams.

**Q: What is the difference between `terraform destroy` and `terraform apply -destroy`?**  
**A:** Both destroy infrastructure. `destroy` is a dedicated command. `apply -destroy` is a flag that forces destroy mode.

**Q: What is a Terraform output?**  
**A:** An output is a value that is displayed after `apply`, useful for passing data between modules or to other tools.

**Q: What is the difference between `terraform refresh` and `terraform plan`?**  
**A:** `refresh` updates the state file with actual infrastructure state. `plan` compares the desired state to the actual state and shows changes.

## Cloud Platforms

**Q: What is AWS?**  
**A:** AWS (Amazon Web Services) is a cloud platform offering compute, storage, database, networking, and many other services on a pay-as-you-use basis.

**Q: What is Azure?**  
**A:** Azure is Microsoft's cloud platform, offering services similar to AWS with integration with Microsoft products (e.g., Windows Server, Active Directory).

**Q: What is GCP?**  
**A:** GCP (Google Cloud Platform) is Google's cloud platform, known for its data and AI services (BigQuery, AI Platform, Kubernetes Engine).

**Q: What is the difference between EC2 and Lambda?**  
**A:** EC2 is a virtual machine service (IaaS). Lambda is a serverless compute service that runs code in response to events without managing servers.

**Q: What is the difference between S3 and EBS?**  
**A:** S3 is object storage for files (unstructured). EBS is block storage attached to EC2 instances (structured).

**Q: What is the difference between Azure Functions and AWS Lambda?**  
**A:** Both are serverless compute services. Azure Functions is on Azure, Lambda is on AWS. They have similar concepts (triggers, bindings).

**Q: What is the difference between Azure Blob Storage and Azure Disk Storage?**  
**A:** Blob Storage is object storage (like S3). Disk Storage is block storage attached to VMs (like EBS).

**Q: What is the difference between BigQuery and Redshift?**  
**A:** BigQuery is a serverless data warehouse on GCP. Redshift is a managed data warehouse on AWS. Both are for analytics.

## Monitoring & Logging

**Q: What is monitoring?**  
**A:** Monitoring is the process of collecting, analyzing, and displaying metrics about system performance and health.

**Q: What are common monitoring tools?**  
**A:** Prometheus, Grafana, Datadog, New Relic, ELK Stack (Elasticsearch, Logstash, Kibana), Splunk.

**Q: What is the difference between Prometheus and Grafana?**  
**A:** Prometheus collects and stores metrics. Grafana visualizes metrics on dashboards. They are often used together.

**Q: What is the difference between logging and monitoring?**  
**A:** Logging records events and messages (text). Monitoring collects numerical metrics (CPU, memory, latency). Both are needed for observability.

**Q: What is the ELK Stack?**  
**A:** ELK stands for Elasticsearch (search engine), Logstash (log processing), and Kibana (visualization). Used for logging and analytics.

**Q: What is a log aggregator?**  
**A:** A log aggregator collects logs from multiple sources, centralizes them, and provides search and analysis capabilities.

**Q: What is the difference between centralized logging and distributed tracing?**  
**A:** Centralized logging aggregates logs from all services. Distributed tracing tracks requests across services to identify bottlenecks.

## Security

**Q: What is the principle of least privilege?**  
**A:** The principle of least privilege grants only the minimum permissions necessary for a user or service to perform its function.

**Q: What is RBAC?**  
**A:** RBAC (Role-Based Access Control) assigns permissions based on roles. Users are assigned roles, and roles have permissions.

**Q: What is the difference between RBAC and ABAC?**  
**A:** RBAC is based on roles. ABAC (Attribute-Based Access Control) is based on attributes (user, resource, environment) for more fine-grained control.

**Q: What is a secret management tool?**  
**A:** A secret management tool securely stores and manages secrets (passwords, tokens, keys). Examples: HashiCorp Vault, AWS Secrets Manager, Azure Key Vault.

**Q: What is the difference between HashiCorp Vault and AWS Secrets Manager?**  
**A:** Vault is open-source and can be self-hosted or managed. AWS Secrets Manager is a managed service on AWS. Both provide secret storage and rotation.

**Q: What is the difference between encryption at rest and encryption in transit?**  
**A:** Encryption at rest protects data stored on disk. Encryption in transit protects data moving over the network (e.g., TLS/SSL).

**Q: What is a certificate authority (CA)?**  
**A:** A CA is an entity that issues digital certificates, which verify the identity of entities (e.g., websites, servers).

**Q: What is the difference between self-signed certificates and CA-signed certificates?**  
**A:** Self-signed certificates are not trusted by browsers by default. CA-signed certificates are trusted because the CA is in the browser's trust store.

## Configuration Management

**Q: What is configuration management?**  
**A:** Configuration management is the process of maintaining system configurations in a consistent and desired state, often using tools like Ansible, Chef, or Puppet.

**Q: What is Ansible?**  
**A:** Ansible is an open-source configuration management tool that uses YAML playbooks to automate tasks. It is agentless and uses SSH.

**Q: What is the difference between Ansible and Chef?**  
**A:** Ansible is agentless and uses push model. Chef uses agents (Chef clients) and pull model. Ansible uses YAML; Chef uses Ruby.

**Q: What is the difference between imperative and declarative configuration?**  
**A:** Imperative specifies how to achieve the desired state (scripts). Declarative specifies the desired state (Terraform, Kubernetes). Declarative is preferred for IaC.

**Q: What is the difference between configuration management and orchestration?**  
**A:** Configuration management ensures individual systems are in the desired state. Orchestration coordinates multiple systems to achieve a workflow.

## Git

**Q: What is Git?**  
**A:** Git is a distributed version control system for tracking changes in code, enabling collaboration and history management.

**Q: What is the difference between `git merge` and `git rebase`?**  
**A:** `merge` creates a merge commit combining histories. `rebase` rewrites history to apply commits linearly. Rebase keeps history cleaner but can be risky.

**Q: What is the difference between `git fetch` and `git pull`?**  
**A:** `fetch` downloads changes from remote without merging. `pull` fetches and merges (or rebases) changes into the current branch.

**Q: What is a Git branch?**  
**A:** A branch is an independent line of development. It allows parallel work without affecting the main branch.

**Q: What is the difference between a fast-forward merge and a three-way merge?**  
**A:** Fast-forward moves the branch pointer forward if the history is linear. Three-way merge creates a new commit when histories diverge.

**Q: What is the difference between `git stash` and `git commit`?**  
**A:** `stash` temporarily saves changes without committing. `commit` permanently saves changes to history.

**Q: What is the difference between `git reset` and `git revert`?**  
**A:** `reset` moves the branch pointer (rewrites history). `revert` creates a new commit that undoes changes (preserves history).

**Q: What is a Git remote?**  
**A:** A remote is a version of the repository hosted on a server (e.g., GitHub, GitLab). It enables collaboration.

**Q: What is the difference between `git clone` and `git init`?**  
**A:** `clone` copies an existing remote repository. `init` creates a new local repository.

**Q: What is the difference between `git checkout` and `git switch`?**  
**A:** `checkout` switches branches or restores files. `switch` is a newer command specifically for switching branches.

## CI/CD Best Practices

**Q: What are some CI/CD best practices?**  
**A:** Use pipelines as code, run tests on every commit, deploy frequently, use feature flags, monitor deployments, and automate rollbacks.

**Q: What is a feature flag?**  
**A:** A feature flag is a mechanism to enable or disable features without deploying code. It allows safe releases and A/B testing.

**Q: What is the difference between blue-green deployment and canary deployment?**  
**A:** Blue-green switches traffic between two identical environments. Canary releases to a subset of users first, then gradually rolls out.

**Q: What is a rolling update?**  
**A:** A rolling update gradually replaces old instances with new ones, ensuring zero downtime by updating a few instances at a time.

**Q: What is the difference between rolling update and blue-green deployment?**  
**A:** Rolling update gradually replaces instances in place. Blue-green switches to a new environment entirely. Both aim for zero downtime.

## DevOps Interview Questions

**Q: Describe a CI/CD pipeline you built.**  
**A:** Explain the stages (build, test, deploy), tools used (Jenkins, Docker, Kubernetes), challenges faced, and how you ensured reliability and speed.

**Q: How do you handle failed deployments?**  
**A:** Monitor alerts, investigate logs, rollback to previous version, fix the issue, and redeploy. Use automated rollbacks for fast recovery.

**Q: How do you ensure security in CI/CD?**  
**A:** Scan dependencies, use secret management, enforce least privilege, sign artifacts, and monitor for vulnerabilities.

**Q: How do you optimize CI/CD pipeline speed?**  
**A:** Cache dependencies, parallelize jobs, use incremental builds, optimize test execution, and use faster runners.

**Q: How do you manage infrastructure drift?**  
**A:** Use IaC (Terraform) to ensure desired state, schedule periodic reconciliation, and monitor for unauthorized changes.
