# ansible-role-cloud-info-provider

Ansible role for setting up [cloud-info-provider](https://github.com/indigo-dc/cloud-info-provider)

## Requirements

The role should be run in an environment where a supported cloud middleware is
available (OpenStack or OpenNebula).

## Role variables

Role variables with their default values.

### General configuration

* cloud_info_provider_sitename: TEST
* cloud_info_provider_conf_dir: /etc/cloud-info-provider-indigo
* cloud_info_provider_main_conf_file: bdii.yaml
* cloud_info_provider_require_martkeplace_id: false
* cloud_info_provider_middleware: openstack

### OpenStack configuration

* cloud_info_provider_os_username: admin
* cloud_info_provider_os_password: openstack
* cloud_info_provider_os_auth_url: http://127.0.01:5000/v2.0
* cloud_info_provider_os_tenant_name: demo

### OpenNebula configuration

* cloud_info_provider_on_auth: oneadmin:opennebula
* cloud_info_provider_on_xmrpc_url: http://127.0.0.1:2633/RPC2

### CMDB configuration

* cloud_info_provider_cmdb_read_url: http://indigo.cloud.plgrid.pl/cmdb
* cloud_info_provider_cmdb_write_url: http://couch.cloud.plgrid.pl/indigo-cmdb-v2
* cloud_info_provider_cmdb_user: unset but mandatory
* cloud_info_provider_cmdb_password: unset but mandatory

## Example Playbook

    - hosts: servers
      roles:
         - { role: indigo-dc.cloud-info-provider, cloud_info_provider_cmdb_user=XXXX, cloud_info_provider_cmdb_password=1h3$3Cur3P4$$ }

## License

MIT

## Author Information

Baptiste Grenier <baptiste.grenier@egi.eu>
