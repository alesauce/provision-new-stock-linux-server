Role Name
=========

This is a role I created to do some of the first tasks needed for a new server in my homelab:
1. Create a new user
1. Transfer SSH keys
1. Secure SSH config
1. Change hostname

Nothing too crazy, but saves me some time now :)

**NOTE:** If you use this role, please note that it does change the SSH settings. I have tested this via Molecule with the current settings, but if you were to tweak any settings, I recommend that you have an SSH session logged into a host you are testing on so you don't get locked out.

Requirements
------------

Nothing outside of the builtin library here.

Role Variables
--------------

`new_user_name`: As you might guess, a variable for the name of the new user created by the role. Defaults to `new_user` (sorry, I wasn't feeling creative).

`user_groups`: Groups you want to add your new user to. Defaults:
```yaml
user_groups:
- sudo
- video
```

`ssh_public_key_file`: The location of your SSH **public** key to add to the server for authentication. Defaults to a file named `authorized_keys` in the same directory as the playbook running this role.

`can_sudo_passwordless`: If you want to be able to have any user part of the `sudo` group sudo passwordless, this will alter that setting. Defaults to `true`.

`change_ssh_port`: If you want to change the ssh port from the standard port 22. Defaults to `false`.

`new_ssh_port`: The companion to `change_ssh_port`. Only active if `change_ssh_port` is set to true. Defaults to `1337`.

`upload_new_sshd_config`: I have a lightly opinionated SSHD config available that will be templated out if you want. Defaults to `true`. TODO: Allow for uploading custom SSHD config.

`create_new_hostnames`: Will update the hostname of each host in your Ansible inventory based on the Ansible `{{ inventory_hostname }}`. Defaults to `true`.


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

License
-------

BSD

Author Information
------------------

[My GitHub](https://github.com/alesauce)
[My personal website](https://alexandersauceda.dev/)
