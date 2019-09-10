hmpps-delius-core-389ds-bootstrap
=========

Ansible role to setup/configure a [389 Directory Server](https://directory.fedoraproject.org) instance for use with National Delius in AWS.


Role Variables
--------------

```yaml
workspace: Workspace location for storing temporary files during bootstrap

# AWS
s3_dependencies_bucket: S3 bucket name containing artefacts
s3_backups_bucket: S3 bucket name to be used for LDIF backups

# LDAP
ldap_protocol: Protocol to be expose the ldap on - ldap or ldaps 
ldap_port: Port to expose the ldap on
bind_user: Admin user to create. Default='cn=Directory Manager'.
bind_password: Desired password for the admin user.
base_root: The root context for the directory (eg. dc=moj,dc=com)
base_users: The context where users are stored (eg. cn=Users,dc=moj,dc=com). Note it is assumed base_root is the direct parent of base_users.

# 389 DS
dirsrv_user: Linux user to run the directory service as. Default=dirsrv.
dirsrv_group: Linux group to add the user to. Default=dirsrv.

# Data import
import_users_ldif: LDIF file to import from the s3_backups_bucket. This can be set to LATEST to retrieve the latest backup from S3. Default=None (no users)
import_users_ldif_base_users: The context where users are stored in the imported LDIF (eg. ou=NDProd,cn=Users,dc=moj,dc=com)
sanitize_oid_ldif: Whether to remove Oracle-specific attributes from the LDIF
perf_test_users: Number of users to create to support performance testing. Default=0

```

Dependencies
------------


License
-------

MIT

Author Information
------------------

HMPPS Digital Studio
