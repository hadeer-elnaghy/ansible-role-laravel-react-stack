# Laravel & React Stack Ansible Role

An Ansible role that automates the deployment of a full-stack environment with a Laravel API and a React frontend on Ubuntu or Red Hat/CentOS.

## Requirements
- Access to a server running Ubuntu or Red Hat/CentOS.
- Sudo privileges.

## Role Variables
Available variables are listed below, along with default values (see `defaults/main.yml`):

| Variable | Default | Description |
|----------|---------|-------------|
| `app_user` | `USER` | The system user for deployment |
| `app_name` | `my-test-app` | Name of the application |
| `base_path` | `/var/www/my-test-app` | Path to the project root |
| `enable_ssl` | `false` | Whether to enable Let's Encrypt SSL |

## Dependencies
- geerlingguy.nginx
- geerlingguy.php
- geerlingguy.mysql

## Example Playbook
```yaml
- hosts: webservers
  roles:
     - { role: hadeer-elnaghy.laravel-react-stack }