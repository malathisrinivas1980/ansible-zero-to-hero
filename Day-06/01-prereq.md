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
ansible-vault is a command line and used in ansible, it enrypt, decrypt sensetive data like password, API token and yaml files ... It helps keep secrets secure in version control 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```
We need to pass vault.pass while running ansible playbook, because ansible look for token password in ansible-vault file, now that file password enycrption is stored in vault.pass
```
root@controlnode-europe ansible]# ansible-playbook ec2instancecreation.yaml 

PLAY [localhost] ***************************************************************
ERROR! Attempting to decrypt but no vault secrets found
[root@controlnode-europe ansible]# 
```
later, worked with below
```
 ansible-playbook ec2instancecreation.yaml  --vault-password-file vault.pass
```





