- groupe all 

```bash
ansible -m ping -i hosts -u ansible all
```

- tester la connexion à arch1

```bash
ansible -m ping -i hosts -u ansible arch1
```

- l'inventaire est un fichier ini (illisible) ou YAML

- ansible est un outil qui fait exactement ça

- on peut "automatiser" :

```pseudo-shell
for host in ./host-file:
  scp script.sh ansible@$host:/tmp
  ssh ansible@$host "exec /tmp/script.sh > /tmp/script.out"
  scp ansible@$host:/tmp/script.out /tmp
  cat /tmp/script.out
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
