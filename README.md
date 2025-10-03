# <center>**Gestion des Permissions en Linux :**</center>

<br>
<br>

## **Table des Matières**

- [**1. La commande chmod**](#1-chmod)
  - [1.1. À quoi sert ?](#11-à-quoi-sert-)
  - [1.2. Syntaxe](#12-syntaxe-)
  - [1.3. Options utiles](#13-options-utiles)
- [**2. La commande chown**](#2-chown)
  - [2.1. À quoi sert chown ?](#21-à-quoi-sert-chown-)
  - [2.2. Syntaxe de chown](#22-syntaxe-de-chown-)
  - [2.3. Options utiles](#23-options-utiles)
- [**3. La commande sudo**](#3-sudo)
  - [3.1. À quoi sert sudo ?](#31-à-quoi-sert-sudo-)
  - [3.2. Syntaxe de sudo](#32-syntaxe-de-sudo-)
  - [3.3. Cas d’utilisation](#33-cas-dutilisation-)
  - [3.4. Options utiles](#34-options-utiles)
  - [3.5. Exemples pratiques](#35-exemples-pratiques-)
  - [3.6. Points importants à retenir](#36-points-importants-à-retenir-)
- [**4. La commande su**](#4-su)
  - [4.1. À quoi sert su ?](#41-à-quoi-sert-su-)
  - [4.2. Différence avec sudo](#42-différence-avec-sudo)
  - [4.3. Syntaxe de su](#43-syntaxe-de-su-)
  - [4.4. Cas d’utilisation](#44-cas-dutilisation-)
  - [4.5. Options utiles](#45-options-utiles)
  - [4.6. Exemples pratiques](#46-exemples-pratiques-)
  - [4.7. Points importants](#47-points-importants-)
- [**5. La commande passwd**](#5-passwd)
  - [5.1. À quoi sert passwd ?](#51-à-quoi-sert-passwd-)
  - [5.2. Syntaxe](#52-syntaxe-)
  - [5.3. Cas d’utilisation](#53-cas-dutilisation-)
  - [5.4. Options utiles](#54-options-utiles)
  - [5.5. Exemples pratiques](#55-exemples-pratiques-)
- [**6. La commande adduser**](#6-adduser)
  - [6.1. À quoi sert ?](#61-à-quoi-sert-)
  - [6.2. Syntaxe](#62-syntaxe-)
  - [6.3. Cas d’utilisation](#63-cas-dutilisation-)
  - [6.4. Options utiles](#64-options-utiles)
  - [6.5. Exemples pratiques](#65-exemples-pratiques-)
- [**7. La commande deluser**](#7-deluser)
  - [7.1. À quoi sert ?](#71-à-quoi-sert-)
  - [7.2. Syntaxe](#72-syntaxe-)
  - [7.3. Cas d’utilisation](#73-cas-dutilisation-)
  - [7.4. Options utiles](#74-options-utiles)
  - [7.5. Exemples pratiques](#75-exemples-pratiques-)
- [**8. La commande groups**](#8-groups)
  - [8.1. À quoi sert ?](#81-à-quoi-sert-)
  - [8.2. Syntaxe](#82-syntaxe-)
  - [8.3. Cas d’utilisation](#83-cas-dutilisation-)
  - [8.4. Options utiles](#84-options-utiles)
  - [8.5. Exemples pratiques](#85-exemples-pratiques-)
- [**9. La commande addgroup**](#9-addgroup)
  - [9.1. À quoi sert ?](#91-à-quoi-sert-)
  - [9.2. Syntaxe](#92-syntaxe-)
  - [9.3. Cas d’utilisation](#93-cas-dutilisation-)
  - [9.4. Options utiles](#94-options-utiles)
  - [9.5. Exemples pratiques](#95-exemples-pratiques-)
- [**10. La commande delgroup**](#10-delgroup)
  - [10.1. À quoi sert ?](#101-à-quoi-sert-)
  - [10.2. Syntaxe](#102-syntaxe-)
  - [10.3. Cas d’utilisation](#103-cas-dutilisation-)
  - [10.4. Options utiles](#104-options-utiles)
  - [10.5. Exemples pratiques](#105-exemples-pratiques-)
- [**11. La commande whoami**](#11-whoami)
  - [11.1. À quoi sert ?](#111-à-quoi-sert-)
  - [11.2. Syntaxe](#112-syntaxe-)
  - [11.3. Cas d’utilisation](#113-cas-dutilisation-)
  - [11.4. Options utiles](#114-options-utiles)

<br>
<br>



<br>
<br>


## **1. <code>chmod</code> :**

### **1.1. À quoi sert ?**

La commande <code>chmod</code> (Change Mode) sert à modifier les permissions d’accès d’un fichier ou d’un dossier dans Linux.
Ces permissions concernent qui peut lire, écrire ou exécuter un fichier.

En Linux, chaque fichier/dossier a trois types de permissions :

- <code>r</code> (read) → lecture

- <code>w</code> (write) → écriture

- <code>x</code> (execute) → exécution

Et elles s’appliquent à trois catégories d’utilisateurs :

- <code>u</code> (user) → le propriétaire du fichier

- <code>g</code> (group) → le groupe du fichier

- <code>o</code> (others) → tous les autres

- <code>a</code> (all) → tout le monde (u+g+o)



### **1.2. Syntaxe :**

La syntaxe générale est :

```bash
chmod [options] mode fichier
```
Deux façons de définir le mode :

**A. Notation symbolique (avec ``u``, ``g``, ``o``, ``a``, et ``+``, ``-``, ``=``) :**

```bash
chmod u+x fichier.txt     # ajoute le droit d'exécution au propriétaire
chmod g-w fichier.txt     # enlève le droit d'écriture au groupe
chmod o=r fichier.txt     # donne seulement le droit de lecture aux autres
```

**B. Notation numérique (octale) :**

Chaque permission correspond à un chiffre binaire transformé en octal : <code>r = 4</code>, <code>w = 2</code>, <code>x = 1</code>

Exemple :

- ``7 = 4+2+1`` → lecture + écriture + exécution

- ``6 = 4+2`` → lecture + écriture

- ``5 = 4+1`` → lecture + exécution

Structure : 

```bash
chmod XYZ fichier
```
- ``X`` = droits du propriétaire (``u``)

- ``Y`` = droits du groupe (``g``)

- ``Z`` = droits des autres (``o``)

Exemple :

```bash
chmod 755 script.sh
```

- propriétaire : lecture, écriture, exécution
- groupe et autres : lecture, exécution uniquement.

### **1.3. Options utiles :**

- ``-R`` : appliquer les permissions de manière récursive (dans tous les sous-dossiers et fichiers).

```bash
chmod -R 755 /var/www
```

- ``-c`` : afficher seulement les fichiers dont les permissions ont changé.

- ``-v`` : mode verbeux (affiche les changements effectués).

- ``--reference=fichier`` : appliquer les mêmes permissions qu’un autre fichier.

<br>
<br>

-----------------------------------------------------

<br>
<br>


## **2. ``chown`` :**

### **2.1. À quoi sert ``chown`` ?**

La commande ``chown`` (Change Owner) sert à changer le propriétaire et/ou le groupe d’un fichier ou d’un répertoire.

En Linux, chaque fichier/dossier a :

- un propriétaire (``user``) → celui qui l’a créé par défaut.

- un groupe (``group``) → ensemble d’utilisateurs pouvant avoir certains droits dessus.

Exemple : 

- si tu veux qu’un fichier appartienne à un autre utilisateur ou groupe, tu utilises chown.

### **2.2. Syntaxe de ``chown`` :**

```bash
chown [options] nouveau_propriétaire[:nouveau_groupe] fichier
```

- ``nouveau_propriétaire`` → l’utilisateur qui devient propriétaire.

- ``nouveau_groupe (optionnel)`` → le groupe qui devient associé au fichier.

- ``fichier`` → le fichier ou dossier concerné.


### **2.3. Options utiles :**

- ``-R`` : appliquer le changement de propriétaire/groupe de manière récursive (dans tous les sous-dossiers et fichiers).
```bash
chown -R root:root /var/www
```

- ``-c`` : afficher seulement les fichiers modifiés.

- ``-v`` : afficher un message détaillé pour chaque fichier traité.

- ``--reference=fichier_ref`` : appliquer le même propriétaire et groupe qu’un fichier existant.

```bash
chown --reference=ancien.txt nouveau.txt
```

<br>
<br>

-----------------------------------------------------

<br>
<br>


## **3. ``sudo``:**

### **3.1. À quoi sert ``sudo`` ?**

La commande ``sudo`` (superuser do) permet à un utilisateur d’exécuter une commande avec les privilèges d’un autre utilisateur, généralement l’administrateur (root).

En résumé : ``sudo`` donne temporairement des droits d’administration pour exécuter des actions qui nécessitent plus de permissions (installation de logiciels, modification de fichiers système, gestion des utilisateurs, etc.).

### **3.2. Syntaxe de ``sudo`` :**

```bash
sudo [options] commande
```

- ``commande`` → la commande que tu veux exécuter avec des privilèges élevés.

- ``options`` → permettent de contrôler le comportement de sudo.

### **3.3. Cas d’utilisation :**

- Installer un logiciel :

```bash
sudo apt install nginx
```

- Modifier un fichier système avec un éditeur :

```bash
sudo nano /etc/hosts
```

- Redémarrer le système :

```bash
sudo reboot
```

- Lancer une commande en tant qu’un autre utilisateur (exemple : user1) :

```bash
sudo -u user1 commande
```

### **3.4. Options utiles :**

- ``-l`` : liste les droits de sudo de l’utilisateur courant.

```bash
sudo -l
```

- ``-u`` utilisateur : exécuter une commande en tant qu’un autre utilisateur (par défaut = root).

```bash
sudo -u www-data ls /var/www
```

- ``-k`` : force la demande du mot de passe la prochaine fois que sudo est utilisé.

- ``-s`` : ouvrir un shell avec les privilèges root.

```bash
sudo -s
```

- ``-i`` : ouvre une session de connexion complète en tant que root (comme si on se connectait directement).

```bash
sudo -i
```

### **3.5. Exemples pratiques :**
```bash
sudo apt update                  # mise à jour des dépôts
sudo systemctl restart apache2   # redémarrer un service
sudo chown root:root fichier.txt # changer propriétaire vers root
sudo rm fichier_protege.txt      # supprimer un fichier protégé
sudo -u abdelhafid ls /home      # exécuter en tant qu’un autre utilisateur
```

### **3.6. Points importants à retenir :**

- ``sudo`` demande le mot de passe de l’utilisateur courant (pas celui de root directement).

- Les permissions de ``sudo`` sont définies dans le fichier ``/etc/sudoers``.

- Tous les utilisateurs n’ont pas accès à ``sudo`` (il faut être dans le groupe sudo).


<br>
<br>

-----------------------------------------------------

<br>
<br>


## **4. ``su``:**

### **4.1. À quoi sert ``su`` ?**

La commande ``su`` (substitute user ou switch user) permet de changer d’utilisateur dans le terminal.

Par défaut, sans argument, ``su`` permet de passer à l’utilisateur ``root`` (administrateur) si tu connais son mot de passe.

Avec un argument, ``su`` permet de passer à un autre utilisateur spécifique.

### **4.2. Différence avec ``sudo`` :**

- ``su`` → tu bascules dans la session d’un autre utilisateur (tu deviens cet utilisateur).

- ``sudo`` → tu exécutes une seule commande avec des privilèges élevés (sans changer d’utilisateur de façon permanente).

### **4.3. Syntaxe de ``su`` :**

```bash
su [options] [nom_utilisateur]
```

- ``nom_utilisateur`` → l’utilisateur dans lequel tu veux basculer.

Si tu ne mets rien, ça passe par défaut en root.

### **4.4. Cas d’utilisation :**

- Passer en root (administrateur) :

```bash
su
```

➝ demande le mot de passe root.

- Passer à un autre utilisateur (exemple : abdelhafid) :

```bash
su abdelhafid
```

➝ demande le mot de passe de abdelhafid.

- Ouvrir une session root avec son environnement complet (comme une vraie connexion root) :

```bash
su -
```

### **4.5. Options utiles :**

- (ou ``-l``) : ouvre une session de connexion complète (charge l’environnement de l’utilisateur).

```bash
su - root
```

- ``-c`` "commande" : exécuter une commande en tant qu’un autre utilisateur, puis revenir à l’utilisateur courant.

```bash
su -c "ls /root" root
```

- ``-s`` shell : lancer un shell spécifique avec l’utilisateur choisi.

```bash
su -s /bin/bash user1
```

### 4.6. Exemples pratiques :
```bash
su                        # passer en root
su -                      # passer en root avec environnement complet
su abdelhafid             # se connecter en tant qu’abdelhafid
su -c "apt update" root   # exécuter une commande unique en root
su -s /bin/sh user1       # ouvrir un shell spécifique pour user1
```

### **4.7. Points importants :**

- ``su`` demande le mot de passe du compte cible (contrairement à sudo qui demande ton propre mot de passe).

- Dans beaucoup de distributions modernes (comme Ubuntu), ``su`` n’est pas utilisé par défaut car le compte root est désactivé (on utilise plutôt sudo).

- ``su -`` est plus sûr que su car il charge aussi l’environnement de l’utilisateur (variables, PATH, etc.).

<br>
<br>

-----------------------------------------------------

<br>
<br>

## **5. ``passwd`` :**

### **5.1. À quoi sert ``passwd`` ?**

La commande ``passwd`` permet de changer le mot de passe d’un utilisateur dans Linux.

- Sans argument → l’utilisateur change son propre mot de passe.

- Avec un nom d’utilisateur (et les droits administrateur) → l’administrateur change le mot de passe d’un autre utilisateur.

C’est une commande très importante pour la sécurité des comptes.

### **5.2. Syntaxe de ``passwd`` :**

```bash
passwd [options] [nom_utilisateur]
```

- ``nom_utilisateur`` → facultatif. Si omis, c’est ton propre mot de passe qui est modifié.

- ``options`` → permettent d’avoir plus de contrôle (expiration, blocage, etc.).

### **5.3. Cas d’utilisation :**

- Changer ton propre mot de passe :

```bash
passwd
```
➝ le système te demande ton ancien mot de passe puis le nouveau (deux fois).

- L’administrateur change le mot de passe d’un autre utilisateur (exemple abdelhafid) :

```bash
sudo passwd abdelhafid
```

➝ permet de définir un nouveau mot de passe pour abdelhafid.

- Forcer un utilisateur à changer son mot de passe à la prochaine connexion :

```bash
sudo passwd -e etudiant
```

### **5.4. Options utiles :**

- ``-d`` : supprime le mot de passe de l’utilisateur (compte sans mot de passe).

```bash
sudo passwd -d user1
```

- ``-l`` : verrouille le mot de passe d’un utilisateur (il ne peut plus se connecter).

```bash
sudo passwd -l user1
```

- ``-u`` : déverrouille un mot de passe verrouillé.

```bash
sudo passwd -u user1
```

- ``-e`` : force l’expiration immédiate du mot de passe → l’utilisateur doit en choisir un nouveau à la prochaine connexion.

```bash
sudo passwd -e user1
```

- ``-S`` : affiche l’état du mot de passe de l’utilisateur.

```bash
sudo passwd -S user1
```

### **5.5. Exemples pratiques :**

```bash
passwd                    # changer ton propre mot de passe
sudo passwd abdelhafid    # admin change le mot de passe d’un utilisateur
sudo passwd -l etudiant   # verrouiller le compte d’un utilisateur
sudo passwd -u etudiant   # déverrouiller le compte d’un utilisateur
sudo passwd -e user1      # forcer user1 à changer son mot de passe
sudo passwd -S user1      # vérifier l’état du mot de passe d’un utilisateur
```

<br>
<br>

-----------------------------------------------------

<br>
<br>

## **6. ``adduser`` :**

### **6.1. À quoi sert ?**

``adduser`` permet de créer un nouvel utilisateur sur le système Linux.

Elle configure automatiquement :

- Le compte de l’utilisateur.

- Son répertoire personnel (/home/nom_utilisateur).

- Son shell par défaut (/bin/bash en général).

- Son appartenance à des groupes.

- La demande de mot de passe.

C’est une commande plus conviviale que ``useradd`` (plus bas niveau).

### **6.2. Syntaxe :**

```bash
sudo adduser [options] nom_utilisateur
```

### **6.3. Cas d’utilisation :**

- Créer un nouvel utilisateur :

```bash
sudo adduser abdelhafid
```

➝ crée le compte abdelhafid, son dossier /home/abdelhafid, et demande un mot de passe.

- Ajouter un utilisateur dans un groupe existant :

```bash
sudo adduser abdelhafid sudo
```

➝ ajoute abdelhafid au groupe sudo (droits admin).

### **6.4. Options utiles :**

- ``--home /chemin`` : définir un répertoire personnel différent.

```bash
sudo adduser --home /opt/user1 user1
```

- ``--shell /bin/zsh`` : définir un shell par défaut différent.

```bash
sudo adduser --shell /bin/zsh devuser
```

- ``--disabled-password`` : créer un compte sans mot de passe (accès uniquement via SSH ou sudo).

- ``--ingroup groupe`` : associer directement à un groupe.

### **6.5. Exemples pratiques :**
```bash
sudo adduser testuser               # crée un nouvel utilisateur
sudo adduser testuser sudo          # ajoute testuser au groupe sudo
sudo adduser --shell /bin/sh dev    # utilisateur avec shell différent
sudo adduser --home /data/userX uX  # utilisateur avec home personnalisé
```

<br>
<br>

-----------------------------------------------------

<br>
<br>

## **7. ``deluser`` :**

### **7.1. À quoi sert ?**

``deluser`` sert à supprimer un utilisateur du système Linux.

Contrairement à ``userdel``, elle est plus conviviale et offre plus d’options simples (comme la suppression de son dossier personnel en même temps).

### **7.2. Syntaxe :**

```bash
sudo deluser [options] nom_utilisateur
```

### **7.3. Cas d’utilisation :**

- Supprimer un utilisateur sans supprimer son dossier /home :

```bash
sudo deluser testuser
```

- Supprimer un utilisateur et son répertoire personnel :

```bash
sudo deluser --remove-home testuser
```

- Supprimer un utilisateur d’un groupe (sans le supprimer complètement) :

```bash
sudo deluser testuser sudo
```

### **7.4. Options utiles :**

- ``--remove-home`` : supprime aussi le répertoire personnel de l’utilisateur.

- ``--remove-all-files`` : supprime tous les fichiers appartenant à l’utilisateur sur tout le système.

- ``--backup`` : crée une sauvegarde des fichiers de l’utilisateur avant suppression.

### **7.5. Exemples pratiques :** 

```bash
sudo deluser user1                  # supprime l’utilisateur (mais garde /home/user1)
sudo deluser --remove-home user1    # supprime l’utilisateur + son home
sudo deluser --remove-all-files uX  # supprime tous ses fichiers
sudo deluser user1 sudo             # retire user1 du groupe sudo
```

<br>
<br>

-----------------------------------------------------

<br>
<br>

## **8. ``groups`` :**

### **8.1. À quoi sert ?**

La commande ``groups`` permet de voir à quels groupes un utilisateur appartient dans Linux.

- Chaque utilisateur peut appartenir à plusieurs groupes.

- Les groupes servent à gérer les permissions d’accès aux fichiers, dossiers et ressources.

- C’est très utile pour vérifier si un utilisateur a accès à certaines fonctions ou fichiers via ses groupes.

### **8.2. Syntaxe :**

```bash
groups [nom_utilisateur]
```

- ``nom_utilisateur`` → optionnel.

Si tu ne le précises pas, la commande montre les groupes de l’utilisateur courant.

Sinon, elle montre les groupes de l’utilisateur indiqué.

### **8.3. Cas d’utilisation :**

- Voir tes propres groupes :

```bash
groups
```

- Voir les groupes d’un autre utilisateur (exemple abdelhafid) :

```bash
groups abdelhafid
```

- Vérifier si un utilisateur est dans le groupe sudo :

```bash
groups abdelhafid | grep sudo
```

### **8.4. Options utiles :**

- ``-q`` : affichage rapide, seulement les noms des groupes.

- ``--help`` : afficher l’aide de la commande.

Exemple :

```bash
groups -q abdelhafid
```

### **8.5. Exemples pratiques :**

```bash
groups                     # affiche les groupes de l’utilisateur courant
groups root                # affiche les groupes de l’utilisateur root
groups abdelhafid          # affiche tous les groupes de abdelhafid
groups | grep sudo
```

<br>
<br>

-----------------------------------------------------------

<br>
<br>

## **9. ``addgroup`` :**

### **9.1. À quoi sert ?**

``addgroup`` permet de créer un nouveau groupe sur le système Linux.

- Les groupes servent à regrouper plusieurs utilisateurs pour leur donner des permissions collectives.

- Utile pour gérer l’accès à des fichiers, dossiers ou services pour un ensemble d’utilisateurs.

### **9.2. Syntaxe :**

```bash
sudo addgroup [options] nom_du_groupe
```

### **9.3. Cas d’utilisation :**

- Créer un nouveau groupe :

```bash
sudo addgroup developpeurs
```

➝ crée le groupe developpeurs.

- Créer un groupe avec un GID spécifique :

```bash
sudo addgroup --gid 1050 testgroup
```

➝ testgroup aura l’ID 1050 au lieu d’un ID attribué automatiquement.

### **9.4. Options utiles :**

- ``--gid GID`` : spécifier un ID pour le groupe.

- ``--system`` : créer un groupe système (pour les services, pas pour les utilisateurs normaux).

### **9.5. Exemples pratiques :**

```bash
sudo addgroup marketing        # créer un groupe classique
sudo addgroup --gid 2000 ventes # créer un groupe avec un GID spécifique
sudo addgroup --system docker   # créer un groupe système pour le service docker
```

<br>
<br>

-----------------------------------------------------------

<br>
<br>

## **10. ``delgroup`` :**

### **10.1. À quoi sert ?**

``delgroup`` permet de supprimer un groupe existant sur le système Linux.

- Utile pour nettoyer les groupes inutilisés ou obsolètes.

- Ne supprime pas les utilisateurs associés, juste le groupe.

### **10.2. Syntaxe :**

```bash
sudo delgroup [options] nom_du_groupe
```

### **10.3. Cas d’utilisation :**

- Supprimer un groupe :

```bash
sudo delgroup developpeurs
```

➝ supprime le groupe developpeurs.

- Supprimer un groupe système :

```bash
sudo delgroup --system docker
```

### **10.4. Options utiles :**

- ``--system`` : supprimer un groupe système.

- ``--backup`` : crée une sauvegarde de la configuration avant suppression (selon distribution).

### **10.5. Exemples pratiques :**

```bash
sudo delgroup marketing       # supprime le groupe marketing
sudo delgroup --system docker # supprime le groupe système docker
```

<br>
<br>

-----------------------------------------------------------

<br>
<br>

## **11. ``whoami`` :**

### **11.1. À quoi sert ?**

La commande ``whoami`` permet de connaître l’utilisateur courant avec lequel tu es connecté dans le terminal.

- Très utile pour vérifier sous quel compte tu exécutes des commandes, surtout quand tu utilises sudo ou su.

- Simple et directe : elle retourne juste le nom de l’utilisateur actif.

### **11.2. Syntaxe :**

```bash
whoami
```

- aucun argument n’est nécessaire.

- Elle peut être combinée avec d’autres commandes si besoin.

### **11.3. Cas d’utilisation :**

- Vérifier ton utilisateur courant :

```bash
whoami
```
Exemple de sortie :

```bash
abdelhafid
```

- Vérifier l’utilisateur après un su ou sudo -u :

```bash
sudo -u root whoami
```

Sortie :

```bash
root
```

- Combiner avec echo pour un message personnalisé :

```bash
echo "Vous êtes connecté en tant que $(whoami)"
```

### **11.4. Options utiles :**

whoami est très simple et n’a pas beaucoup d’options, mais quelques options standards :

- ``--help`` : afficher l’aide de la commande.

- ``--version`` : afficher la version du programme.

### **11.5. Exemples pratiques :**

```bash
whoami                       # affiche l’utilisateur courant
sudo -u root whoami           # affiche root si on exécute en tant que root
echo "Utilisateur: $(whoami)" # afficher un message avec l’utilisateur
```

<br>
<br>

-----------------------------------------------------------

<br>
<br>

# <center>**Correction du Challenge 2**</center>

### **Créer la structure des dossiers :**

```bash
mkdir -p "user backup"/{important,temporaire,rapport}
```

``mkdir -p`` crée les dossiers parent et enfants en une seule commande.

### **1. Créer les fichiers dans user backup :**

```bash
cd "user backup"
touch todo.txt note1.txt brouillon.txt test1.log test2.log
```

``touch`` crée des fichiers vides.

### **2. Déplacer todo.txt et note1.txt vers important :**

```bash
mv todo.txt note1.txt important/
```

### **3. Déplacer brouillon.txt, test1.log, test2.log vers temporaire :**

```bash
mv brouillon.txt test1.log test2.log temporaire/
```

### **4. Copier todo.txt vers rapport sous le nom todo_backup.txt :**

```bash
cp important/todo.txt rapport/todo_backup.txt
```
### **5. Concaténer todo.txt et note1.txt dans rapport/synthese.txt :**

```bash
cat important/todo.txt important/note1.txt > rapport/synthese.txt
```

### **6. Afficher le début de synthese.txt (10 premières lignes) :**

```bash
head -n 10 rapport/synthese.txt
```

### **7. Supprimer tous les fichiers .log dans temporaire :**

```bash
rm temporaire/*.log
```

### **8. Supprimer le dossier temporaire complètement après nettoyage :**

```bash
rmdir temporaire
```

ou si le dossier n’est pas vide : 

```bash
rm -r temporaire
```

### **9. Afficher le chemin absolu de user backup :**
```bash
pwd
```

Assurez d’être dans le dossier parent de user backup pour obtenir le chemin complet.

### **10. Lister tout le contenu restant avec arborescence :**

```bash
tree "user backup"
```

Si ``tree`` n’est pas installé : sudo apt install tree (Ubuntu/Debian)

### **11. Compresser le dossier important dans important_backup.zip :**

```bash
zip -r important_backup.zip important/
```

``-r`` pour récursif (tous les fichiers du dossier)

### **12. Créer un dossier restore/ et extraire l’archive dedans :**

```bash
mkdir restore
unzip important_backup.zip -d restore/
```

Vérifie que le dossier important est bien restauré dans restore/.


<br>
<br>

-----------------------------------------------------------

<br>
<br>

# <center>**Correction du Challenge 3 :**</center>

### **1. Vérifier les permissions actuelles du dossier user backup :**

```bash
ls -ld "user backup"
```

``-l`` : détails, ``-d`` : uniquement le dossier lui-même

### **2. Changer les permissions de rapport/ pour qu’il soit accessible uniquement par toi :**

```bash
chmod 700 rapport
```

- ``7`` = lecture, écriture, exécution pour le propriétaire

- ``0`` = aucun droit pour le groupe et les autres

### **3. Changer les permissions de synthese.txt pour qu’il soit lisible mais non modifiable par les autres :**

```bash
chmod 644 rapport/synthese.txt
```

- Propriétaire : lecture + écriture ``(6)``

- Groupe : lecture ``(4)``

- Autres : lecture ``(4)``

### **4. Créer un utilisateur (ex : collaborateur) :**

```bash
sudo adduser collaborateur
```

Le système demandera mot de passe et informations de l’utilisateur.

### **5. Créer un groupe (ex : equipe-projet) et ajouter l’utilisateur dedans :**

```bash
sudo addgroup equipe-projet
sudo adduser collaborateur equipe-projet
```

L’utilisateur collaborateur appartient maintenant au groupe equipe-projet.

### **6. Changer le propriétaire du dossier important/ vers l’utilisateur créé :**

```bash
sudo chown collaborateur: important
```

- Le dossier important appartient maintenant à collaborateur

- Le groupe reste inchangé (: sans groupe garde le groupe actuel).

### **7. Afficher les groupes auxquels tu appartiens :**

```bash
groups
```

Affiche tous les groupes dont l’utilisateur courant fait partie
