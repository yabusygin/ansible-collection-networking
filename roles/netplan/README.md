Ansible Role - yabusygin.networking.netplan
===========================================

The role configures networking with [Netplan][Home].

[Home]: https://netplan.io/

Requirements
------------

None.

Role Variables
--------------

The `netplan_config` specifies path to Netplan configuration file template
(Jinja). The variable is mandatory.

Netplan configuration files that are not managed by this role are removed by
defualt. To suppress this behaviour set the `netplan_remove_unmanaged_configs`
value to `false`.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
---
- name: Example playbook
  hosts: server
  tasks:
    - name: Configure networking
      ansible.builtin.import_role:
        name: yabusygin.networking.netplan
      vars:
        netplan_config: netplan.yml.jinja
        server_address: 192.168.0.10
        server_prefixlen: 24
        server_gateway: 192.168.0.1
        server_nameservers:
          - 192.168.0.1
          - 10.10.10.10
```

The `netplan.yml.jinja` file content:

```
---
network:
  version: 2
  renderer: networkd
  ethernets:
    uplink:
      match:
        name: en*
      addresses:
        - {{ server_address }}/{{ server_prefixlen }}
      routes:
        - to: default
          via: {{ server_gateway }}
{% if server_nameservers is defined %}
      nameservers:
        addresses:
    {% for address in server_nameservers %}
          - {{ address }}
    {% endfor %}
{% endif %}
```
