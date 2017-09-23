# sepalate

## include
include `tasks.yml` `tasks2.yml` `vars.yml`
```
ansible-playbook include.yml
```

`include.yml` is run setting.(it's mean can custom tasks)  
`include_vars` get values and carry under tasks.

include is free and no Directory Structure.

## role

roughly "role" is custom version for include.  
it's have "Directory Structure"  

document: [Roles — Ansible Documentation](https://docs.ansible.com/ansible/devel/playbooks_reuse_roles.html)  

### Directory Structure
important directory is "roles" "roles/any_role/tasks"  

```
site.yml
webservers.yml
fooservers.yml
roles/
   common/
     tasks/
       main.yml
     handlers/
     files/
     templates/
     vars/
     defaults/
     meta/
   webservers/
     tasks/
     defaults/
     meta/
```

main.yml(default run)

### run simple

```
ansible-playbook role.yml
```

role can use. `roles:` and `tasks/include_role`

attention: `tasks:` run after `roles:`


### run with tag

tag is runnning flag  
it's can set roles, tasks

```
ansible-playbook roletags.yml --tags test
ansible-playbook roletags.yml --tags test2
ansible-playbook roletags.yml --skip-tags skip
ansible-playbook roletags.yml --tags test,test2 --skip-tags skip
```


