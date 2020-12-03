# Crontab - Memento
<i>Mini récap de ce merveilleux outil qu'est Crontab !</i>
__________

## I - Présentation

Crontab c'est quoi ? C'est tout simplement le planificateur d'évènements le plus utilisé dans les ditributions Linux du moment. Très souvent installé nativement dans la distribution, il permet de planifier l'exécution d'une commande à l'heure et à la fréquence que vous souhaitez. Si toutefois Crontab n'est pas installé par défaut, vous pouvez toujours le faire via la commande : 

```
apt install crontab -y
```
<i>Pour les distributions Debian ou</i>
```
yum install crontab -y
```
<i>Pour les distributions Redhat</i>

## II - Commandes usuelles

Pour ajouter une commande dans l'utilitaire Crontab tapez :
```
crontab -e
```

Cette commande aura pour effet d'ouvrir votre éditeur de texte favori et vous pourrez ainsi ajouter une tache planifiée dans le fichier.
Veillez cependant à avoir les droits pour exécuter cette commande avec l'utilisateur sur lequel vous avez entré la commande ci-dessus. En effet, si vous tenter d'accéder à des fichiers sur lesquels vous n'avez pas les droits en lecture par exemple, votre commande ne sera pas exécutée !

Si vous souhaitez exécuter cette commande avec l'utlisateur qui possède ces droits, vous avez le choix entre changer d'utilisateur manuellement et relancer la commande précédente ou de faire cette commande :

```
crontab -u <utilisateur> -e
```

Vous aurez cependant besoin d'ajouter un <b>sudo</b> devant la commande si vous voulez modifier le planificateur d'évènements du compte *root*.

<i><b>Remarque :</b> Pour toutes ces manipulations, je vous conseille de passer par l'éditeur Crontab plutôt que d'essayer de chercher le fichier de configuration manuellement sur la machine. De plus, ce dernier est suceptible de changer en fonction de la distribution Linux que vous utilisez.</i> 

## III - Formattage des commandes

En théorie voici ce que Crontab nous dis :
```
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
```
Mais avouez cependant qu'au premier abord c'est pas très intuitif...

## IV - Alias
`WIP...`