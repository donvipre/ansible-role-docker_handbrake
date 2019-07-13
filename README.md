# Ansible Role: docker_handbrake

An Ansible role to deploy handbrake application as [container](https://github.com/jlesage/docker-handbrake). Thanks to Jocelyn Le Sage for this!

## Requirements

used modules:
  - [docker_container](https://docs.ansible.com/ansible/latest/modules/docker_container_module.html)
  - [docker_image](https://docs.ansible.com/ansible/latest/modules/docker_image_module.html)
  - [docker_network](https://docs.ansible.com/ansible/latest/modules/docker_network_module.html)

Fedora RPM packages:
  - python3-docker

## Installation

Install from [Github](https://github.com/donvipre/ansible-role-docker_handbrake)
```
git clone https://github.com/donvipre/ansible-role-docker_handbrake.git ansible-role-docker_handbrake
```

## Role variables

```
---
# defaults file for ansible-role-docker_handbrake

handbrake_name: handbrake
handbrake_image: jlesage/handbrake
handbrake_timezone: Etc/UTC
handbrake_display_width: "1280"
handbrake_display_height: "768"
handbrake_published_ports:
  - "5800:5800"
handbrake_network: handbrake
handbrake_iprange: 10.1.1.0/24
handbrake_volumes:
  - "/docker/appdata/handbrake:/config:rw"
  - "{{ lookup('env','HOME') }}:/storage:ro"
  - "{{ lookup('env','HOME') }}/HandBrake/watch:/watch:rw"
  - "{{ lookup('env','HOME') }}/HandBrake/output:/output:rw"
```

## Dependencies

None.

## Example Playbook

```
- hosts: servers
  roles:
    - ansible-role-docker_handbrake
```

## License

This work is licensed under [BSD-3-Clause](./LICENSE)

## Author Information

- Author: Uwe Arnold
- Mail: [donvipre@gmail.com](mailto:donvipre@gmail.com)
