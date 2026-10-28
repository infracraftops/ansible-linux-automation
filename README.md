# ansible-linux-automation

Production-ready Ansible roles for automating Linux server configuration — includes baseline hardening, user management, NTP, firewall, and web server setup. Targeting RHEL/Rocky Linux 8/9.

## Roles

| Role | Description |
|------|-------------|
| `baseline` | OS hardening, sysctl tuning, SSH configuration |
| `users` | User creation, sudo access, SSH key management |
| `ntp` | Chrony NTP configuration |
| `firewall` | firewalld zones and rules |
| `webserver` | Apache installation and virtual host configuration |
| `security` | auditd, fail2ban, login banner |

## Requirements

- Ansible 2.12+
- Target OS: RHEL / Rocky Linux 8 or 9
- SSH access with sudo privileges

## Usage

### 1. Clone the repo

```bash
git clone https://github.com/infracraftops/ansible-linux-automation.git
cd ansible-linux-automation
```

### 2. Set up your inventory

```bash
cp inventory/hosts.ini.example inventory/hosts.ini
# Edit hosts.ini with your target server IPs
```

### 3. Review group variables

Edit `group_vars/all.yml` to set:
- NTP servers
- Admin users and SSH keys
- Firewall ports
- Web server virtual host settings

### 4. Run the full site playbook

```bash
ansible-playbook -i inventory/hosts.ini site.yml
```

### 5. Run individual roles

```bash
# Baseline hardening only
ansible-playbook -i inventory/hosts.ini site.yml --tags baseline

# Web server only
ansible-playbook -i inventory/hosts.ini site.yml --tags webserver
```

## Role Variables

Each role has a `defaults/main.yml` with documented variables you can override in `group_vars/all.yml` or at the host level.

## Directory Structure

```
ansible-linux-automation/
├── README.md
├── site.yml
├── inventory/
│   └── hosts.ini.example
├── group_vars/
│   └── all.yml
└── roles/
    ├── baseline/
    ├── users/
    ├── ntp/
    ├── firewall/
    ├── webserver/
    └── security/
```

## Author

[infracraftops](https://github.com/infracraftops)
