# Rendu Packer Etienne DRAPP

Le playbook.yaml a besoin d'aller chercher le template du service le dossier template. Le dossier doit se trouver dans ce chemin (ou alors modifier le chemin dans le playbook) :

```bash
/root/Etienne-TP1-PACKER/template/golang.service
```

#### SELinux

Pour set selinux en permissive, il y a potentiellement besoin d'installer la collection posix. Mais comme cette dernière est renseignée dans le playbook.yaml, ceci n'est pas obligatoire

```bash
ansible-galaxy collection install ansible.posix
```


# packer-course-bootstrap

## Kickstart 

#### Générer le mot de passe de root

```bash
openssl passwd -6
```
La suite de caractére obtenu est a spécifier de la maniére suivante :
```ks
rootpw --iscrypted <password>
```


## Debug

#### Augmenter le niveau de log de packer

Avant de lancer Packer définissez la variable d'environnement 'PACKER_LOG'.

```bash
export PACKER_LOG=1
```
#### Augmenter le niveau de log d'Ansible
Dans votre fichier PAcker, ajouter la configuration suivante au provisionner d'Ansible.

```hcl
    extra_arguments = [ "-vv" ]
```
