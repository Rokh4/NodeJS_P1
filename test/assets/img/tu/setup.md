
<h4 align="center">
  Installations via snap
</h4>
On installe snap :

```shell
sudo apt install snap
```

On commence par installer tout ce qui est installable par snap (https://snapcraft.io/store) :

```shell
sudo snap install code --classic
sudo snap install postman
sudo snap install chromium
sudo snap install mysql-workbench-community
```

___

```shell
sudo apt install glogg
sudo apt install git
sudo apt install curl
sudo apt install subversion
sudo apt install terminator
curl -s "https://get.sdkman.io" | bash
curl -L https://git.io/n-install | bash
```

.bashrc à la fin : 
#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
export SDKMAN_DIR="/home/rokh/.sdkman"
[[ -s "/home/rokh/.sdkman/bin/sdkman-init.sh" ]] && source "/home/rokh/.sdkman/bin/sdkman-init.sh"

export N_PREFIX="$HOME/n"; [[ :$PATH: == *":$N_PREFIX/bin:"* ]] || PATH+=":$N_PREFIX/bin"  # Added by n-install (see http://git.io/n-install-repo).

___

<h4 align="center">
  Installations tomcat
</h4>

```shell
wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.57/bin/apache-tomcat-8.5.57.tar.gz
sudo tar xvf apache-tomcat-8.5.57.tar.gz -C /opt
sudo ln -s /opt/apache-tomcat-8.5.57 /opt/tomcat8
rm apache-tomcat-8.5.57.tar.gz
sudo chmod 755 -R /opt/tomcat8
 
wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.37/bin/apache-tomcat-9.0.37.tar.gz
sudo tar xvf apache-tomcat-9.0.37.tar.gz -C /opt
sudo ln -s /opt/apache-tomcat-9.0.37 /opt/tomcat9
rm apache-tomcat-9.0.37.tar.gz
sudo chmod 755 -R /opt/tomcat9
```

___

<h4 align="center">
  Installations via java via sdkman et création des liens
</h4>

```shell
sudo ln -s ~/.sdkman/candidates/java/11.0.9.open-adpt /opt/java11
sudo ln -s ~/.sdkman/candidates/java/8.0.265-open /opt/java8
sudo ln -s ~/.sdkman/candidates/ant/current /opt/ant
sudo ln -s ~/.sdkman/candidates/gradle/current /opt/gradle
```

___

<h4 align="center">
  Clean les installations potentiellement incomplètes
</h4>

```shell
sudo apt --fix-broken install
```

___

<h4 align="center">
  Création de raccourci pour lancer une appli installé à la mano sur linux (exemple avec eclipse)
</h4>

Créer le fichier :  /home/votre_user/.local/share/applications/eclipse.desktop 

méthode 1 :

```shell
[Desktop Entry]
Comment=Eclipse 2020-09
Name=Eclipse 2020-09
Terminal=false
Version=2020-09
Type=Application
Exec=path_vers_votre_eclipse/eclipse
Icon=path_vers_votre_eclipse/icon.png
Categories=Application;
```

méthode 1 :

```shell
[Desktop Entry]
Comment=Eclipse 2020-09
Name=Eclipse 2020-09
Terminal=false
Version=2020-09
Type=Application
Exec=path_vers_votre_eclipse/eclipse %u
Icon=path_vers_votre_eclipse/icon.xpm
NoDisplay=false
MimeType=x-scheme-handler/eclipse+command;x-scheme-handler/eclipse+mpc;
StartupWMClass=Eclipse
```

Vous pouvez chercher maintenant Eclipse 2020-09 dans vos applications et l'ajouter à vos favoris

___

<h4 align="center">
  Soucis de JRE/JDK non trouvé au lancement d'eclipse, faire
</h4>

```shell
sudo ln -s ~/.sdkman/candidates/java/current/bin/javac /usr/bin/javac
sudo ln -s ~/.sdkman/candidates/java/current/bin/java /usr/bin/java
```

___

<h4 align="center">
  Ajouter / Supprimer des éléments au PATH variable de son linux => \o/ Baeldung
</h4>

Path variable pour linux : 
https://www.baeldung.com/linux/path-variable

___

<h4 align="center">
  Peupler la BDD depuis un .dump
</h4>

Méthode 1 :
Créez une base de donnée vierge et lancez la commande:

```shell
mysql -h localhost -u [user] -p [nom_base] < [fichier.dump]
```

Méthode 2 :
Il faut se connecter à mysql en ligne de commande puis :
ATTENTION : Pour le fichier dump il faut indiquer le chemin complet et ne pas utiliser le tilde ~ !

```shell
$ use [nom_base];
$ source [fichier dump]; COMMIT;
```

Vérifiez que vous avez la conf suivante dans le fichier: /etc/mysql/mysql.cnf et redémarrez le service mysql après modification si non:

```shell
[mysqld]
lower_case_table_names = 1
sql_mode='STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION'
```

