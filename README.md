# PROJECT ASSESSMENT

# Agenda:

Building an entirely new platform on AWS, including infrastructure, internal developer platform (IdP/Software Factory), and associated principles and processes. The platform will serve as the foundation for highly available, scalable, and secure application delivery and deployment. Components are developed as microservices to be deployed within Kubernetes clusters.


# 1) Functional & Non-Functional Requirements
# Business (Functional) Requirements
•	User-facing applications: Serve multiple business applications as microservices (HTTP/gRPC APIs, background workers, event processors).
•	Developer workflows: Self-service developer platform: git-based, automated CI/CD.
•	Multi-tenancy (logical): Support multiple teams/environments (dev/test/prod) with isolation.
•	Observability & troubleshooting: Centralized logs, metrics, traces; easy drill-down from alert to pod and code.
•	Security & Compliance: Encryption at rest/in transit, fine-grained access controls, audit logs for compliance.
# Technical (Non-functional) Requirements
•	Availability: 99.95%+ for platform control plane and critical services; application RTO/RPO defined per app (example RTO ≤ 15min for critical).
•	Scalability: Elastic scaling for request spikes; horizontal scaling of microservices.
•	Performance: SLOs per service (e.g., p95 latency < 300ms).
•	Cost efficiency: Use mix of on-demand, spot, Fargate to balance cost and reliability.
•	Security: Zero-trust networking within VPCs, IAM least privilege, secrets management.

# 2) Architecture Principles & Patterns
# Design Principles
•	AWS Well-Architected: Embrace Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization.
•	Infrastructure as Code: Terraform / AWS CDK for infra; Helm + Kustomize for K8s.
•	GitOps: ArgoCD / Flux for continuous delivery of K8s manifests.
•	Immutable infrastructure: Build artifacts (containers, AMIs) and deploy without in-place edits.
•	Least privilege & defense-in-depth: IAM roles, network segmentation, WAF, GuardDuty, etc.
•	Policy-as-Code: OPA/Gatekeeper for K8s admission policies; tfsec/Checkov for IaC scanning.

