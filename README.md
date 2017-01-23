# Ansible Role: Certbot / Let's Encrypt

Installs Certbot (Let's Encrypt) for RHEL/CentOS with Nginx.

Also configures root crontab entries for auto-renew.

## Requirements

* Certbot requires Git be installed

## Role Configuration

* Email address to register domains with:

        certbot_email: admin@example.com

* List of domains to create individual certificates for:

        certbot_domains: 
          - stage.example.com
          - stage.awesome.com

## Dependencies

* In order for certbot to verify domain control, public DNS for each domain must be setup prior to running and an nginx server must exist for each domain

## Example Usage

    - { role: certbot, certbot_email: admin@example.com, certbot_domains: [ stage.example.com ] }
