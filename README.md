# ar-awx-docker-requirements

Ansible role to install awx requirements when using ["docker-compose"](https://github.com/ansible/awx/blob/devel/INSTALL.md#prerequisites-3)

## Role variables

```yaml
# Will create /etc/environment if it does not exists & add the following value (usefull when using pip3)
# LC_ALL=en_US.UTF-8
# LC_CTYPE=en_US.UTF-8
awx_req_set_env: false
```

## Playbook example
```yaml
---
- hosts: awx
  gather_facts: true
  become: true
  
  tasks:
    - name: AWX install requirements
      include_role: name=awx-requirements
```

When using python3 on remote host, it is usefull to set the `ansible_python_interpreter` variable

```
[awx]
stretch2 ansible_ssh_host=192.168.62.2 ansible_user=vagrant
buster3 ansible_ssh_host=192.168.62.3 ansible_user=vagrant ansible_python_interpreter=/usr/bin/python3
xenial4 ansible_ssh_host=192.168.62.4 ansible_user=vagrant ansible_python_interpreter=/usr/bin/python3
bionic5 ansible_ssh_host=192.168.62.5 ansible_user=vagrant ansible_python_interpreter=/usr/bin/python3
```

[vagrant](https://github.com/slgevens/vagrant/blob/master/ansible_tests/Vagrantfile)

## License

[MIT](./LICENSE)
