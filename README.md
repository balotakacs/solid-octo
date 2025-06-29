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

### Use Cloudflare tunnel to provision PulseAudio and more

We are trying to use cloudflared CLI installed in the container that runs anisble to establish ssh connection via a tunnel into the device in order for our playbooks to run against the PI.

For that we created tunnelHosts.yaml, with ssh-pi.balotakacs.com as the host and a special ProxyCommand as argument to the SSH connection in order to use cloudflared. 

Important caveat: before you are able to use this method, run 'ssh -o "ProxyCommand=cloudflared access ssh --hostname ssh-pi.balotakacs.com" balotakacs@ssh-pi.balotakacs.com' in the container before you  run any ansible comands. This will prompt you to authenticate and aquire a token.


### Lessons learnt
1. group_vars folder has to be at same level as playbook in Ansible.
2
