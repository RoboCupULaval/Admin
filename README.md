[![Stories in Ready](https://badge.waffle.io/RoboCupULaval/Admin.png?label=ready&title=Ready)](https://waffle.io/RoboCupULaval/Admin)
# Admin
[![Throughput Graph](https://graphs.waffle.io/RoboCupULaval/Admin/throughput.svg)](https://waffle.io/RoboCupULaval/Admin/metrics/throughput)

Dépôts pour les tâches administratives de la partie intelligence artificielle de Robocup Ulaval.
Ce n'est pas le dépôt de l'administration de Robocup ULaval.

Ce dépôt contient:
  - Les résumés des différentes rencontres avec Beenox.
  - Les procès verbaux ainsi que les ordres du jour des différentes réunions de la team IA.
  - De la documentation

# Nomenclature des fichiers

Les dossiers « beenox » et « rencontres » on des fichiers canevas.tex avec le format souhaitée des documents.

Les fichiers ont comme titres la date de la réunion avec un préfixe définissant son contenu.
Les pocès verbaux ont comme préfixe « pv ».
Les ordres du jour ont comme préfixe « oj ».
Les rencontres  avec Beenox n'ont pas de préfixes.

# Nomenclature des branches

La branche _master_ représente une version stable du code.
Elle est garantie de rouler et d'implémenter la liste des fonctionalités
documentées.
Sur ce dépôt, elle est la seule branche pertinente.

La branche _dev_ représente les développements à jour et qui sont considérés
standardisés.
Ils peuvent potentiellement être instables et engendrer des conflits après des
ajouts majeurs.
Mais elle **devrait** fonctionner.

Pour les autres branches, les noms suivent le format _category/#-description_.

* feature : une branche qui développe une nouvelle fonctionalité
* merge : une branche qui sert à résoudre un merge complexe
* legacy : une branche active, mais dont les particularités sont dépréciées

_#_ est le numéro de la demande associée.
_description_ est une courte description séparée par tiret (**-**).

_e.g:_
* feature/28-pathfinder-rrt
* merge/32-rappatriement-sta
* legacy/gui-api-v0
