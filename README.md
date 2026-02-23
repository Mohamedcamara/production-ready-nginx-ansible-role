Production-Ready Nginx Ansible Role (Multi-Distro)
Overview
This project provides a production-grade Ansible role to deploy Nginx on:
 1. Ubuntu (Debian family)
 2. AlmaLinux (RHEL family)

It demonstrates cross-distribution automation, OS-aware configuration, and safe service orchestration.
Engineering Highlights
- Dynamic OS detection using ansible_os_family
- Separate configuration paths for Debian and RHEL
- Never overrides /etc/nginx/nginx.conf on RHEL systems
- Server blocks deployed to /etc/nginx/conf.d/
- Root directory dynamically assigned
- SELinux context handling
- Configuration validation using nginx -t
- Idempotent execution
- Handler-driven restart logic

Why This Matters
Many automation examples ignore distribution differences.

This role explicitly handles:
- Packaging differences
- Configuration architecture differences
- Service management differences
- Validation before restart
- It reflects real-world production constraints.

Project Structure
production-ready-nginx-ansible-role/
├── inventories
│   └── lab.yml
├── README.md
├── roles
│   └── webserver-role
│       ├── defaults
│       │   └── main.yml
│       ├── files
│       ├── handlers
│       │   └── main.yml
│       ├── meta
│       │   └── main.yml
│       ├── README.md
│       ├── tasks
│       │   └── main.yml
│       ├── templates
│       │   ├── index.html.j2
│       │   └── nginx.conf.j2
│       ├── tests
│       │   ├── inventory
│       │   └── test.yml
│       └── vars
│           └── main.yml
└── sites.yml

12 directories, 13 files

-----------------
How to Run
ansible-playbook -i inventories/lab.yml site.yml
Tested On
 1. Ubuntu 22.04
 2. AlmaLinux 9

-----------------------
ansible.cfg
[defaults]
inventory = inventories/lab.yml
roles_path = roles
host_key_checking = False
retry_files_enabled = False
Key Lessons Learned

-------------------------
DevOps is not about writing YAML.
It is about automating systems you deeply understand.
