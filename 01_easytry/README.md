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

### try

### ping but is have warning

it's echo `[WARNING]: No hosts matched, nothing to do`

```
ansible 192.168.33.99 -m ping
```

we need set target in inventry file,
please see `hosts` file

#### 1. ping & hello world

```
ansible 192.168.33.100 -m ping
ansible 192.168.33.100 -m "shell echo 'hello world'"
```

#### 2. with inventry file

-i is inventry (default=/usr/local/etc/ansible/hosts)

```
ansible -i hosts myhosts -m ping
```

it's can setting in ansible.cfg

```
ansible myhosts -m ping
```

#### playbook hello world

playbook is setting file so what we do.

```
ansible-playbook test.yml
```


