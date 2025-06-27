# solid-octo, that is my Git repo for projects on Raspberrypi 5
As solid as it can be

### (Re-) Provisioning pi5 with Ansible
##### Docker container up with Ansible control node
```
docker compose -up
docker exec -it ansible-control-node bash
```
##### Ping and run hello world playbooks
```
ansible piservers -m ping -i hosts/hosts.yaml
ansible-playbook -i hosts/hosts.yaml playbooks/helloworld.yaml
```
##### Run playbook to setup timeshift
```
ansible-playbook -i hosts/hosts.yaml playbooks/timeshift.yaml
```
##### Run only snapshot on-demand
```
ansible-playbook -i hosts/hosts.yaml playbooks/timeshift.yaml --tags system_snapshot
```


### Lessons learnt
1. group_vars folder has to be at same level as playbook in Ansible.
2
