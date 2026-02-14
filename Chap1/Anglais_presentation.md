# Internal Developer Platform (IDP) & Platform Engineering

## Table of Contents

- [Central Research Question](#central-research-question)
- [Research Question 1 – Concepts, Principles and Patterns of Platform Engineering](#research-question-1--concepts-principles-and-patterns-of-platform-engineering)
- [Research Question 2 – Developer Experience: Definition, Factors & Metrics](#research-question-2--developer-experience-definition-factors--metrics)
- [Research Question 3 – Challenges & Deficits in the Status Quo](#research-question-3--challenges--deficits-in-the-status-quo)
- [Research Question 4 – Goal Conflicts between Standardization, Security, Compliance & Flexibility](#research-question-4--goal-conflicts-between-standardization-security-compliance--flexibility)
- [Research Question 5 – Conceptual & Architectural Target Picture of an IDP](#research-question-5--conceptual--architectural-target-picture-of-an-idp)

---

## Central Research Question

**How can modern platform engineering approaches contribute to the design of an Internal Developer Platform (IDP) that improves the developer experience while reconciling standardization, security and compliance with the necessary flexibility for heterogeneous development teams?**

### Slide 1 – Answer to the Central Research Question (Overview)

#### Platform as a Product

- Dedicated platform team that understands developers as customers  
- Continuous collection of feedback and measurement of developer experience

#### Self-Service and Automation

- Standardized, automated provisioning of infrastructure, CI/CD, environments  
- Reduction of manual tickets and waiting times

#### Golden Paths & Templates

- Predefined, secure standard paths for typical applications  
- High standardization and security without completely prohibiting free choice

#### Built-in Security & Compliance (Shift Left)

- Policy as code, security scans, audit logging integrated directly into pipelines  
- Developers do not have to organize compliance manually – it is provided via the platform

#### Clear Architecture with Guardrails

- Uniform base services (logging, monitoring, auth), extensible via APIs  
- Teams can add their own technologies within safe guardrails

**Key Message**  
Modern platform engineering approaches enable an IDP that significantly improves developer experience by hiding complexity, standardizing security and providing controlled flexibility through guardrails instead of hard prohibitions.

---

## Research Question 1 – Concepts, Principles and Patterns of Platform Engineering

**Question:**  
Which concepts, principles and architectural patterns of platform engineering are described in the scientific literature and in industrial best practices for the design of internal developer platforms?

### Slide 2 – Central Concepts & Principles

#### Platform as a Product

- Platform team with product responsibility, roadmap and KPIs  
- Focus on users: developers are the primary target group

#### Self-Service & Automation

- Self-service portal or API for:
  - Project/repo creation  
  - CI/CD setups  
  - Environments & databases
- High degree of automation with infrastructure as code & GitOps

#### Golden Paths & Standard Blueprints

- Predefined, tested standard paths, e.g.:
  - “Standard web service”
  - “Event-based service”
  - “Data pipeline”
- Include:
  - Build, test and deploy templates  
  - Security scans, logging, monitoring “out of the box”

#### You-Build-It-You-Run-It Support

- IDP provides all building blocks so that teams can operate their services themselves  
- Observability, alerting, runbooks as standard

### Slide 3 – Architectural Patterns & Best Practices

#### Typical Architectural Patterns

- Multi-layer architecture:
  - Infrastructure layer (cloud, Kubernetes, network)  
  - Platform layer (CI/CD, observability, security, service catalog)  
  - Application layer (line-of-business services)
- API-first & plugin-capable developer portal

#### Best Practices from Industry

- Dedicated platform team that co-creates with dev teams  
- Policy as code for security & compliance (e.g. OPA, Kyverno)  
- Standardized repository structure & templates  
  - e.g. via Cookiecutter, Backstage templates
- Tight integration of:
  - CI/CD  
  - Container orchestration (e.g. Kubernetes)  
  - Observability (e.g. Prometheus, Grafana, OpenTelemetry)

**Short Answer RQ1**  
Modern platform engineering approaches describe product-oriented, self-service-capable platforms that work with golden paths, a high degree of automation and a clear layered architecture in order to design IDPs that are user-centric, secure and efficient.

---

## Research Question 2 – Developer Experience: Definition, Factors & Metrics

**Question:**  
How is developer experience defined in the context of modern software development, and which factors and metrics are suitable for its evaluation within an internal developer platform?

### Slide 4 – Definition & Factors of Developer Experience

#### Definition of Developer Experience (DX)

Developer experience is the totality of experiences that developers have with tools, processes, platforms and the organization in order to develop, test, deploy and operate software throughout its entire lifecycle.

#### Essential Factors in an IDP

- **Simplicity & Usability**
  - Clear, understandable service catalog  
  - Good UX in the portal, clean CLI/API interfaces

- **Productivity & Flow**
  - Fast builds, short feedback loops, automated tests  
  - Few context switches between tools

- **Autonomy**
  - Self-service for environments, deployments, secrets, databases

- **Transparency**
  - Easy insight into logs, metrics, pipelines, costs

- **Support**
  - Good documentation, examples, support channels, training

### Slide 5 – Metrics for Evaluating DX in an IDP

#### Quantitative Metrics

- DORA metrics:
  - Deployment frequency  
  - Lead time for changes  
  - Change failure rate  
  - Mean time to recovery (MTTR)
- Platform-specific metrics:
  - Time to first successful deployment on the IDP  
  - Duration of typical workflows (e.g. new project → production operation)  
  - Share of services using golden paths/templates  
  - Number of manual steps in deployments vs. automated steps

#### Qualitative Metrics

- Regular DX surveys (e.g. quarterly)  
- Developer Net Promoter Score (DevNPS)  
- Surveys on perceived:
  - Complexity of the platform  
  - Autonomy  
  - Satisfaction with documentation & support

**Short Answer RQ2**  
DX in the context of an IDP describes how efficiently, pleasantly and autonomously developers can work with the platform. It is shaped by factors such as usability, flow, autonomy and transparency and can be measured using DORA metrics, platform KPIs and regular developer surveys.

---

## Research Question 3 – Challenges & Deficits in the Status Quo

**Question:**  
Which challenges and deficits exist in the current status quo of development and delivery processes with regard to developer experience?

### Slide 6 – Technical & Process Challenges

#### Tool Sprawl & Heterogeneity

- Different CI/CD tools, monitoring solutions, deployment procedures  
- No uniform standards, every application “works differently”

#### Manual Processes & Tickets

- Environments and resources are requested from Ops via tickets  
- Long waiting times, media breaks, high error potential

#### Lack of Automation

- Many manual steps in build, test and deployment processes  
- High cognitive load, as developers must know infrastructure details

#### Low Transparency

- Unclear view of deployments, logs, metrics  
- Difficult troubleshooting, especially in production environments

### Slide 7 – Impact on Developer Experience

#### Long Time-to-First-Value

- Onboarding new developers or projects takes weeks instead of days

#### Frustration & Context Switching

Developers constantly have to deal with non-value-adding tasks:

- Tracking tickets  
- Manual configuration work  
- Coordination across multiple teams

#### Unreliability & Uncertainty

- Different quality of pipelines and deployments  
- Uncertainty as to whether security and compliance requirements are actually being met

#### Organizational Deficits

- Platform or tooling is seen as a “by-product”, no clear ownership  
- No clear channel to make DX problems visible and prioritize them

**Short Answer RQ3**  
The current status quo is often characterized by tool sprawl, manual processes, lack of automation and low transparency. This leads to slow onboarding, frustration, high cognitive load and uncertain compliance with standards, which significantly deteriorates developer experience.

---

## Research Question 4 – Goal Conflicts between Standardization, Security, Compliance & Flexibility

**Question:**  
Which goal conflicts exist between standardization, security and compliance requirements and the necessary flexibility for different development teams?

### Slide 8 – Concrete Goal Conflicts

#### Standardization vs. Flexibility

- Standardized pipelines, technologies and architectures  
  ↔ Need of teams to try out new technologies and patterns

#### Security & Compliance vs. Speed

- Strict reviews, manual approvals, documentation obligations  
  ↔ Desire for fast, frequent releases

#### Central Control vs. Team Autonomy

- Central governance and policies  
  ↔ Self-determined choice of tools and deployment strategies

#### Efficiency/Costs vs. Technological Diversity

- Concentration on a few, well-supported platform services  
  ↔ “Best-of-breed” approaches by individual teams

### Slide 9 – How These Goal Conflicts Can Be Addressed

#### Guardrails Instead of Gates

- Predefined guardrails:
  - Security policies  
  - Standard Terraform modules  
  - Approved container images
- Automated checks in CI/CD instead of manual approvals

#### Tiered Models for Freedoms

- Standard path (golden path) with maximum support  
- “Escape hatches”: controlled exceptions with clear conditions

#### Risk-Based Governance

- Stricter controls for critical systems  
- Lighter, automated controls for less critical applications

#### Transparent Catalogs & Approvals

- List of approved technologies & patterns (tech radar)  
- Clearly defined process for integrating new technologies via the IDP

**Short Answer RQ4**  
The essential goal conflicts lie between standardization/security and flexibility/speed. These can be resolved in such a way that both security and innovation remain possible by using guardrails, automated policies, risk-based governance and clearly defined degrees of freedom.

---

## Research Question 5 – Conceptual & Architectural Target Picture of an IDP

**Question:**  
How can a conceptual and architectural target picture of an internal developer platform be designed that meets these requirements?

### Slide 10 – Conceptual Target Picture

#### Objectives of the IDP

- End-to-end support of the software lifecycle:  
  Ideation → development → testing → deployment → operations
- Significant improvement of DX while simultaneously adhering to standards

#### Central Design Principles

- Platform as a product with a dedicated platform team  
- Self-service for all recurring tasks:
  - Repositories  
  - Environments  
  - Pipelines  
  - Databases  
  - Secrets
- “Secure by default” and “compliance by design”  
- Modular, extensible, API-first

#### Core Functions

- Developer portal (service catalog, golden paths, documentation)  
- Unified CI/CD pipelines  
- Observability platform (logging, metrics, tracing)  
- Security services (IAM, secrets management, scans, policies)  
- Cost transparency (FinOps features)

### Slide 11 – Architectural Target Picture (High Level)

#### Experience Layer

- Developer portal as central entry point  
- Self-service catalog for:
  - New services  
  - Databases  
  - Environments  
  - Pipelines

#### Platform Services Layer

- Standardized CI/CD engine with integrated quality and security gates  
- Service registry, API gateway, optionally service mesh  
- Observability stack, central logging and monitoring service  
- Policy-as-code engine for security and compliance rules

#### Infrastructure Layer

- Cloud/Kubernetes infrastructure as standardized base  
- Infrastructure as code for all resources

#### Operating Model

- Platform team with roadmap, SLAs and DX metrics  
- Regular feedback loops with development teams  
- Continuous further development of golden paths & templates

**Short Answer RQ5**  
A suitable target picture of an IDP consists of a developer portal (experience layer), a set of standardized platform services (CI/CD, observability, security, service catalog) and an automatically managed infrastructure layer. It is supported by a platform team that operates the platform as a product, measures DX and continuously improves it.
