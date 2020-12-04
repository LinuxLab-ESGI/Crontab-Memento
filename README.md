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

Vous pouvez également lister la liste de vos taches programmées de l'utilisateur courant avec la commande : 
```
crontab -l
```

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

Imaginez un tableau Excel dans laquelle vous ajouter des ligne dans celui-ci. Crontab c'est sensiblement la même chose. Chaque colonne correspond à une information bien spécifique :

- Le "<b>m</b>" étant la minute précise à laquelle la commande sera exécuté (par exemple la 24ème à une heure du matin).
- Le "<b>h</b>" étant l'heure de la journée (en format 24h).
- Le "<b>dom</b>" pour Day Of The Month étant le jour du moins.
- Le "<b>mon</b>" quant à lui fait référence au mois de l'année (de 1 à 12).
- Le "<b>dow</b>" pour Day Of The Week correspond au jour de la semaine de 0 à 6. 0 étant le dimanche et samedi le 6.
- Puis la colonne "<b>command</b>", étant la commande que vous souhaitez exécuter. Plutôt logique !

Faites donc attention d'avoir au moins 5 espaces dans votre ligne pour renseigner chacune des colonnes du "tableau". Si vous ne souhaitez pas prendre en compte un des critères de planification de l'évènement, vous pouvez mettre une "*" à la place de la valeur.

Par exemple pour exécuter une commande toutes les heures à la 4ème minute le lundi on entrera :
```
04 * * * 1 <commande>
```

Pour en exécuter une autre toutes les minutes du mois de janvier : 
```
* * * 1 4 <commande>
```


## IV - Alias

Pour éviter de se poser la question de ce qu'on doit renseigner comme valeur dans chacun des colonnes précédant la commande, il existe certains alias qui permettent de nous simplifier la vie ! C'est alias se notent <b>@alias</b> juste avant la commande comme ceci :

```
@weekly <commande>
```

Voici la liste des alias courant qui existent sur Crontab avec leur équivalent :

Alias | Description | Équivalent |
--- | --- | --- |
@yearly / @annually| Tous les ans | 0 0 1 1 * |
@monthly | Tous les mois | 0 0 1 * * |
@weekly | Toutes les semaines | 0 0 * * 0 |
@daily / @midnight | Tous les jours | 0 0 * * * |
@hourly | Toutes les heures | 0 * * * * |

Enfin, il existe un alias q(ui n'en est pas vraiment un finalement) faisant référence au démarrage de la machine : <b>@reboot</b>.
______________________________
<i>Écrit par Xen0rInspire.</i>