# ansible-role-enable-ansible

This role is used for one shot use. It creates an *ansible* user and group.

## Description

By default this role creates an user `ansible` and corresponding group `ansible`.

## Role Variables


| Name                                 |   Default   | Description                                                                                                                                                                            |
| :----------------------------------- | :---------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `enable_ansible_username`            |  `ansible`  | Username for ansible user.                                                                                                                                                             |
| `enable_ansible_username_password`   |     ""      | Set password for ansible user. It has to be hased See: https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module |
| `enable_ansible_uid`                 |   `9999`    | UID of ansible user.                                                                                                                                                                   |
| `enable_ansible_shell`               | `/bin/bash` | Default shell for ansible user.                                                                                                                                                        |
| `enable_ansible_authorized_pub_keys` |     []      | Public key to add to authorized_key file. (**MANDATORY**)                                                                                                                              |
| `enable_ansible_groupname`           |  `ansible`  | Groupname of ansible user primary group.                                                                                                                                               |
| `enable_ansible_gid`                 |   `9999`    | UID of primary group.                                                                                                                                                                  |
| `enable_ansible_group_sudo`          |   `true`    | Enable `sudo` without entering password                                                                                                                                                |
| `enable_ansible_sudo_nopasswd`       |   `false`   | If true you do not have to enter a password to escalate privilieges for `sudo`.                                                                                                        |


## Role Tags

| Name                       | Description                 |
| -------------------------- | --------------------------- |
| `enable_ansible_all`       | Tag to run all tasks.       |
| `enable_ansible_preflight` | Tag to run preflight tasks. |
| `enable_ansible_install`   | Tag to run install tasks.   |
| `enable_ansible_configure` | Tag to run configure tasks. |

## Dependencies

**None**

## Example Playbook


```yaml
- name: All
  hosts: all
  debugger: on_failed
  roles:
    - role: ansible-role-enable-ansible
      vars:
        enable_ansible_authorized_pub_keys:
          - "lookup('file', '/path/to/key.pub')"
```

## License

MIT License

## Contributors

Daniel von Essen
