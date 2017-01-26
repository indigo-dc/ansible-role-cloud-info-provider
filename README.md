# ansible-role-cloud-info-provider

Ansible role for setting up [cloud-info-provider-indigo](https://github.com/indigo-dc/cloud-info-provider-indigo)

[![BuildStatus](https://travis-ci.org/indigo-dc/ansible-role-cloud-info-provider.svg?branch=master)](https://travis-ci.org/indigo-dc/ansible-role-cloud-info-provider)

## Requirements

The role should be run in an environment where a supported cloud middleware is
available (OpenStack or OpenNebula).

## Role variables

Role variables with their default values.

### General configuration

* cloud_info_provider_sitename: TEST
* cloud_info_provider_conf_dir: /etc/cloud-info-provider
* cloud_info_provider_main_conf_file: static.yaml
* cloud_info_provider_tpl_extension: indigo
* cloud_info_provider_setup_cron: unset. Set to true to enable cron job.
* cloud_info_provider_require_martkeplace_id: unset. Set to true to enable filter.
* cloud_info_provider_middleware: unset but mandatory

### OpenStack configuration

* cloud_info_provider_os_release: liberty
* cloud_info_provider_os_username: admin
* cloud_info_provider_os_password: openstack
* cloud_info_provider_os_auth_url: http://127.0.01:5000/v2.0
* cloud_info_provider_os_tenant_name: demo

### OpenNebula configuration

* cloud_info_provider_on_auth: oneadmin:opennebula
* cloud_info_provider_on_rpcxml_url: http://127.0.0.1:2633/RPC2

### CMDB configuration

* cloud_info_provider_cmdb_read_url: http://indigo.cloud.plgrid.pl/cmdb
* cloud_info_provider_cmdb_write_url: http://couch.cloud.plgrid.pl/indigo-cmdb-v2
* cloud_info_provider_cmdb_user: unset but mandatory
* cloud_info_provider_cmdb_password: unset but mandatory

## Example Playbook

``` yaml
---
- hosts: node1
  roles:
    - role: indigo-dc.cloud-info-provider
      cloud_info_provider_sitename: TEST
      cloud_info_provider_middleware: indigoon
      cloud_info_provider_setup_cron: true
      # OpenNebula configuration
      cloud_info_provider_on_auth: oneadmin:opennebula
      cloud_info_provider_on_xmlrpc_url: http://127.0.0.1:2633/RPC2
      # CMDB configuration
      cloud_info_provider_cmdb_read_url: http://indigo.cloud.plgrid.pl/cmdb
      cloud_info_provider_cmdb_write_url: http://couch.cloud.plgrid.pl/indigo-cmdb-v2
      cloud_info_provider_cmdb_user: XXXXXXXXXXX
      cloud_info_provider_cmdb_password: XXXXXXXXXXX
```

## License

MIT

## Author Information

Baptiste Grenier <baptiste.grenier@egi.eu>
