Paulus Alois

-----------------------
Projet Unix 2013-2014 |
-----------------------

1) Analyse des packets R 
_________________________

1.1) Utilisation du script
---------------------

./rextrat.sh -d pathToFolder

ou bien pour obtenir de l'aide

./rextrat.sh -h

1.2) Les arguments
---------------------

- L: Ignore les liens symboliques 
- p: Affiche le contenu du fichier package.csv
- c: Supprime tous les fichiers généré par le script
- r: Active la recherche de packet R dans un packet R
- d path: Donne le chemin du dossier à examiner

1.3) Structure du script
---------------------

Mon script est composé de plusieurs fonctions génériques pour éviter de devoir maintenir trop de ligne de code. De plus débugger en bash n'est pas facile donc il est préférable d'avoir des petites fonctions plus ou moins faciles à vérifier.

Chaque fonction est documentée dans le script, je ne les ai donc pas reprises dans le rapport.

Pour ce script comme pour le suivant, j'ai beaucoup employé les tableaux. Car ils m'ont permis de stocker facilement des données et aussi de créer des fonctions génériques, par exemple : la liste des dossiers et des fichiers obligatoires.

La commande "find" m'a été très utile pour chercher des fichiers ou des dossiers répondant à certaines conditions. J'ai égalemment employé les expressions régulière pour chercher les fichiers d'un type spécifique.

La structuture générale du script correspond à :

1) Récupérer tous les dossiers contenant les fichiers obligatoires dans le dossier donné en paramètre.
(Attention si paramètre -r, on cherche dans tous les descendant sinon on cherche uniquement dans les descendant direct du dossier)

2) Pour chaque dossier :
    - Vérifier si c'est un packet R: si il a des folders optionnels ils ne sont pas vide ...
    - Si oui, traiter ce dossier: compter le nombre de fichiers R, le nombres de fichiers sources, écritures dans les différents fichiers.
    - Si non/oui (dependant du paramètre -r) rechercher si il contient des packets R
3) Fin


2) Suite de Syracuse
_____________________


1.1) Utilisation du script
--------------------------

./syracuseGen.sh n


1.2) SyracuseGen.sh
---------------------

Ce script appelle le script syracuse.sh pour obtenir la suite de syracuse pour chaque nombre contenu entre 1 et n. 
Ensuite il génère les graphiques grâce l'outil DOT pour chacune de ces suites.


1.3) Syracuse.sh
---------------------

Il prend en paramètre un entier strictement positif et génère en language DOT le graphe d'écrivant les vols de Syracuse pour les suites partant des entiers de 1 à n (n'étant le paramètre).

Pour cela j'ai employé un tableau de tableau. Pour chaque nombre je stocke un tableau de nombre contenant sa suite de Syracuse.
Ensuite je parcours ce tableau de tableau pour générer le fichier DOT. 

Le graphique DOT est généré avec le l'option "strict" qui permet d'afficher plusieurs arrêtes en une seule.

3) Outils et commandes découverts
___________________________________

- getopts : j'ai employé cet outil pour gérer les options du script d'analyse des packets R. Il m'a été très utile pour gérer les options multiples, non ordonnées et avec arguments.

getops prend en paramètre les options attendues ainsi que si l'on désire, leurs arguments.

Example : getopts "a" attends l'option -a
          getopts "a:" attends l'option -a avec un argument
          getopts "abc" attends l'option -a ou -b ou -c ou bien une combinaison de ces options.

- xargs : j'ai employé cette commande pour compter le nombre de ligne total d'une liste de fichier.

xargs est une commande qui permet de lire des éléments d'un pipe (ici le résultat du find) délimité par des blanc ou des nouvelles lignes et exécute une commande pour chacun de ces éléments.

4) Bibliographie
------------------

http://cran.r-project.org/doc/manuals/r-release/R-exts.html#Package-structure
http://askubuntu.com/
http://stackoverflow.com/
http://content.hccfl.edu/pollock/unix/findcmd.htm
http://www.cyberciti.biz/faq/linux-unix-bsd-xargs-construct-argument-lists-utility/

