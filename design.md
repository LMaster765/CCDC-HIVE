# HIVE Design

## Mission
Provide one-command deployment of repeatable CCDC practice environments.

## Goals
- Automated deployment
- Automated teardown
- Version-controlled scenarios
- Instructor dashboard
- AI adversary

## Architecture

At a very high level, HIVE's architecture looks like the following:

```
Infrastructure Host:
│   Proxmox + Ludus
│
├── Management VM:
│   ├── Git/Documentation
│   ├── Scenario Orchestration
│   └── Web-App Dashboard
│
├── Attacker VM:
│   ├── Adversary Emulation Tooling
│   └── AI-Assisted Adversary Logic (stretch goal)
│
└── Scenario VMs:
    ├── Domain Controller (AD)
    ├── Windows Servers
    ├── Linux Servers
    └── Routers & Firewalls
```

### Host

At its core, HIVE is a Proxmox server configured with Ludus. To improve maintainability, the system has been designed to keep as much functionality off of the host server as possible. This should also make it easier to take a vanilla Proxmox/Ludus server and set up HIVE.

### Management VM

The bulk of the interaction with the HIVE system will be done through the management VM to remove the management logic from the host system. All scenario orchestration will be performed from this machine.

### Templates

HIVE templates are the reusable base images used to rapidly create scenario components. Templates are versioned and rebuilt as needed so that scenarios remain consistent across deployments.

### Scenario Library

The Scenario Library contains reusable lab definitions that can be deployed independently or composed into larger environments. Each scenario defines topology, services, credentials, objectives, and difficulty level. Scenario VMs are deployed into isolated environments by default, with connectivity defined per scenario as needed. Scenario definitions are stored in version control and can be redeployed repeatedly from the same source.

## Roadmap

### MVP

Install the host stack, deploy one basic scenario, verify reset/destroy works, and document the process.

### Phase 2

Add templates and a small scenario library.

### Phase 3

Add the dashboard and scoring.

### Future Research

Add AI-assisted adversary planning and scenario generation.