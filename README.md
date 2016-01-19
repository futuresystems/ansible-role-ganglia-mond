# Description

This role deploys the Ganglia `mond` daemon.

# Platforms supported

- Ubuntu 14.04
- EL7

# Variables

See [defaults/main.yml](https://github.com/futuresystems/ansible-role-ganglia-mond/blob/master/defaults/main.yml)

# Example

The following deploys `gmond` to all nodes and directs them to
communicate with the first node in the `monitor` group.

```yaml
- name: ganglia nodes
  hosts: all
  sudo: yes
  roles:
  - role: ganglia_mond
    ganglia_udp_send_channels:
      - host: "{{ hostvars[groups['monitor'][0]].ansible_eth0.ipv4.address }}"
        port: "{{ ganglia_defaults_gmon_port }}"
```
