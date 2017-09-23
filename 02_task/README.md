# playbook

## use value
set test.yml `{{username}}` `{{msg}}` `{{msg2}}`
```
ansible-playbook test.yml --extra-vars "username=foo"
```

`--extra-vars` set value and overwrite vars_files's value.  
please try this command
```
ansible-playbook test.yml
```
it's return "hello" "world". set to "vars.yml"  
and can set inventryfile(hosts) it's overwrited by varsfile.

### vars strong order

1. cli
2. task vars_files
3. inventryfile vars

## tasks

yum update & run task multi value  

```
ansible-playbook test2.yml
```

this task use sudo. if use sudo yes, echo warning.  
want not display warning set ansible.cfg 'deprecation_warnings=False'

### documents

[Module Index — Ansible Documentation](https://docs.ansible.com/ansible/devel/modules_by_category.html)

#### mypickup

- [Utilities modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_utilities_modules.html)
    - "debug"
- [Packaging modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_packaging_modules.html)
    - "yum"
- [Commands modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_commands_modules.html)
    - "command" "script" "shell"
- [Files modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_files_modules.html)
    - "copy" "find" "replace" "unarchive"
- [Source Control modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_source_control_modules.html)
    - "git"
- [System modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_system_modules.html)
    - "firewalld" "hostname" "iptables" "make" "ping" "selinux" "sysctl" "timezone" "user"
- [Crypto modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_crypto_modules.html)
    - "ssh"
- [Notification modules — Ansible Documentation](https://docs.ansible.com/ansible/devel/list_of_notification_modules.html)
    - notification "slack" "mail" "syslogger" etc...

### yum

- state
    - present(default): install if not install
    - installed: install if not install
    - latest: install if it's have later version
    - absent: uninstall
    - removed: uninstall
