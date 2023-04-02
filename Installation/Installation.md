Ouvrez un terminal et exécutez la commande suivante pour mettre à jour la liste des paquets et installer les mises à jour disponibles:

 
 
sudo apt update && sudo apt upgrade -y
Installer Java:
Elasticsearch nécessite Java pour fonctionner. Vous pouvez installer OpenJDK avec la commande suivante:

 
sudo apt install -y openjdk-11-jdk
Vérifiez que Java est correctement installé en exécutant :

 
Ajouter le dépôt Elastic:
Importez la clé GPG du dépôt Elastic avec la commande suivante:

 
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
Ajoutez le dépôt Elastic en créant un nouveau fichier dans /etc/apt/sources.list.d/:

 
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
Installer Elasticsearch:
Mettez à jour la liste des paquets et installez Elasticsearch avec la commande suivante:

 
sudo apt update && sudo apt install -y elasticsearch
Activez et démarrez le service Elasticsearch:

 
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
Installer Logstash:
Installez Logstash en utilisant la commande suivante:

 
sudo apt install -y logstash
Activez et démarrez le service Logstash:

 
sudo systemctl enable logstash
sudo systemctl start logstash
Installer Kibana:
Installez Kibana avec la commande suivante:

 
sudo apt install -y kibana
Activez et démarrez le service Kibana:

 
sudo systemctl enable kibana
sudo systemctl start kibana
Configurer Elasticsearch, Logstash et Kibana:
Vous devrez configurer chaque composant en fonction de vos besoins spécifiques. Voici quelques conseils pour commencer:

Elasticsearch: Modifiez le fichier /etc/elasticsearch/elasticsearch.yml pour configurer les paramètres tels que le cluster, le nœud et l'adresse IP d'écoute.

Logstash: Créez des fichiers de configuration dans le répertoire /etc/logstash/conf.d/ pour définir les entrées, les filtres et les sorties. Par exemple, vous pouvez créer un fichier 01-input.conf pour définir les entrées, un fichier 02-filter.conf pour les filtres et un fichier 03-output.conf pour les sorties.

Kibana: Modifiez le fichier /etc/kibana/kibana.yml pour configurer les paramètres tels que l'adresse IP d'écoute, le port et l'URL d'Elasticsearch.