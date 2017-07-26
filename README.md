marcusianlevine.cifs-mount
=========

Mount CIFS network shared drive with Samba

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

### Required

* `domain`: AD domain name e.g. example.domain.com
* `samba_share`: Domain name of shared drive e.g. //my-cifs-share.example.domain.com/sharedfolder
* `samba_mount_user`: Name of the domain user that will be used to authenticate against the shared drive during mount
* `samba_mount_pass`: Password for `samba_mount_user`

### Optional

* `samba_mount_path`: Path at which the drive will be mounted (default: `/share`)
* `samba_user`: Username of the user who will own the mounted drive (default: `ansible_user_id`)
* `samba_home`: Home directory of `samba_user` (default: `{{ ansible_env.HOME }}`)

Example Playbook
----------------

``` yaml
    - hosts: servers
      vars_files:
        - secrets/mysecrets.yml
      roles:
        - role: marcusianlevine.cifs-mount
          domain: example.domain.com
          samba_share: "//my-cifs-share.{{ domain }}/sharedfolder"
          samba_mount_user: myuser
          samba_mount_pass: "{{ vaulted_password_value }}"
```

License
-------

BSD

Author Information
------------------

Written by Marcus Levine for CKM Advisors