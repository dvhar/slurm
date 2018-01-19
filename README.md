Ansible Role - slurm
====================

This role simply installs SLURM Workload Manager with the following configuration.

- Install directory: `/opt/slurm/{{ slurm_version }}`
- Configuration directory: `/opt/slurm/{{ slurm_version }}/etc`
- Logging directory: `/var/log/slurm`
- Slurmd spool directory: `/var/spool/slurmd`
- PAM Slurm: `/lib64/security/pam_slurm.so`

Platforms
---------

CentOS 6 and 7

Dependencies
------------

None.

Example Playbook and Inventory
----------------

Include the role like this:

    - hosts: slurmcluster
      become: true
      roles:
      - role: slurm

make sure the inventory file has groups 'controller' and 'workers' like this:

    [slurmcluster:children]
    controller
    workers

    [controller]
    headnodename

    [workers]
    worknode1
    worknode2
    worknode3

License
-------

MIT License.

Authors
------

- Koji Tanaka - RDI2
- David Hardy
