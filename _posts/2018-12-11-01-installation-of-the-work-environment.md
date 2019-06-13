---
layout: post
comments: true
title: "01 - Installation of the work environment"
categories: [post]
author: "Benjamin Berhault"
lang: en
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/anaconda.png' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">
    The easiest way to install Python and Jupyter Notebook is probably with Anaconda. <br>
     <br>
     Anaconda is a free and open source ditribution of Python and R programming languages particularly oriented for applications in data science. One of the major assets of Anaconda is its simplification in the management of packages and their dependencies.
  </div>
</div>

#### Contenu de la page
<ul>
	<li>Working environment installation on Microsoft Windows
	<ul>
		<li>Installing Python with Anaconda</li>
		<li>Creating a first Jupiter Notebook</li>
		<li>Installing Python packages
			<ul>
				<li>Package installation with conda (preferred)</li>
				<li>Package installation with pip</li>
				<li>Manually install a package (as a last resort)</li>
			</ul>
		</li>
		<li>Compose with corporate network constraints
			<ul>
				<li>Install a Python package with pip without Internet access</li>
				<li>Troubleshoot Anaconda proxy issues</li>
			</ul>
		</li>
	</ul>
	</li>
</ul>

Pour ceux bien décidés à utiliser R en lieu et place de Python : [Documentation Anaconda détaillant l'installation de R pour le Jupyter Notebook](https://docs.anaconda.com/anaconda/navigator/tutorials/r-lang/)

## Working environment installation on Microsoft Windows

### Installing Python with Anaconda

Download the version of Anaconda supporting the latest version of <b>Python 3</b>: [https://www.anaconda.com/download/#windows](https://www.anaconda.com/download/#windows)

Launch and follow the instructions of the installation executable.

Once the installation is complete, launch the anaconda console via <b>Start menu > Anaconda3 > Anaconda Prompt</b>.

<center><img src="{{ '/images/03-installation_environnement/01-installation_environnement.jpg' | relative_url }}"></center>

Create a Python 3.7 <b>conda environment</b>. (for more information about this consult the [documentation on managing environments](https://conda.io/docs/user-guide/tasks/manage-environments.html))
```console
conda create --name py37 python=3.7
```

<div class="card-panel teal lighten-4">A conda environment is a directory containing a specific collection of packages that you have decided to install. Because some packages do not support the latest version of Python, it may be appropriate to maintain an environment for a specific version of Python. <br>
	<br>
	<b>The ability to create an environment with Anaconda for a package caused me some problems, so I ended up using the Python 3.7 environment installed by default.</b>
</div>
            
To activate your environment within the Anaconda console, enter:
```console
activate py37
```

To leave your environment, simply enter:
```console
deactivate
```

Check your version of Python in this environment:
```console
python --version
```
If you have a Python 3.7 environment installed, it should be returned to you: `Python 3.7.0`

<br>

### Create a first Jupiter Notebook

<div class="row">
  <div class="col grid s12 m6 l6">
  	The Jupyter Notebook is an interactive web tool that allows you to create and share your data handling and analysis scripts with your explanations and numerical or visual results. <br>
  		<br>
    In the Anaconda console, navigate to the directory of your choice, for example: <br>
	<pre class="language-console"><code class="language-console">cd ./Documents/Python_notebooks</code></pre>
	<br>
	Launch a Jupiter notebook<br>
	<pre class="language-console"><code class="language-console">Jupyter Notebook</code></pre>

  </div>
  <div class="col grid s12 m6 l6 ">
    <center><img src="{{ '/images/03-installation_environnement/02-installation_environnement.png' | relative_url }}" class="responsive-img"></center>
  </div>
</div>


Create a new notebook by clicking <b>New > Python 3</b>

In the empty dialog box, enter:
```python
import os

curDir = os.getcwd()
print(curDir)
```

Run this cell either by pressing `Shift`+`Enter` or clicking <b>Run</b>

Its execution should return the current location of your notebook, something similar to:

```console
C:/Users/xxxxx/Documents/Python_notebooks
```
<br>

### Installing Python packages
#### Package installation with conda (preferred)

Say you want to install the <b>Jupyter notebook extensions</b> from the following GitHub directory: [https://github.com/ipython-contrib/jupyter_contrib_nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions)

You can do this very simply now that you have Anaconda, with the following command:
```console
conda install -c conda-forge jupyter_contrib_nbextensions
```

The installable packages via `conda` are listed within [https://anaconda.org/](https://anaconda.org/)

With this package just installed, you will be able to activate an autocompletion wizard. To do this, access your new configuration page:  [http://localhost:8888/nbextensions?nbextensions=codefolding/main](http://localhost:8888/nbextensions?nbextensions=codefolding/main)

And activate the <b>Hinterland</b> extension by checking the associated box.

You will now see in your notebook an autocompletion assistant during your keyboard entries.

#### Package installation with pip
If the package you are looking for is not part of Anaconda-managed packages, or you want to take advantage of the latest version of a package not yet supported by Anaconda, you can always try to find it on the Python Package Index Aka PyPi: [https://pypi.org/](https://pypi.org/)

Package installation with `pip` takes the following form
```console
pip install nom_du_package
```

You will potentially encounter error messages that indicate missing prerequisite packages. Yes ... Anaconda takes care of everything, with  `pip` it's up to you to do the job.

#### Manually install a package (as a last resort)

As a last resort, if you need a package not available `conda` or `pip`, you can still install it manually.

* Download the package source files
* Unzip them if necessary
* If there are any installation instructions (usually found within INSTALL.md or READ.md) read them and follow them OTHERWISE
* Navigate through the Anaconda console in its directory containing the `setup.py` file
* And just type and run
```console
python setup.py install
``` 
<br>

### Compose with corporate network constraints

Say you want to install the `seaborn` package. 

#### Troubleshoot Anaconda proxy issues
When trying to install a Python package via the command-line tool `conda`, you might find yourself stuck with the following message

```console
conda install -c conda-forge seaborn
Fetching package metadata:
``` 

To resolve this problem, contact your network administrator and request details about the enterprise proxy.

With this information you will edit a `.condarc` configuration file within your user folder (`C:\Users\votre_repertoire_utilisateur`).

<div class="card-panel teal lighten-4">
	<a href="https://conda.io/docs/user-guide/configuration/use-condarc.html">&#91;conda.io&#93;</a> The <code>.condarc</code>, configuration file is an optional configuration file that allows advanced users to configure different aspects of conda, such as package discovery channels, proxy configuration, and environment directories.<br>
	<br>
	The <code>.condarc</code> file <b><u>is not</u></b> included by default in the Anaconda installation, but it is automatically created within your <b>home directory</b> (<code>C:\Users\Username</code>) the first time you run the command: <code>conda config</code><br>
</div>

At your command prompt, create the `.condarc` file by running the command
```console
conda config
```

Edit your `.condarc` file with the information provided by the network administrator.

* with identification information:

```console
proxy_servers:
  http: http://user:pass@corp.com:8080
  https: https://user:pass@corp.com:8080

ssl_verify: False
``` 

* without identification information:

```console
proxy_servers:
  http: http://corp.com:8080
  https: https://corp.com:8080

ssl_verify: False
```

#### Install a Python package with pip without Internet access

From a machine where you have access to the Internet, download from [https://pypi.org](https://pypi.org) or any other relevant source the .whl file of the package you want to install.

The .whl file for seaborn can be downloaded from [https://pypi.org/project/seaborn/#files](https://pypi.org/project/seaborn/#files)

Transfer this .whl file to the machine where it is to be installed, the one that does not have Internet access or restricted access, and run the following command (replacing the name of the .whl file with the one you just get):

```console
pip install seaborn-0.9.0-py3-none-any.whl
```

You will probably face some warnings in red with messages of the form:

```console
xxxxxx xx.x.x requires xxxxxx>=xx.x.x, which is not installed.
```

This message indicates that you must first follow this process for each missing Python package before you can install the package that you originally wanted.

An alternative to using a .whl file is installing manually the previously processed package.

[02 - Bibliothèques Python à privilégier <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-02-some-python-libraries-to-consider %})
{: .align-right}




{% comment %}

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