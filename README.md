collectd Ansible role
=====================

Installs and configures collectd

Requirements
------------

 * CentOS 7.x
 * Ansible 2.x
 * systemd

Role Variables
--------------

See defaults/main.yml and `collectd.conf(5) <https://collectd.org/documentation/manpages/collectd.conf.5.shtml>`_

Example Playbook
----------------

    ---
    - hosts: localhost
      become: yes
      roles:
        - role: collectd
          collectd_interval: 60
          collectd_plugins:
            - syslog
            - network
            - cpu
            - ping
          collectd_network_servers:
            - hostname: localhost
              port: 25826
          collectd_ping_hosts:
            - example.com
            - 8.8.8.8
          collectd_package_version: 5.7.1

Tests
-----

Use [molecule](https://github.com/metacloud/molecule) to test this role.

Because this role depends on systemd and SELinux, only a Vagrant provider is configured at the moment.

License
-------

MIT
