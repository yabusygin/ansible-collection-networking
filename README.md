Ansible Collection - yabusygin.networking
=========================================

The `yabusygin.networking` Ansible collection is used for setting up networking
configuration.

Included Content
----------------

Roles:

- `yabusygin.networking.netplan`: configure Netplan

Requirements
------------

Only the `ansible-core` package is required. Tested with the `ansible-core`
version 2.16.

Installation
------------

The collection may be installed with the following command:

```sh
ansible-galaxy collection install --requirements-file=requirements.yml
```

The `requirements.yml` file content:

```yaml
---
collections:
  - name: yabusygin.networking
```

License
-------

MIT

Author Information
------------------

Alexey Busygin \<yaabusygin@gmail.com\>
