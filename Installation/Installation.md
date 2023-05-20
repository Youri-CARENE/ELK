
## Mise à jour du système

1. Ouvrir un terminal et exécuter la commande suivante pour mettre à jour la liste des paquets et installer les mises à jour disponibles :
```
sudo apt update && sudo apt upgrade -y
```

## Installation de Java

1. Installer OpenJDK avec la commande suivante :
```
sudo apt install -y openjdk-11-jdk
```

## Ajout du dépôt Elastic

1. Importer la clé GPG du dépôt Elastic avec la commande suivante :
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

2. Ajouter le dépôt Elastic en créant un nouveau fichier dans /etc/apt/sources.list.d/ :
```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
```

## Installation d'Elasticsearch

1. Mettre à jour la liste des paquets et installer Elasticsearch avec la commande suivante :
```
sudo apt update && sudo apt install -y elasticsearch
```

2. Activer et démarrer le service Elasticsearch :
```
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
```

## Installation de Logstash

1. Installer Logstash avec la commande suivante :
```
sudo apt install -y logstash
```

2. Activer et démarrer le service Logstash :
```
sudo systemctl enable logstash
sudo systemctl start logstash
```

## Installation de Kibana

1. Installer Kibana avec la commande suivante :
```
sudo apt install -y kibana
```

2. Activer et démarrer le service Kibana :
```
sudo systemctl enable kibana
sudo systemctl start kibana
```

## Configuration d'Elasticsearch, Logstash et Kibana

1. Configurer Elasticsearch en modifiant le fichier /etc/elasticsearch/elasticsearch.yml pour définir les paramètres tels que le cluster, le nœud et l'adresse IP d'écoute.

2. Créer des fichiers de configuration dans le répertoire /etc/logstash/conf.d/ pour définir les entrées, les filtres et les sorties de Logstash. Par exemple, créer un fichier 01-input.conf pour définir les entrées, un fichier 02-filter.conf pour les filtres et un fichier 03-output.conf pour les sorties.

3. Modifier le fichier /etc/kibana/kibana.yml pour configurer les paramètres de Kibana tels que l'adresse IP d'écoute, le port et l'URL d'Elasticsearch.

Vous avez maintenant installé et configuré Elasticsearch, Logstash et Kibana sur votre système. Vous pouvez commencer à les utiliser pour l'analyse et la surveillance des journaux.