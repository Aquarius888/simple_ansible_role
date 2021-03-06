# Role Name
------------
ca-role

## Description
------------
Simple Ansible role that generate root CA pair and create selfsigned certificate

## Requirements
------------
pyopenssl is requred (pip install pyopenssl)

### Role Variables
--------------
- cert_common_name: certificate Common Name (CN)
- cert_country: certificate Country
- client_cert_email_address: the email address used in client certificate
- server_cert_email_address: the email address used in server certificate
- ca_cert_email_address: the email address used in CA certificate
- cert_locality: certificate Locality
- cert_dir: the target directory that files will be output to
- cert_organizational_unit: certificate Organizational Unit
- client_cert_organizational_unit: certificate Organizational Unit client
- server_cert_organizational_unit: certificate Organizational Unit server
- ca_cert_organizational_unit: certificate Organizational Unit CA
- cert_organization: certificate Organization
- cert_state: certificate State
- server_name: the name of the server (or otherwise) that will be utilizing the certificate
- force_regeneration: overwrite existing certificate files
- cert_passphrase: password phrase
- root_ca_name: name of root CA

Example Playbook
----------------
see tests/test.yml

```
    - hosts: localhost
      tasks:
      - include_role:
          name: ca-role
        vars:
          server_name: "server"
          client_name: "client"
          server_url: "test.com" 
```

### Notes
---------

Ubuntu16.04 core

Add this snippet to the top of your playbook. 
It will install python2 if missing (but checks first so no expensive repeated apt updates)


```
 - hosts: all
   gather_facts: False
   tasks:
   - name: install python 2
     raw: test -e /usr/bin/python || (apt -y update && apt install -y python-minimal)
```

Centos7 core (TODO via Ansible)

Need to install pip, pyopenssl

``` 
 yum install -y epel-release
 yum install -y python-pip
 pip install pyopenssl
```

### TODO
----------

Write Dockerfile: Centos7-base, python2, pyopenssl-17.5.0, ansible-2.7 - versions defense
