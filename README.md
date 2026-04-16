# Linux Auto Patching Framework

This repository contains Ansible playbooks used to automate patching and basic system management across Linux servers.

## Overview

The purpose of this project is to provide a consistent and repeatable method of applying system updates across infrastructure.

It is designed to integrate with automation platforms such as AWX or Semaphore, using Git as the source of truth for playbooks and configuration.

## Key Features

- Automated patching using Ansible
- Git-driven workflow for version control and change tracking
- Integration with AWX for scheduling and execution
- Support for controlled patch windows via inventory grouping

## Repository Structure

.
├── playbooks/
│ ├── patch-linux.yml
│ ├── patch-dryrun.yml
│ ├── sshkey.yml
│ └── test-ssh.yml

## Playbooks

- **patch-linux.yml**  
  Performs system updates and applies patches to target hosts.

- **patch-dryrun.yml**  
  Simulates patching to identify pending updates without applying them.

- **sshkey.yml**  
  Manages SSH key deployment for access and automation.

- **test-ssh.yml**  
  Validates SSH connectivity to target hosts.

This repository is intended to be consumed by AWX.

Typical workflow:
1. AWX syncs this repository from GitHub
2. A Job Template selects the required playbook
3. Inventory groups define which hosts are targeted (e.g. `patch_monday`)
4. Jobs are executed manually or via scheduled patch windows

## Notes

- Always test playbooks in a non-production environment before rollout
- Ensure maintenance windows are aligned with patch schedules
- Monitor systems during and after patching
