# Playbooks

This directory contains Ansible playbooks for automating home server setup and deployment tasks.

## Structure

### Main Playbooks

- `core-setup.yml` - Main orchestration playbook that runs all infrastructure setup tasks

### Infrastructure (`infrastructure/`)

Core system setup and configuration playbooks:

- `docker-setup.yml` - Install Docker and configure container environment
- `vpn-setup.yml` - Configure OpenVPN auto-start service

### Applications (`applications/`)

Application deployment playbooks (currently empty - add service-specific deployments here)

## Usage

```bash
# Run complete infrastructure setup
ansible-playbook core-setup.yml

# Run individual infrastructure components
ansible-playbook infrastructure/docker-setup.yml
ansible-playbook infrastructure/vpn-setup.yml

# Dry run to check changes
ansible-playbook core-setup.yml --check
```

## Security Note

Some services may be excluded from automation for security reasons. Manual configuration may be required for sensitive components.
