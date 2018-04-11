- un playbook est une liste de play (un recueil de pièces de théâtre)

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
