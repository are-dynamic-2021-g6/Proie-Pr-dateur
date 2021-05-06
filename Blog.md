# Blog

### Semaine 1
25 mars 2021

C'est avec ces idées en tête qu'on a commencé à chercher les méthodes utilisées pour modéliser le phénomène de prédation. Et sur Wikipedia on a découvert les fameuses équations de [Lotka-Volterra](https://fr.wikipedia.org/wiki/%C3%89quations_de_pr%C3%A9dation_de_Lotka-Volterra). C'est un couple d'équations différentielles qui prennent chacune en compte l'autre. C'est ce qui permet aux deux mondes d'évoluer interchangeablement, l'un en fonction de l'autre. Dont la forme la plus générale:

![Image](https://wikimedia.org/api/rest_v1/media/math/render/svg/022e443557bb93a3a04b3bac125daeddbeba5def)


Ensuite il nous fallait trouver un moyen pour convertir ces équations différentielles en code Python. Pour cela on a commencé à regarder des sites pour chercher une piste mais il y en avait plusieurs. Mais on a décidé laisser ça pour la prochaine fois et déjà finir le carnet de bord.


### Semaine 2
8 avril 2021

Cette semaine on attaque la programmation des équations différentielles. On effectue une recherche sur Internet et on tombe sur deux méthodes principales pour coder une équation différentielle sur Python. La première (comme [ici](https://scipy-cookbook.readthedocs.io/items/LoktaVolterraTutorial.html)) utilisait des fonctions déjà préparées (comme integrate.odeint) mais qui nécessitait une bonne manœuvre des outils de Matplotlib, ce qui n'était pas notre cas. On partit alors sur une deuxième voie plus classique qui consiste à boucler des simples soustractions pour la dérivation et fixer chaque paramètre comme une constante pour l'autre. Ensuite, on a comparé nos résultats à ceux obtenus par des modèles sur internet:

![Image](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Lotka-Volterra_orbits_02.svg/1280px-Lotka-Volterra_orbits_02.svg.png)


On s'est rendu compte que les paramètres initiaux étaient intrinsèquement liés et ne pouvaient pas être choisi au hasard au risque de l'extinction des proies suivie des prédateurs. Par exemple, si le taux de croissance des prédateurs était trop élevé face à celui des proies, la dynamique faisait faillite. On a donc déterminé une marge de valeurs qui marchaient propre à notre modèle.
