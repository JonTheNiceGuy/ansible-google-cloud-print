Role Name
=========

This role deploys Google-Cloud-Print-Connector, and optionally copies in the config file to allow remote printing.

Requirements
------------

Ubuntu Xenial or later, Debian Sid or later

Role Variables
--------------

All these variables are optional - the role defines defaults for them all.

* `gcp_username`: Username to run the GCP daemon as - default: `cloud-print-connector`
* `gcp_group`: Group to run the GCP daemon as - default: `nogroup`
* `gcp_config_file_path`: Destination of the config/secret file for this daemon - default: `/etc/cloud-print-connector`
* `gcp_config_file_name`: Actual file to use - default: `secret.json`
* `gcp_config_file_src`: the pre-generated config file to use. OPTIONAL. GCP Default config will be applied otherwise
* `force_gcp_config_file`: If gcp_config_file_src is not defined, but this is set, then force the systemd service to add the config path.

Dependencies
------------

None

Example Playbook
----------------

A basic playbook should be included like this:

    - hosts: servers
      roles:
         - role: jontheniceguy.google-cloud-print

A more complex one looks like this:

    - hosts: servers
      roles:
         - role: jontheniceguy.google-cloud-print
           gcp_username: gcp-user
           gcp_group: gcp-admins
           gcp_config_file_path: /home/gcp-user
           gcp_config_file_name: your-config-file.json
           force_gcp_config_file: True

License
-------

BSD

Author Information
------------------

Jon "The Nice Guy" Spriggs - jon@sprig.gs - https://jon.sprig.gs/blog/
