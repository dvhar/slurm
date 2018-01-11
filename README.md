Ansible Role - slurm
====================

This role simply installs SLURM Workload Manager with the following configuration.

- Install directory: `/opt/slurm/{{ slurm_version }}`
- Configuration directory: `/opt/slurm/{{ slurm_version }}/etc`
- Logging directory: `/var/log/slurm`
- Slurmd spool directory: `/var/spool/slurmd`
- PAM Slurm: `/lib64/security/pam_slurm.so`

- examples directory predates my tinkering with it, may be deprecated

Platforms
---------

CentOS 6.7 and 7.2 are supported and tested so far.

Default Variables
-----------------

- slurm_version: `17.11.1-2`
- slurm_url: `https://download.schedmd.com/slurm/slurm-{{ slurm_version }}.tar.bz2`
- slurm_prefix: `/opt/slurm/{{ slurm_version }}`

Dependencies
------------

None.

Example Playbook
----------------

Include the role like this:

  - hosts: vcluster2
    tasks: [ ]

  - hosts: controller
    become: true
    roles:
    - { role: slurm, cluster: vcluster2, node_type: master }

  - hosts: workers
    become: true
    roles:
    - { role: slurm, cluster: vcluster2, node_type: slave }

License
-------

MIT License.

Authors
------

- Koji Tanaka - RDI2
- David Hardy
