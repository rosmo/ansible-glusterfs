ansible-glusterfs
=================

Ansible GlusterFS module for managing GlusterFS volumes.

## Sample playbook

```
---
- hosts: gluster-test
  remote_user: root
  tasks:
  - name: create gluster volume
    glusterfs: action=create name=test1 brick=/bricks/brick1/g1 rebalance=yes
    args:
      hosts: "{{ play_hosts }}"
    run_once: true

  - name: tune
    glusterfs: action=tune name=test1 option=performance.cache-size parameter=256MB
    run_once: true

  - name: start gluster volume
    glusterfs: action=start name=test1
    run_once: true

  - name: limit usage
    glusterfs: action=limit-usage name=test1 directory=/foo value=20.0MB
    run_once: true

  - name: stop gluster volume
    glusterfs: action=stop name=test1
    run_once: true
```

(c) 2014, Taneli Leppä <taneli@crasman.fi>

```
This file is part of Ansible (sort of)

Ansible is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

Ansible is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with Ansible.  If not, see <http://www.gnu.org/licenses/>.
```