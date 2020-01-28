# ansible-consul-template

[![contributing][contributing-img]](CONTRIBUTING.md)

1. [Overview](#overview)
1. [Description](#description)
1. [Requirements](#requirements)
1. [Setup](#setup)
1. [Role Variables](#role-variables)
1. [Playbook Example](#playbook-example)
1. [Dependencies](#dependencies)
1. [Limitations](#limitations)
1. [Development](#development)

## Overview

[consul-template](https://github.com/hashicorp/consul-template)
The daemon consul-template queries a Consul or Vault cluster and updates any number of specified templates on the file system.

## Description

This role deploy and configure [consul-template](https://github.com/hashicorp/consul-template).

## Requirements

None

## Setup

Use `ansible-galaxy` or download the role in your `roles` directory.

## Role Variables

Sane consul-template defaults are set in the variables,
see [defaults/main.yml/consul_template_configurations](./defaults/main.yml)

Consul server address and consul-template configuration can be overrided with:
```yaml
consul_template_server: "1.2.3.4:8500"

consul_template_configuration:
  auth:
    enabled: false
    username:
    password:
  server: "{{ consul_template_server | default("127.0.0.1:8500") }}"
  retry:
    enabled: true
    attempts: 12
    backoff: "250ms"
    max_backoff: "1m"
  ssl:
    enabled: false
    verify: false
    cert:
    key:
    ca_cert:
    ca_path:
    sni:
  log:
    level: "warn"
    syslog:
      enabled: true
      facility: "LOCAL5"
  dedup:
    enabled: true
    prefix: "consul-template/dedup/"
```

## Playbook Example

Use default configuration, means that nothing will be done.

```yaml
- hosts: localhost
  roles:
    - ansible-consul-template
```

## Dependencies

None

## Limitations

So far, this is compatible with Debian and derivatives.

## Development

Please read carefully CONTRIBUTING.md before making a merge request.

[contributing-img]: https://img.shields.io/badge/contributing--grey.svg
