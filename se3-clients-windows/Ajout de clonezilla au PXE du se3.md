
# Ajout de clonezilla au PXE du se3. Utilisation en clonage, sauvegarde, restauration

**Clonezilla est un Logiciel opensource permettant de faire/restaurer des images de disques, de partitions. 
Ces images peuvent être stockées localement sur une partition, un disque dur externe ou tout simplement sur 
le se3 par connexion ssh.**

Une connexion en ssh sur le serveur se3 se fera par défaut dans le répertoire /home/partimag/

Il peut être judicieux de rajouter un disque dur interne sur le se3. Ce disque sera monté de façon permanente en /home/partimag.
Il pourrait contenir des images de chaque type de PC, des partitions spécifiques à des pc d’une salle si des logiciels spécifiques ne peuvent être déployées par WPKG.

Un disque dur séparé n’est pas obligatoire mais permettra de faire des clonages sans que l’activité du serveur ne s’en trouve diminuée. Le format peut-être en ext3,ntfs, fat32 ou autre puisque les images générées sont découpées en fichiers de taille inférieure à 2 G0.

Clonezilla permet aussi de copier une image de partition vers une autre partition locale, servant ainsi de sauvegarde à la première, comme le fait le module du se3.

Le but est de pouvoir démarrer Clonezilla sur le poste client directement en PXE en vue de le restaurer/creer une image du poste, ou tout simplement faire une sauvegarde/restauration de partitions.

## Première partie : installation de clonezilla sur le serveur.

Les images au format ZIP de clonezilla peuvent être téléchargées aux adresses suivantes :

[http://downloads.sourceforge.net/project/clonezilla/clonezilla_live_stable/2.1.2-43/clonezilla-live-2.1.2-43-i686-pae.zip](http://downloads.sourceforge.net/project/clonezilla/clonezilla_live_stable/2.1.2-43/clonezilla-live-2.1.2-43-i686-pae.zip)

http://downloads.sourceforge.net/project/clonezilla/clonezilla_live_stable/2.1.2-43/clonezilla-live-2.1.2-43-i486.zip

http://downloads.sourceforge.net/project/clonezilla/clonezilla_live_stable/2.1.2-43/clonezilla-live-2.1.2-43-amd64.zip

Version alternative basée sur Ubuntu raring (utilisée sur mon se3)

http://downloads.sourceforge.net/project/clonezilla/clonezilla_live_alternative/20130819-raring/clonezilla-live-20130819-raring-i386.zip

**Remarque** : Je n’ai testé que la version "raring" dans mon établissement. Les autres sont peut-être plus ou moins performantes ou reconnues.

En cas de maj, les liens ne seront plus valides, mais les archives pourront être téléchargées ici :

http://clonezilla.org/downloads/download.php?branch=stable

Ouvrir une session root au choix sur le serveur, sur un poste client Windows avec Putty ou plus simplement une connexion en ssh avec un client linux (qui va rendre le copier coller des lignes suivantes bien plus pratique...)

Depuis le client linux


```sh
# ssh -22 root@ipduse3
```