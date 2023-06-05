# ansible-gitbucket

## Requirements
### On Host:
* dnf install mysql
* dnf install ansible
* ansible-galaxy collection install community.mysql
* ansible-galaxy collection install ansible.posix

## Usage
Edit `hosts` file to include your managed machine adresses. Change default passwords inside `vault.yml` with
```
ansible-vault edit vault.yml
```

After that change the default password "root" for vault.yml
```
ansible-vault rekey vault.yml
```

Initiate a playbook by running:
```
ansible-playbook -e @vault.yml --ask-vault-pass runsetup.yaml
```

