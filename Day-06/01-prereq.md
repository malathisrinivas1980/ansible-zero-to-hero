# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

ansible-vault is a command-line tool that comes with Ansible, used to encrypt and decrypt sensitive data like passwords, API keys, or entire YAML files. It helps keep secrets secure in version control.
1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```





