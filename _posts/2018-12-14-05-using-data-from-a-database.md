---
layout: post
comments: true
title: "05 - Using data from a database"
categories: [post]
author: "Benjamin Berhault"
lang: en
---

<div class="row">
  <div class="col grid s12 m6 l3" height>
    <img src="{{ '/images/db_python.png' | relative_url }}" class="responsive-img" style="padding-top: 20px">
  </div>
  <div class="col grid s12 m6 l9 ">
    For those comfortable with SQL, it may be relevant to first import the dataset into a database to conduct a first phase of exploratory data analysis and manipulation.<br>
    	<br>
    Once this first phase is done, Python will be used in a second phase to continue the analysis and data exploitation and data rendering activities.
  </div>
</div>


* <big>Within a Microsoft Windows environment</big>
	* I will opt for [SQL Server 2017 Express Edition](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express) as a database system
	* and [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) to manage and query it.
* <big>Within a Linux or Mac OS environment</big>
	* I will opt for a PostgreSQL database
	* and pgAdmin 4 to manage and query it.

## Within a Microsoft Windows environment

#### Microsoft SQL Server and SSMS installation
Download <b>[SQL Server 2017 Express Edition](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express)</b>.

Launch the executable and follow the installation instructions.

Following this installation your computer will need to restart.

Once restarted, in the same language as your SQL Server installation download and install <b>[SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)</b>.

Once installed, open <b>SQL Server Management Studio</b> (<b>Start menu > Microsoft SQL Server Tools 17 > Microsoft SQL Server Management Studio</b>).

An instance of Microsoft SQL Server Express should automatically be detected and offered at login (otherwise <b>Server name > Browse... > Database Engine > DESKTOP-XXXXX</b>).

Click on <b>Connect</b>.

#### Importing data into a database

Create a new database from the <b>Object Explorer</b> window by right-clicking on the <b>Database</b> folder.

Give him a name. and click <b>OK</b>.

<b>Right click</b> on your new database <b>> Tasks > Import data...</b>
<img src="{{ '/images/04-exploitation-des-donnees-au-sein-d-une-bdd/02-exploitation-des-donnees-au-sein-d-une-bdd.png' | relative_url }}" class="responsive-img" style="padding-top: 20px">

Select for <b>Data Source: Flat File Source</b>.

<b>Next</b>

As file name, browse through the <b>Parcourir...</b> button the [data.csv file]({{ '/data/data.zip' | relative_url }}) (select the CSV file format) previously downloaded and unzipped.

<b>Open</b>

Make sure the <b>Code Page</b> field is set to <b>65001 (UTF-8)</b>.

<img src="{{ '/images/04-exploitation-des-donnees-au-sein-d-une-bdd/03-exploitation-des-donnees-au-sein-d-une-bdd.png' | relative_url }}" class="responsive-img" style="padding-top: 20px">

Via the <b>Avanced</b> tab, modify only the <b>DataType</b> of the Unicode String <b>Statut opérationnel</b> column [DT_WSTR].

<img src="{{ '/images/04-exploitation-des-donnees-au-sein-d-une-bdd/04-exploitation-des-donnees-au-sein-d-une-bdd.png' | relative_url }}" class="responsive-img" style="padding-top: 20px">

<b>Next</b>

<b>Destination : SQL Server Native Client 11.0</b>

<b>Next</b>

Click <b>Edit mappings...</b>.

Change the type of the <b>Statut opérationnel</b> to <b>nvarchar</b>.

<b>OK</b>

<b>Next</b>

<b>Finish</b>

In the <b>Object Explorer</b> window, with a right click on the database name <b>> Refresh</b> you should see your table: <b>dbo.data</b>.

Here you can check the data by right clicking on the table name <b>> Select first 1000 rows</b>.
<img src="{{ '/images/04-exploitation-des-donnees-au-sein-d-une-bdd/05-exploitation-des-donnees-au-sein-d-une-bdd.png' | relative_url }}" class="responsive-img" style="padding-top: 20px">

Our data has been loaded but the types are not optimal.

We will therefore create a new table with the correct data types.

Right-click on your table <b>> Generate Table Script As > CREATE To > New Query Editor Window</b>.

And modify this code in the following way (here a dedicated diagram has been created).

```sql
USE [data-challenge]
GO

/****** Object:  Table [dbo].[data]    Script Date: 15/12/2018 10:25:00 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE SCHEMA BSPP
GO

CREATE TABLE [BSPP].[data](
	[Date] [Datetime] NULL,
	[Longitude] float NULL,
	[Latitude] float NULL,
	[Véhicule de secours] int NULL,
	[Famille de véhicule de secours] [varchar](50) NULL,
	[Statut opérationnel] [nvarchar](50) NULL,
	[Numéro Intervention] int NULL,
	[Type d'intervention] [varchar](50) NULL,
	[Disponibilité du moyen de secours] bit NULL,
	[Centre de secours] int NULL
) ON [PRIMARY]
GO
```

Insert the correctly formatted data to your new table.
```sql
SET DATEFORMAT ymd

INSERT INTO [BSPP].[data]
SELECT CONVERT(datetime, [Date], 121)
	,IIF([Longitude] NOT LIKE 'NULL', CAST([Longitude]  As float), NULL)
	,IIF([Latitude] NOT LIKE 'NULL', CAST([Latitude]  As float), NULL)
	,IIF([Véhicule de secours] NOT LIKE 'NULL', CAST([Véhicule de secours] As INT), NULL)
	,IIF([Famille de véhicule de secours] NOT LIKE 'NULL', [Famille de véhicule de secours], NULL)
	,IIF([Statut opérationnel] NOT LIKE 'NULL', [Statut opérationnel], NULL)
	,IIF([Numéro Intervention] NOT LIKE 'NULL', CAST([Numéro Intervention] As INT), NULL)
	,IIF([Type d'intervention] NOT LIKE 'NULL', [Type d'intervention], NULL) As [Type d'intervention]
	,IIF([Disponibilité du moyen de secours] NOT LIKE 'NULL', CAST([Disponibilité du moyen de secours] AS BIT), NULL)
	,IIF([Centre de secours] NOT LIKE 'NULL', CAST([Centre de secours] AS INT), NULL)
FROM [data-challenge].[dbo].[data] 
```

#### Querying SQL Server from a Jupyter Notebook

Once you have completed the first phase of your data analysis and manipulation within SQL Server Management Studio, you will want to be able to query the Microsoft SQL Server database from the Jupyter Notebook.

To query SQL Server in Python you can use the package `pymmsql` (this package distributed under conda-forge is only for linux-64 and osx-64, so choose the one distributed by anaconda).

```console
conda install -c anaconda pymssql
```

To directly execute row SQL queries within a Jupyter Notebook you can use the ipython-sql package.

```console
conda install -c conda-forge ipython-sql
```

<div class="card-panel teal lighten-4">
The ability to create an <a href="https://conda.io/docs/user-guide/tasks/manage-environments.html">environnement</a> with Anaconda for this package caused me problems, so I used the default Python 3.7 environment.
</div>

From now on in a Jupyter Notebook, you can enter SQL queries as follows:
<center><img src="{{ '/images/04-exploitation-des-donnees-au-sein-d-une-bdd/01-exploitation-des-donnees-au-sein-d-une-bdd.png' | relative_url }}" class="responsive-img" style="padding-top: 20px"></center>

<b>Connection strings</b>

* without identifiers
```console
%sql mssql+pyodbc://@serveur/base_de_donnees?driver=SQL+Server+Native+Client+11.0
```

* avec identifiers
```console
%sql mssql+pyodbc://login_utilisateur:mot_de_passe@serveur/base_de_donnees?driver=SQL+Server+Native+Client+11.0
```

<p style="text-align: right;"><a href="{{site.baseurl}}/challenge.html">Access the challenge <i class="material-icons" style="vertical-align:middle">fast_forward</i></a></p>

{% comment %}

## Linux (exemple sous Gnome/CentOS 7)

Optant pour une base de données relationnelle dans un environnement Linux j'opterai pour une base PostgreSQL

Installez Postgresql

Ajouter le Postgres Yum repository
```console
rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm
```

Installer PostgreSQL Server & les bibliothèques partagées de développement
```console
yum install postgresql10 postgresql10-devel postgresql10-server
```

Après l'installation de PostgreSQL, vous aurez besoin de l'initialiser avant première utilisation.
```console
/usr/pgsql-10/bin/postgresql-10-setup initdb
```

Par défaut, PostgreSQL n'utilise pas authentification via mot de passe. Nous allons changer cela en éditant sa configuration host based authentication (HBA).

Editez le fichier de configuration HBA.
```console
sudo vi /var/lib/pgsql/10/data/pg_hba.conf

host    all             all             127.0.0.1/32            md5
host    all             all             ::1/128                 md5
```

Sauvegardez-le et fermez-le. PostgreSQL est désormais configuré pour permettre une identification par mot de passe.

Démarrez le service PostgreSQL.
```console
systemctl start postgresql-10
```

Pour que PostgreSQL soit lancé au démarrage du système, exécutez:
```console
systemctl enable postgresql-10
```

Vous pouvez vérifier le statut du service PostgreSQL.
```console
systemctl status postgresql-10
```

Installation de pgAdmin
```console
sudo yum install pgadmin4 pgadmin4-desktop-gnome
```

Lancer pgAdmin4 qui s'ouvrira au sein de votre navigateur
```console
pgadmin4
```

Créez un serveur
* Onglet General
	* Spécifiez un Name
* Onglet Connection
	* Host name/address : localhost
	* Port : 5432
	* Maintenance database :
	* Username : 
	* Password :

Save

{% endcomment %}