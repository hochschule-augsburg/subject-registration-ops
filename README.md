# Subject Registration Ops

This repository contains the scripts and necessary files to put the
HSA subject registration into operation.

## Ansible dependencies

This playbook requires the `geerlingguy.docker` role.

```
ansible-galaxy install geerlingguy.docker
```

## Local setup with Vagrant

Start a plain debian VM with vagrant and run the setup playbooks:

```
vagrant up
vagrant ssh # (run at least once to setup ssh key)

ansible-playbook -i hosts/vagrant setup.yml
ansible-playbook -i hosts/vagrant subjectreg.yml
```

## Production setup

```
ansible-playbook -i hosts/prod setup.yml
ansible-playbook -i hosts/prod subjectreg.yml
```

## Post-Setup

**Create an admin user for Keycloak:**

Adding default credentials to the dockerfile has caused issues when restarting the Keycloak container.

```
docker exec <CONTAINER> /opt/jboss/keycloak/bin/add-user-keycloak.sh -u <USERNAME> -p <PASSWORD>
```
