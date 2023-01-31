# IPv6 for IPv4-only Services

[![Molecule Tests](https://github.com/blackieops/ansible-role-sixfour/actions/workflows/test.yml/badge.svg)](https://github.com/blackieops/ansible-role-sixfour/actions/workflows/test.yml)

This is an [Ansible][ansible] role for configuring `socat` tunnels as systemd
services to proxy IPv6 traffic to services that can only listen on IPv4. This
allows you to provide IPv6 connections to your clients, even if what you're
running doesn't understand IPv6 (such as a single-stack Kubernetes cluster).

[ansible]: https://ansible.com

## Required variables

| **Name** | **Type** | **Description**
| -------- | -------- | ---------------
| `sixfour_ports` | `array(string)` | A list of ports for which to start proxies.

## Usage

Install the role by adding either the Ansible Galaxy package or Git remote to
your `requirements.yml`:

```yaml
# via Galaxy
- src: blackieops.sixfour

# or via Git
- src: https://github.com/blackieops/ansible-role-sixfour.git
```

Then install it with `ansible-galaxy`:

```
$ ansible-galaxy install -r requirements.yml
```

Finally, you can reference the role in your playbooks:

```yaml
- hosts: all
  roles:
    - { role: blackieops.sixfour }
```
