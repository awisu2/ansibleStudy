# easytry

ansible is python's integration tool

## install

```
brew install ansible
brew cask install varant vagrant-manager virtualbox
```

## hunds up

### create test hosts

```
cd 00_vagrant
vagrant up
```

### 0. ping but it have warning

it's echo `[WARNING]: No hosts matched, nothing to do`

```
ansible 192.168.33.99 -m ping
```

we need set target in inventry file,  
please see `hosts` file (not set 192.168.99)

#### 1. ping & hello world(with multi)

```
ansible 192.168.33.100 -m ping
ansible 192.168.33.100 -m "shell echo 'hello world'"
ansible 192.168.33.100,192.168.33.101 -m ping
```

#### 2. with inventry file

`-i` is inventry (default=/usr/local/etc/ansible/hosts)

```
ansible -i hosts myhosts -m ping
ansible -i hosts myhosts2 -m ping
```

it's can setting in ansible.cfg (please check ansible.cfg)  
this command not use `-i`

```
ansible myhosts -m ping
```

#### playbook hello world

playbook is setting file(yaml) so what we do.

```
ansible-playbook test.yml
```

## info


### escape ssh knownhost check
this sample's ansible.cfg have "ssh_connection", it's escape sshe knownhost check.
```
[ssh_connection]
ssh_args = -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null
```


