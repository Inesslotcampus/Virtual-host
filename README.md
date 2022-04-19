# Virtual-host

__avoir installé apache2 en amont__


## 1. Créer la structure du répertoire

sudo mkdir -p /var/www/NomDuDomaine.com/public_html

## 2. Accorder des autorisations

sudo chown -R $USER:$USER /var/www/example.com/public_html //$USER prend la valeur de l'utilisateur connecté 

sudo chmod -R 755 /var/www //Donne autorisations pour que le répertoir général du web et tous les fichiers soit lus et que les pages soient servies autrement

## 3. Créer une page démo 

nano /var/www/NomDuDomaine.com/public_html/index.html

rajout: 

<html>
  
  <head>
    
    <title>Welcome to NomDuDomaine.com!</title>
    
  </head>
  
  <body>
    
    <h1>virtual host is working!</h1>
  
  </body>

</html>

=> CTRL X puis Y(yes) et ENTER


## Créer nouveaux fichiers vhost 

- sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/NomDuDomaine.conf // copier fichier pr premier domaine

- sudo nano /etc/apache2/sites-available/NomDuDomaineconf // nv fichier ds éditeur web 
 => changer serverAdmin avec sonmail du campus
 => ajouter : ServerName NomduDomaine //établit 
ServerAlias www.NomDuDomaine
=> DocumentRoot /var/www/NomDuDomaine/public_html // modif DocumentRoot

=> enregistrer fichier 

## Activer fichier vhost

- sudo a2ensite NomDuDomaine.conf // a2ensite active site 
- sudo a2dissite 000-default.conf // desactivation de dossier defaut 

- sudo systemctl restart apache2
- sudo systemctl status apache2


## Test résultat 

http://NomDuDomaine


##DNS (=domain name system)

P Le DNS permet d’associer un nom compréhensible, à une adresse IP. On associe donc une adresse logique, le nom de domaine, à une adresse physique l’adresse IP.




