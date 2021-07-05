Ansible Role: Logwatch
=========

An Ansible role that installs and configures [Logwatch][logwatch].

Requirements
------------

 - Ansible 2.10+ (uses ansible.builtin.package)

Role Variables
--------------

This role aims to provide full coverage for configuration options of Logwatch, including the ignores.conf file.
Options are described in detail in both the logwatch-ignores.conf.j2 and logwatch.conf.j2 templates, as well as
the defaults/main.yaml file in this role.

The main variables you are likely to care about are described below, but this is not a complete list of variables that are supported within this role.  For that, see the defaults/main.yaml file.

### Basic Variables

Example values for variables are all the distribution defaults except 'logwatch_disabled_services' and 'logwatch_ignores' which are empty by default, 
but have been populated with sample data as examples.

```yml
logwatch_mailto: root
logwatch_mailfrom: Logwatch
logwatch_format: text
logwatch_range: Yesterday
logwatch_detail: Low
logwatch_service: All
logwatch_disabled_services:
  - zz-disk_space
  - zz-lm_sensors
logwatch_ignores:
  - apparmor=\"ALLOWED\"
  - ACPI BIOS Error
```


Dependencies
------------

None

Example Playbook
----------------

```yml
    - hosts: servers
      vars:
        logwatch_mailto: kfiresmith@college.edu
        logwatch_mailfrom: logwatch-noreply
        logwatch_output: mail
        logwatch_range: yesterday
        logwatch_detail: Low
        logwatch_service: All
      roles: kfiresmith.logwatch
```

License
-------

MIT

Author Information
------------------

This role was created in 2021 by [Kodiak Firesmith][github], an ops guy at [Woods Hole Oceanographic Institution][whoi].
Aside from [GitHub][github], I'm most active on [LinkedIn][linkedin].

[whoi]: https://whoi.edu
[github]: https://github.com/kfiresmith
[linkedin]: https://www.linkedin.com/in/kodiak-firesmith-b6059434/
[logwatch]: https://sourceforge.net/projects/logwatch/
