# Home Infrastructure Ansible Repository

This repository contains Ansible playbooks and configurations for managing my home infrastructure. It includes setup and maintenance scripts for various services running on my home server.

## Preparing Resources

Setup configuration files:

1. Copy `ansible-template.cfg` to `ansible.cfg` and update with your settings:
   - `remote_user`: Your SSH username
   - `private_key_file`: Path to your SSH private key

2. Copy `inventory-template.ini` to `inventory.ini` and modify with your target hosts

3. Additional resource files required for the playbooks should be placed in the `resources/` directory. Refer to `resources/README.md` for details on necessary files.

## Installation

You can install ansible directly or use a virtual environment. Both will work just fine.

### Using system package manager

Install ansible using your system's package manager:

```bash
sudo apt-get install ansible
```

### Using virtual environment

Enable the environment using `uv`. Get uv from [uv](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer).

```bash
# Create virtual environment
uv venv

# Activate the environment
source .venv/bin/activate

# Install dependencies
uv pip install -r requirements.txt
```

Do not forget to update the virtual environment dependencies when additional packages are downloaded:

```bash
uv pip freeze > requirements.txt
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

# Main setup
ansible-playbook playbooks/core-setup.yml

# Dry run (check what would change)
ansible-playbook playbooks/core-setup.yml --check
```

## Services

- **VPN**: Auto-connects on boot using systemd service
- **Docker**: Manages containers for various services
