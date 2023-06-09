# ansible-gitbucket

<p align="center">
  <img src="images/diagram.svg" />
</p>

This ansible playbook is intented for personal use. But feel free to borrow or modify it for your needs.

## Requirements
* The architecture allows for 1 Load Balancer, 1 Shared Database, 1 Shared NFS Server, and an `n` number of workers. So in total you need to have `3 + n` servers. 
* All servers must be some flavor of `RHEL`, `Oracle Linux` or `CentOS`.  
* Firewall rules restrict ingress trafic to `10.26.0.0/24` mask, so be aware of that.


### On Host:
* sudo dnf update
* dnf install ansible-core mysql
* ansible-galaxy collection install community.mysql
* ansible-galaxy collection install ansible.posix

## Usage
Edit `hosts` file to include your managed machine adresses. Configure an ssh connection to your managed machines.

Сhange the default password 'root' for vault.yml:
```
ansible-vault rekey vault.yml
```

Change default password variables inside `vault.yml` with:
```
ansible-vault edit vault.yml
```

Initiate a playbook by running:
```
ansible-playbook -e @vault.yml --ask-vault-pass runsetup.yaml
```

