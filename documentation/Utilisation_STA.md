#**Guide d'utilisation des Stratégies, Tactiques et Actions**
*Ou comment faire bouger les robots plus ou moins comme on veut*

##**Introduction**
Les STA sont situées dans le dossier StrategyIA/ai/STA.
Ce dossier est séparé en trois sous-dossiers qui illustrent une séparation conceptuelle importante:
- Les **actions**, qui retournent un object AICommand et qui correspondent donc à des comportements très courts que l'on peut effectuer à répétitions, tels des déplacements.
- Les **tactiques**, implémentées comme des machines à états qui contiennent des états en fonction de leur avancement. Chaque état retourne une action, et donc une AICommand, jusqu'à la fin de l'exécution de la tactique.
- Les **stratégies**, implémentées comme un graphe dont chaque noeud est une tactique et chaque arète, une condition. Ce graphe a comme nombre d'enfants au deuxième niveau le nombre de robot, car chaque robot correspond à un sous-arbre.

Ainsi, les **stratégies** contiennent des **tactiques** qui contiennent des **actions**.

###**Quelques actions:**
- GetBall: déplace le robot vers la balle
- MoveToPosition: déplace le robot vers une position donnée
- Kick: on ne bouge pas, mais on active le kicker. Attention les doigts!
- GoBehind: permet d'aller derrière la balle en fonction d'un point donné (viser ce point avec la balle)
- ProtectGoal: place un robot (le gardien de préférence!) entre le but et la balle, très près du but 

*La création d'une commission spéciale à l'Assemblée nationale est envisagée pour légiférer sur le statut de certaines actions qui devraient peut-être être des tactiques.*

###**Quelques tactiques:**
- GoGetBall: renvoie GetBall jusqu'à ce qu'on soit rendu à la balle
- GoToPosition: renvoie MoveToPosition jusqu'à ce qu'on soit rendu à la position donnée
- ShootGoal: vérifie si le robot est bien orienté puis renvoie l'action Kick
- ReceiveBall: oriente le robot vers la balle, puis renvoie l'action Idle (ne rien faire) pour finalement indiquer le succès de la tactique si le robot reçoit la balle

*Les tactiques possèdent des Flags qui indiquent Success, Failed ou WIP (Work in progress) afin d'aider la stratégie à prendre des décisions.*

###**Quelques stratégies:**
- SimpleDefense: 1 gardien de but (T: ProtectGoal), 1 attaquant (T: GoGetBall) et 4 défenseurs avec chacun leur zone (T: ProtectZone). *Cette stratégie 
n'utilise pas notre nouvel objet Stratégie qui implémente le graphe mentionné plus haut et donc, elle n'est pas évolutive.*
- Diverses stratégies de test: C'est au niveau stratégique que l'on peut effectuer des tests. Voir la section **Les robots en action**.

La stratégie accorde à chaque robot une tactique qui variera en fonction des conditions que le robot remplira. 
Par exemple, la stratégie pourrait attribuer au robot la tactique d'aller chercher la balle (GoGetBall).
La condition pour passer à la prochaine stratégie pourrait être que le robot soit rendu à la balle, ce qui serait un 
cas simple qui ne nécessiterait pas l'emploi de notre graphe; en effet, il suffirait de vérifier que la tactique 1 est terminée avant d'accorder au robot la tactique 2.

Toutefois, cette condition pourrait être qu'un autre robot soit placé en position stratégique pour recevoir la balle. Ainsi, il faudra que notre premier robot patiente avant de la lui envoyer.
Cette nécessité de vérifier des conditions globales, et non centrées sur la tactique d'un seul robot, justifie l'utilisation de notre graphe.

##**Les robots en action**
Lorsque j'ai rejoint l'association, je n'arrivais pas à faire bouger les robots. Pour vous éviter cette grande tragédie, je propose de vous expliquer rapidement comment tester une stratégie.

Vous aurez besoin de 3 instances pour tester une stratégie:
- [main.py de StrategyIA](https://github.com/RoboCupULaval/StrategyIA) (qui roule l'IA et envoie les commandes à grSim)
- [grSim](https://github.com/RoboCupULaval/grSim) (pour voir les robots sur le terrain en 3D)
- [main.py de UI-Debug](https://github.com/RoboCupULaval/UI-Debug) (pour fixer manuellement la stratégie à l'équipe)

**To be continued**
