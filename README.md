# Ansible Role: Certbot (Let's Encrypt)

[![Build Status](https://travis-ci.com/davidalger/ansible-role-certbot.svg?branch=master)](https://travis-ci.com/davidalger/ansible-role-certbot)

Installs Certbot (Let's Encrypt) for RHEL/CentOS with Nginx and configures root crontab entry for auto-renew.

## Requirements

Certbot requires `git` be installed on the target servers.

## Role Variables

    certbot_generate: false

False by default, set `certbot_generate: true` for certbot to attempt generation of SSL certificates (requires public DNS hence default value of false)

    certbot_email: admin@example.com

Email address to register domains with.

    certbot_domains: 
      - stage.example.com
      - stage.awesome.com

List of domains to create individual certificates for.

## Dependencies

In order for certbot to verify domain control, public DNS for each domain must be setup prior to running and an nginx server must exist for each domain.

## Example Playbook

    - hosts: web-servers
      vars:
        certbot_generate: true
        certbot_email: admin@example.com
        certbot_domains:
          - example.com
          - stage.example.com
      
      roles:
        - { role: davidalger.certbot, tags: certbot }

## License

This work is licensed under the MIT license. See LICENSE file for details.

## Author Information

This role was created in 2017 by [David Alger](http://davidalger.com/).
