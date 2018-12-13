# Role Name
=========

ca-role

## Requirements
------------

pyopenssl is requred (pip install pyopenssl)

### Role Variables
--------------

 cert_common_name: certificate CN
 cert_country: certificate Country
 cert_email_address: the email address used in certificate
 cert_locality: certificate Locality
 cert_dir: the target directory that files will be output to
 cert_organizational_unit: certificate Organizational Unit
 cert_organization: certificate Organization
 cert_state: certificate State
 server_name: the name of the server (or otherwise) that will be utilizing the certificate
 force_regeneration: overwrite existing certificate files
 cert_passphrase: password phrase


Example Playbook
----------------

    - hosts: localhost
      tasks:
      - include_role:
          name: ca-role
        vars:
          server_name: "test_server"
          server_url: "test.com"
