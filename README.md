Experitest - Reporter ansible role
=========

This role will install \ uninstall reporter for windows hosts

Requirements
------------

This role assumes that you have java 8 installed on the instance
Supports mac os hosts only.

Role Variables
--------------

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| state | should the application be present or absent | present, absent | present | no |
| app_version | application version to install | string | 12.4.838 | no |
| server_port | port number for the server | number | 8080 | no |
| db_connection_string | connection string to postgres | string | jdbc:postgresql://localhost:5432/reporter | no |
| db_username | username for db connection | string | postgres | no |
| db_password | password for db connection | string |  | no |
| installation_folder | the folder in which the applction will be installed | string | for mac: ~/experitest/reporter-version <br> for windows: C:\\Experitest\\reporter  | no |
| jmx_port | port number for jmx inspection | number | 51234 | no |
| custom_download_url | custom url to download the installation from (zip format) | string |  | no |
| start_after_install | should application start after installation is completed | boolean | True | no |
| clear_temp_folder | remove temp folder after installation | boolean | False | no |
| clear_before_install | removing old installation before installing new version | boolean | False | no |

Example Playbook
----------------

#### [see working example](/example)

In requirements.yml file

    - src: git+https://github.com/ExperitestOfficial/ansible-role-reporter.git
      version: master
      name: reporter


In site.yml file

    - hosts: reporters
      roles:
        - role: reporter

To invoke, run the following commands:

- install dependencies \
  *ansible-galaxy install -r requirements.yml --force*

- run the playbook \
  *ansible-playbook site.yml*
