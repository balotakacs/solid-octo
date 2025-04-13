# solid-octo
As solid as it can be

### (Re-) Provisioning pi5 with Ansible
    - docker compose -up
    - docker exec -it ansible-control-node bash
    - ansible piservers -m ping -i hosts.yaml
    - ansible-playbook -i hosts.yaml playbook.yaml
