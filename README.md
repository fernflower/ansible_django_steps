# ansible_django_steps
Ansible playbook for django_steps project deploy

### Installation
1. Put all sensitive data in *secret_vars.yml*.
2. Save ansible-vault password in *vault_pass.txt*. Though it's gitignored, still ... do not attempt to commit it!
3. Encrypt *secret_vars.yml*:
```
ansible-vault encrypt secret_vars.yml --vault-password vault_pass.txt
```
Decryption is symmetrical:
```
ansible-vault decrypt secret_vars.yml --vault-password vault_pass.txt
```
4. Prepare host and target machines:
  * set proper hosts and host variables in hosts file
  * make sure ansible is installed on both host and target
  * target machine can be reached by ssh from host
5. Run the playbook and enjoy your freshly deployed app :)
```
ansible-playbook deployme.yml -i hosts -K --vault-password-file vault_pass.txt
```
