# Home Infrastructure Ansible Repository

This repository contains Ansible playbooks and configurations for managing my home infrastructure. It includes setup and maintenance scripts for various services running on my home server.

## Getting Started

Enable the environment using `uv`. Get uv from [uv](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer).

```bash
# Create virtual environment
uv venv

# Activate the environment
source .venv/bin/activate

# Install dependencies
uv pip install -r requirements.txt
```

## Playbooks

### Individual Playbooks
- `playbooks/vpn-setup.yml` - Configure OpenVPN auto-start on boot
- `playbooks/docker-setup.yml` - Install Docker and dependencies
- `playbooks/salon-deploy.yml` - Deploy Salon Landing Page container

### Main Playbook
- `playbooks/main.yml` - Runs all setup tasks in sequence

## Usage

```bash
# Test connectivity
ansible all -m ping

# Run individual playbooks
ansible-playbook playbooks/vpn-setup.yml
ansible-playbook playbooks/docker-setup.yml
ansible-playbook playbooks/salon-deploy.yml

# Run everything
ansible-playbook playbooks/main.yml

# Dry run (check what would change)
ansible-playbook playbooks/main.yml --check
```

## Services

- **VPN**: Auto-connects on boot using systemd service
- **Salon Landing Page**: Runs on port 80, accessible at http://10.8.0.250