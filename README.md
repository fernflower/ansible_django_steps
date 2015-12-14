# ansible_django_steps
Ansible playbook for django_steps project deploy

### Installation
1. Put all sensitive data in *secret_vars.yml*. Required variables are:
```
django_secret_key: yoursecretkeyhere
django_superuser: youruser
django_superpass: yourpass
dbname: yourdb
dbuser: yourdbuser
dbpass: yourdbpass
```
Save ansible-vault password in *vault_pass.txt*. Though it's gitignored, still.. do not try to commit it!
Encrypt *secret_vars.yml*:
```
ansible-vault encrypt secret_vars.yml --vault-password-file vault_pass.txt
```
Decryption is symmetrical:
```
ansible-vault decrypt secret_vars.yml --vault-password-file vault_pass.txt
```


2. Prepare host and target machines:
  * set proper hosts and host variables in hosts file
  * make sure ansible is installed on both host and target
  * target machine can be reached by ssh from host
3. Run the playbook and enjoy your freshly deployed app :)
```
ansible-playbook deployme.yml -i hosts -K --vault-password-file vault_pass.txt
```
