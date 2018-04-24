

- Variables set_fact and register

```
ansible-playbook bonjour_7.yml --inventory hosts.yml --user ansible
```
 
- Variables Inventory

```
ansible-playbook bonjour_4.yml --inventory envs/dev/hosts.yml --user ansible
```

- Variables (host_vars/group_vars)

```
ansible-playbook bonjour_4.yml --inventory hosts.yml --user ansible
```

- Variables (vars_file:)
```
ansible-playbook bonjour_6.yml --inventory hosts.yml --user ansible
```


- Variables (var:)

```
ansible-playbook bonjour_5.yml --inventory hosts.yml --user ansible
```


- Variables (-e)
https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable
```
ansible-playbook bonjour_4.yml --inventory hosts.yml --user ansible --extra-vars="filename=custom_var_filename hello=Hi"
ansible -m shell -a "cat /tmp/custom_var_filename" -i hosts.yml -u ansible arch1
```

- Templates 

```
ansible-playbook bonjour_2.yml -i hosts.yml -u ansible arch1
```

http://jinja.pocoo.org/docs/2.10/templates/
(essayer 2/3 trucs: if, for, comments, macros)

- What's this "Gathering facts" ?
+ module debug
```
ansible-playbook bonjour_2.yml -i hosts.yml -u ansible arch1
```

- un playbook est une liste de "play" (https://www.merriam-webster.com/dictionary/playbook)

```
ansible-playbook bonjour_1.yml -i hosts.yml -u ansible arch1
```

- gather facts (module setup)

```
ansible -m setup -i hosts.yml -u ansible arch1
```

utiliser `ansible_facts.ansible_default_ipv4.address`

- module copy

```bash
ansible -m copy -a "src=templates/bonjour dest=/tmp/bonjour" -i hosts.yml -u ansible archlinux
ssh arch1
```

- modules aka "task plugin" aka "library plugin"

```bash
ansible-doc -l
ansible-doc ping
ansible -m ping -a "data=punk" -i hosts.yml -u ansible webserver
```

- une machine peut être dans plrs groupes 

```bash
ansible -m ping -i hosts.yml -u ansible webserver
```

- création de groupe `webserver` et `load-balancer`

```bash
ansible -m ping -i hosts.yml -u ansible webserver
ansible -m ping -i hosts.yml -u ansible load-balancer
```
- groupe all 

```bash
ansible -m ping -i hosts.yml -u ansible all
```

- tester la connexion à arch1

```bash
ansible -m ping -i hosts.yml -u ansible arch1
```

- l'inventaire est un fichier ini (illisible) ou YAML

- ansible est un outil qui fait exactement ça

- on peut "automatiser" :

```pseudo-shell
for host in ./host-file:
  scp script.sh ansible@$host:/tmp
  ssh ansible@$host "exec /tmp/script.sh"
```
- par ssh :

```bash
ssh ansible@arch1
ls /tmp/bonjour # check not already done
ip addr
echo "Bonjour je suis 192.168.1.37" >> /tmp/bonjour
``` 

et pareil pour `arch2`


- on veut créer un fichier `/tmp/bonjour` sur chaque machine :
  
      Bonjour je suis <addresse ip>.
        
- il y a 2 machines : arch1 et arch2 
  - python
  - openssh

 


- [ansible-galaxy](http://docs.ansible.com/ansible/latest/reference_appendices/galaxy.html)
