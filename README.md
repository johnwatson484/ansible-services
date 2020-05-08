# Ansible Services
Ansible playbooks for creating shared services server

## Prerequisites
- Ansible

## Setting up server
### Update hosts file
Amend host and worker IP addresses as appropriate in `./hosts`

### Create Ubuntu user
`ansible-playbook -i ./hosts ./initial.yaml`
