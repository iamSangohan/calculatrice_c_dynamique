# README "calculatrice_c_dynamique"

**I- Generalité sur les librairies**

Les librairies contiennent la definition de fonction susceptible d'etre utiliser par plusieurs programmes simultanement ou non. Il existe deux types de librairie : Les librairies statiques et dynamiques.

Le nom des librairies statiques est typiquement de la forme *libxxx.a*. Le nom des librairies dynamiques est de la forme *libxxx.so*.

Utiliser une librairie dynamique revient a indicer au programme d'ou il pourra charger en memoire ses definitions apres le lancement du programme.

<sub>Dans ce repo, nous allons créer et utiliser une librairie dynamique.</sub>


**II- Création de la librairie**

Pour generer la librairie dynamique lancer la commande suivante :
>gcc -o libcalculatrice.so -shared *.o (vous devez avoir les fichiers objets des fonctions)
Apres vous metter la nouvelle librairie dans le dossier "lib". Vous pourrez alors lancer l'executable avec la commande :
>gcc src/prog.c -L lib -I include -l calculatrice -o prog
Si vous lancez l'executable, il doit normalement avoir une erreur. Elle est dû au faite qu'avoir les librairies dynamiques, le systeme va chercher les fichiers dans un dossier special. Et vu que notre librairie n'y est pas, on doit indiquer au systeme qu'il doit aussi chercher dans notre dossier lib. Pour cela, on execute les commandes suivantes :
>echo $LD_LIBRARY_PATH (pour verifier que la variable est vide)
>export LD_LIBRARY_PATH=/chemin/vers/le/dossier/lib:$LD_LIBRARY_PATH
Le programme devrait s'executer sans probleme maintenant
**NB** = Au redemarrage du l'ordinateur, il faudrait refaire la config car c'est une variable temporaire.
http://perso.ens-lyon.fr/frederic.vivien/Enseignement/PPP-2001-2002/LibDyn.pdf
Vous pouvez utiliser ce lien qui explique un peu comment créer une librairie dynamique


**III- Notes importantes**

>Il faut include dans les fichiers sources, les .h dont on a besoin.

>L'argument -I include indique les .h se trouve dans le dossier include. -L lib lui indique que la librairie statique est dans le dossier lib.

>Plus besoin de mettre libcalculatrice. Juste calculatrice marche.
