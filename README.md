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

> Remember to expose port if remove required.

### Create super user (Optional)

Create superuser with login rights from any source.  

Update `./postgres/super-user.yaml` with appropriate username and MD5 hashed password.  The example in the file uses `superuser` and `postgres` as the MD5 hash.  

`ansible-playbook -i ./hosts ./postgres/super-user.yaml`

### Create database (Optional)

Update `./postgres/database.yaml` with appropriate database, user and MD5 hashed password.  The example in the file uses `test`, `testuser` and `postgres` as the MD5 hash.  

`ansible-playbook -i ./hosts ./postgres/database.yaml`

## MongoDB

### Install

`ansible-playbook -i ./hosts ./mongo/install.yaml`

### Configure

`ansible-playbook -i ./hosts ./mongo/configure.yaml`

> Remember to expose port if remove required.

### Create super user (Optional)

Create superuser with login rights from any source.  

Update `./mongo/super-user.yaml` with appropriate username and MD5 hashed password.  The example in the file uses `superuser` and `mongo`.

`ansible-playbook -i ./hosts ./mongo/super-user.yaml`

## RabbitMQ

### Install

`ansible-playbook -i ./hosts ./rabbitmq/install.yaml`

### Configure

Update `./rabbitmq/configure.yaml` with appropriate management username and password.  

`ansible-playbook -i ./hosts ./rabbitmq/configure.yaml`

> Remember to expose port if remove required.

## Kafka

### Install

`ansible-playbook -i ./hosts ./kafka/install.yaml`

### Configure

`ansible-playbook -i ./hosts ./kafka/configure.yaml`

> Remember to expose port if remove required.

### Configure authentication (Optional)

Configure SASL/SCRAM auth for broker. Also adds an initial client user. 

Update `./kafka/configure-auth.yaml` with appropriate username passwords.  The example in the file uses `kafka` for username of the broker and `client` for clients. 

The public IP address in the listener configuration also needs updating.

`ansible-playbook -i ./hosts ./kafka/configure-auth.yaml`
