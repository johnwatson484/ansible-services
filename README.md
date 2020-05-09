# Ansible Services
Ansible playbooks for creating shared services server

## Prerequisites
- Ansible

## Setting up server
### Update hosts file
Amend host and worker IP addresses as appropriate in `./hosts`

### Create Ubuntu user
`ansible-playbook -i ./hosts ./initial.yaml`

## PostgreSQL
### Install
`ansible-playbook -i ./hosts ./postgres/install.yaml`

### Configure
`ansible-playbook -i ./hosts ./postgres/configure.yaml`

### Create super user (Optional)
Create superuser with login rights from any source.  

Update `./postgres/super-user.yaml` with appropriate username and MD5 hashed password.  The example in the file uses `superuser` and `postgres` as the MD5 hash.  

`ansible-playbook -i ./hosts ./postgres/super-user.yaml`

### Create database (Optional)
Update `./postgres/database.yaml` with appropriate database, user and MD5 hashed password.  The example in the file uses `test`, `testuser` and `postgres` as the MD5 hash.  

`ansible-playbook -i ./hosts ./postgres/database.yaml`

## RabbitMQ
### Install
`ansible-playbook -i ./hosts ./rabbitmq/install.yaml`

### Configure
Update `./rabbitmq/configure.yaml` with appropriate management username and password.  

`ansible-playbook -i ./hosts ./rabbitmq/configure.yaml`
