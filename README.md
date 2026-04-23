# Laravel & React Stack Ansible Role

An Ansible role that automates the deployment of a full-stack environment with a Laravel API and a React frontend on Ubuntu or Red Hat/CentOS.

## Requirements
- Access to a server running Ubuntu or Red Hat/CentOS.
- Sudo privileges.

## Features
- *Automated Web Server:* Configures Nginx with optimized routing for SPA frontends and PHP APIs.
- *PHP-FPM Integration:* Dynamic socket handling for Ubuntu and Red Hat.
- *Security:* Optional Let's Encrypt SSL integration and automated crypto-policy adjustments.
- *Ready for Production:* Sets up dedicated app users and clean directory structures.

## Role Variables
Available variables are listed below, along with default values (see `defaults/main.yml`):

| Variable | Default | Description |
|----------|---------|-------------|
| app_user | user | System user that will own the application files. |
| app_name | my-test-app | The name of your project (used for directory naming and Nginx configs). |
| base_path | /var/www/{{ app_name }} | The root directory where your project will be deployed. |
| php_version | 8.3 | The version of PHP to be used (e.g., 8.2, 8.3). |
| api_path | /api | The URL prefix that Nginx will route to the Laravel backend. |
| frontend_dist_folder | dist | The name of your React build folder (standard for Vite). |
| enable_ssl | false | Set to true to trigger Certbot SSL certificate generation. |
| domain_name | yourdomain.com | Your live domain name required for Nginx and SSL. |
| ssl_email | user@example.com | Email address for Let's Encrypt renewal notifications. |

## Dependencies
- geerlingguy.nginx
- geerlingguy.php
- geerlingguy.mysql

## Example Playbook
```yaml
- hosts: webservers
  roles:
     - { role: hadeer-elnaghy.laravel-react-stack }