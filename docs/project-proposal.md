# CCDC HIVE Project Proposal

CCDC HIVE (Hosted Infrastructure for Virtual Exercises) is a proposed platform for deploying reusable cybersecurity practice environments for Cedarville University's Collegiate Cyber Defense Competition (CCDC) team.

Rather than maintaining a single practice environment that attempts to replicate the annual competition network, HIVE enables the rapid deployment of targeted practice scenarios that develop specific defensive skills. The system emphasizes automation, repeatability, and modular design so that future teams can continue expanding the available training scenarios with minimal overhead.

## Problem Statement

Preparing for CCDC currently requires significant manual effort to build and maintain practice environments. These environments are difficult to modify, difficult to reproduce, and eventually become outdated as the competition evolves.

Additionally, maintaining one large practice environment limits the team's ability to focus on specific skills, including:

- Firewall configuration  
- Network troubleshooting  
- Malware and beacon detection  
- Incident response  
- Service recovery

A modular cyber range would allow the team to practice these skills individually while still supporting full-scale competition simulations.

## Proposed Solution

CCDC HIVE will provide an automated system for deploying cyber ranges using Proxmox, Ludus, and Ansible. The platform will run on Cedarville's existing cyber range infrastructure and use reusable virtual machine templates and configuration scripts to create complete practice environments on demand. Each practice scenario will consist of reusable infrastructure components that can be combined to build increasingly complex exercises. This approach allows scenarios to be maintained and expanded independently while reducing duplicated effort.

## Project Scope

The project is divided into four primary phases. Phase 1 is currently being completed during Summer 2026\. The proposed Senior Design project would focus primarily on Phases 2 and 3\.

### Phase 1 — Proof of Concept

**Objective:**

Demonstrate that a Ludus-based cyber range can reproduce the team's existing practice environment.

**Major Tasks:**

- Deploy a Proxmox \+ Ludus instance within Cedarville's cyber range.  
- Recreate the current CCDC practice range.  
- Validate deployment and rollback workflows.  
- Evaluate system performance and resource requirements.

**Deliverable:**

A working proof-of-concept capable of reproducing the existing practice environment through automated deployment.

### Phase 2 — Scenario Development

**Objective:**

Develop a library of reusable cyber range components and practice scenarios.

**Major Tasks:**

- Build reusable virtual machine templates.  
- Develop modular network configurations.  
- Create role-specific and full-team training scenarios.  
- Implement infrastructure configuration using Ansible.  
- Document all templates and scenarios for future maintenance.  
- Investigate a reusable scoring mechanism capable of validating services across multiple scenarios.

Example scenarios include:

- Firewall configuration  
- Incident response  
- Malware and beacon hunting  
- Service recovery  
- Active Directory administration

**Deliverable:**

A documented collection of reusable practice scenarios that can be deployed automatically.

### Phase 3 — User Interface and Automation

**Objective:**

Improve the usability of the platform by simplifying deployment and management.

**Major Tasks:**

- Design a web-based administrative interface.  
- Allow users to browse available practice scenarios.  
- Configure optional scenario modifiers.  
- Deploy and destroy practice environments through a simplified interface.  
- Investigate methods for providing users with direct access to deployed virtual machines without requiring interaction with the underlying Proxmox interface.

The long-term vision is for a team member to log in, select a scenario, deploy it, complete the exercise, and reset or remove the environment with minimal administrative effort.

**Deliverable:**

A user-friendly interface for deploying and managing cyber range exercises.

### Phase 4 — Intelligent Adversary (Stretch Goal)

**Objective:**

Investigate the feasibility of incorporating AI-assisted offensive behavior into practice scenarios.

Potential work includes researching AI systems capable of planning or executing realistic attacker behavior, allowing practice environments to evolve dynamically rather than relying solely on scripted attacks.

Because this area is exploratory, implementation details and project scope would be determined through initial research.

**Deliverable:**

A research prototype or proof of concept demonstrating AI-assisted red team capabilities.

## Expected Outcome

Upon completion, CCDC HIVE will provide Cedarville University's CCDC team with a reusable, extensible cyber range platform capable of supporting both individual training and full-team competition preparation. The project will reduce the effort required to create and maintain practice environments while providing future teams with a foundation that can evolve alongside the competition.