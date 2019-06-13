---
layout: post
comments: true
title: "01 - Installation de l'environnement de travail"
categories: post
author: "Benjamin Berhault"
lang: fr
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/anaconda.png' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">
    Le moyen le plus simple d'installer Python et Jupyter Notebook est probablement avec Anaconda.<br>
    <br>
    Anaconda est une ditribution libre et open source des langages de programmation Python et R particulièrement orientée pour des applications en data science. L'un des atouts majeurs d'Anaconda est sa simplification dans la gestion des packages et de leurs dépendances.
  </div>
</div>

#### Contenu de la page
<ul>
	<li>Installation de l'environnement de travail sous Windows
	<ul>
		<li>Installation de Python avec Anaconda</li>
		<li>Création d'un premier Jupiter Notebook</li>
		<li>Installation de packages Python
			<ul>
				<li>Installation de package avec conda (à privilégier)</li>
				<li>Installation de package avec pip</li>
				<li>Installation d'un package manuellement (en dernier recours)</li>
			</ul>
		</li>
		<li>Composer avec les contraintes de réseau d'entreprise
			<ul>
				<li>Installer un package Python avec pip sans accès à Internet ni autorisations d'administrateur</li>
				<li>Résoudre les problèmes de proxy pour Anaconda</li>
			</ul>
		</li>
	</ul>
	</li>
</ul>

Pour ceux bien décidés à utiliser R en lieu et place de Python : [Documentation Anaconda détaillant l'installation de R pour le Jupyter Notebook](https://docs.anaconda.com/anaconda/navigator/tutorials/r-lang/)

## Sous Windows - Installation de l'environnement de travail

### Installation de Python avec Anaconda

Téléchargez la version d'Anaconda supportant la dernière version de <b>Python 3</b> : [https://www.anaconda.com/download/#windows](https://www.anaconda.com/download/#windows)

Lancez et suivez les instructions de l'exécutable d'installation.

L'installation terminée, lancez la console anaconda via <b>menu Démarrer > Anaconda3 > Anaconda Prompt</b>.

<center><img src="{{ '/images/03-installation_environnement/01-installation_environnement.jpg' | relative_url }}"></center>

Créez un <b>conda environment</b> en Python 3.6. (pour plus d'information à se sujet consultez la [documentation concernant la gestion d'environnements](https://conda.io/docs/user-guide/tasks/manage-environments.html))
```console
conda create --name py36 python=3.6
```

<div class="card-panel teal lighten-4">Un conda environment est un répertoire contenant une collection spécifique de packages que vous aurez décidé d'installer. Certains packages ne supportant pas la dernière version de Python, il peut être pertinent de maintenir un environnement pour une version spécifique de Python. <br>
	<br>
	<b>La possibilité de créer un environnement avec Anaconda pour un package m'a posé certains problèmes, j'ai donc fini par utiliser l'environnement Python 3.7 installé par défaut.</b>
</div>
            
Pour activer votre environnement au sein de la console Anaconda, saisissez : 
```console
activate py36
```

Pour quitter votre environnement, il vous suffira de saisir :
```console
deactivate
```

Vérifiez votre version de Python au sein de cet environement :
```console
python --version
```
Si vous avez installez un environnement Python 3.6, au sein de ce dernier, il devrait vous être retourné : `Python 3.6.0`

<br>

### Création d'un premier Jupiter Notebook

<div class="row">
  <div class="col grid s12 m6 l6">
  	Le Jupyter Notebook est un outil web intéractif vous permettant de créer et de partager vos scripts de manipulation et d'analyse de la donnée, agrémentés d'explications et de vos résultats numériques ou visuels obtenus. <br>
  		<br>
    Au sein de la console Anaconda, naviguez au sein du répertoire de votre choix, par exemple : <br>
	<pre class="language-console"><code class="language-console">cd ./Documents/Python_notebooks</code></pre>
	<br>
	Lancez-y un Jupiter notebook<br>
	<pre class="language-console"><code class="language-console">Jupyter Notebook</code></pre>

  </div>
  <div class="col grid s12 m6 l6 ">
    <center><img src="{{ '/images/03-installation_environnement/02-installation_environnement.png' | relative_url }}" class="responsive-img"></center>
  </div>
</div>


Créez un nouveau notebook en cliquant sur <b>New > Python 3</b>

Au sein de la boite de dialogue vide, saisissez :
```python
import os

curDir = os.getcwd()
print(curDir)
```

Exécuter cette cellule soit  en pressant `Shift`+`Enter` ou en cliquant sur <b>Run</b>

Son exécution devrait retourner l'emplacement courant de votre notebook, quelque chose similaire à :

```console
C:/Users/xxxxx/Documents/Python_notebooks
```
<br>

### Installation de packages Python
#### Installation de package avec conda (à privilégier)

Disons que vous désirez installer les <b>Jupyter notebook extensions</b> du répertoire GitHub suivant : [https://github.com/ipython-contrib/jupyter_contrib_nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions)

Vous pouvez réaliser cela très simplement maintenant que vous avez Anaconda, avec la commande suivante :
```console
conda install -c conda-forge jupyter_contrib_nbextensions
```

Les packages installables via `conda` sont répertoriés au sein de [https://anaconda.org/](https://anaconda.org/)

Grâce à ce package tout juste installé, vous allez pouvoir activer un assistant d'autocompletion. Pour cela, accéder à votre nouvelle page de configuration : [http://localhost:8888/nbextensions?nbextensions=codefolding/main](http://localhost:8888/nbextensions?nbextensions=codefolding/main)

Et activer l'extension <b>Hinterland</b> en cochant sur la case associée.

Vous constaterez dorénavant au sein de votre notebook un assistant d'autocompletion durant vos saisies clavier.

#### Installation de package avec pip
Si le package recherché ne fait pas partie des packages gérés par Anaconda ou que vous souhaitez bénéficier de la dernière version d'un package encore non pris en charge par Anaconda, vous pouvez toujours essayer de le trouver sur le Python Package Index Aka PyPi : [https://pypi.org/](https://pypi.org/)

L'installation de package avce `pip` prend la forme suivante
```console
pip install nom_du_package
```

Vous ferez potentiellement face à des messages d'erreurs vous indiquant des packages pré requis manquants. Eh oui... Anaconda se charge de tout, avec `pip` c'est à vous de faire le job.

#### Installation d'un package manuellement (en dernier recours)

En dernier recours, si vous avez besoin d'un package non disponible ni via `conda` ou `pip`, vous pouvez toujours l'installer manuellement.

* Téléchargez les fichiers source du package
* Dézippez les si nécessaire
* S'il y a des instructions d'installation (contenues généralement au sein d'un INSTALL.md ou READ.md) lisez les et suivez les AUTREMENT
* Naviguez via la console Anaconda au sein de son répertoire contenant le fichier `setup.py`
* Saisissez et exécutez simplement
```console
python setup.py install
``` 
<br>

### Composer avec les contraintes de réseau d'entreprise

Disons que vous souhaitiez installer le package `seaborn`. 

#### Résoudre les problèmes de proxy pour Anaconda
En essayant d'installer un package Python via l'outil de ligne de commande `conda`, vous pourriez vous retrouver coincé avec le message suivant

```console
conda install -c conda-forge seaborn
Fetching package metadata:
``` 

Pour résoudre ce problème, contacter votre administrateur réseau et demander les détails relatifs au proxy d'entreprise.

Avec ces informations vous éditerez un fichier de configuration `.condarc` au sein de votre dossier utilisateur (`C:\Users\votre_repertoire_utilisateur`).

<div class="card-panel teal lighten-4">
	<a href="https://conda.io/docs/user-guide/configuration/use-condarc.html">&#91;conda.io&#93;</a> Le fichier de configuration <code>.condarc</code>, est un fichier de configuration optionnel permettant à des utilisateurs avancés de configurer différents aspects de conda, tel que les cannaux de recherche des packages, la configuration de proxy et répertoires d'environment.<br>
	<br>
	Le fichier <code>.condarc</code> <b><u>n'est pas</u></b> inclu par défaut dans l'installation d'Anaconda, mais il est automatiquement créé au sein de votre 
	<b>home directory</b> (<code>C:\Users\Username</code>) la première fois que vous exécutez la commande : <code>conda config</code><br>
</div>

Au sein de votre invite de commande, créez le fichier `.condarc` en exécutant la commande
```console
conda config
```

Editez votre fichier `.condarc` avec les informations transmises par l'administrateur réseau.

* avec informations d'identification :

```console
proxy_servers:
  http: http://user:pass@corp.com:8080
  https: https://user:pass@corp.com:8080

ssl_verify: False
``` 

* sans informations d'identification :

```console
proxy_servers:
  http: http://corp.com:8080
  https: https://corp.com:8080

ssl_verify: False
```

#### Installer un package Python avec pip sans accès à Internet ni droits administrateur

A partir d'une machine où vous avez accès à Internet, téléchargez sur [https://pypi.org](https://pypi.org) ou toute autre source pertinente le fichier .whl du package que vous souhaitez installer.

Le fichier .whl pour seaborn est téléchargeable à partir de [https://pypi.org/project/seaborn/#files](https://pypi.org/project/seaborn/#files)

Transférez ce fichier .whl sur la machine où il doit être installé, celle qui n'a pas d'accès Internet ou un accès restreint, et exécutez la commande suivante (en remplaçant le nom du fichier .whl par celui que vous venez d'obtenir):

```console
pip install seaborn-0.9.0-py3-none-any.whl
```

Vous ferez probablement face à quelques avertissements en rouge avec des messages de la forme :

```console
xxxxxx xx.x.x requires xxxxxx>=xx.x.x, which is not installed.
```

Ce message indique que vous devez d'abord suivre ce processus pour chaque package Python manquant avant de pouvoir installer le package initialement souhaité. 

Une alternative à l'utilisation d'un fichier .whl est l'installation manuelle du package traitée précédemment.

[02 - Bibliothèques Python à privilégier <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-02-bibliotheques-python-a-privilegier %})
{: .align-right}


{% comment %}

## Installation de R
```console
conda install -c r r-essentials
```

## Sous Linux - Installation de l'environnement de travail

Téléchargez la version d'Anaconda supportant la dernière version de <b>Python 3</b> : [https://www.anaconda.com/download/#linux](https://www.anaconda.com/download/#linux)

Lancez l''exécution de l'installateur
```console
cd ~/Downloads
chmod -R 755 Anaconda3-5.3.1-Linux-x86_64.sh
./Anaconda3-5.3.1-Linux-x86_64.sh
```

Acceptez la licence et ajoutez l’emplacement d’installation d'Anaconda3 à PATH dans votre `/home/username/.bashrc`
```console
Do you wish the installer to prepend the Anaconda3 install location
to PATH in your /home/username/.bashrc ? [yes|no]
[no] >>> yes
```

Refresh your environment variables
```console
. ~/.bashrc
```

Check your default python location
```console
which python
```
Check your Python version
```console
python --version
```

Anaconda having currently no internal update to 3.7, for upgrading Python being under 3.6 for example, you will have to do something like 
```console
conda install python==3.7
```

Install Ipython Notebook
```console
conda install ipython-notebook
```

You can now launch the IPython Notebook with:
```console
ipython notebook
```

The IPython Notebook should open in your web browser.

<i>NB: The IPython Notebook is now known as the Jupyter Notebook, so you can also the command:</i>
```console
jupyter notebook
```

{% endcomment %}