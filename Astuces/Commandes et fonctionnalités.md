Elasticsearch

GET /_cat/indices : affiche une liste de tous les index Elasticsearch.
PUT /index_name : crée un nouvel index Elasticsearch.
DELETE /index_name : supprime un index Elasticsearch existant.
GET /index_name/_search?q=query_string : effectue une recherche sur un index Elasticsearch.
POST /index_name/_search : effectue une recherche plus complexe à l'aide d'une requête Elasticsearch JSON.
Logstash

input {} : définit la source de données pour Logstash.
filter {} : définit les filtres qui doivent être appliqués aux données.
output {} : définit la destination des données traitées.
stdout {} : affiche la sortie dans la console.
elasticsearch {} : envoie les données traitées à Elasticsearch.
file {} : écrit les données traitées dans un fichier.
Kibana

Discover : affiche les données brutes à partir de l'index Elasticsearch.
Visualize : crée des visualisations à partir des données Elasticsearch.
Dashboard : crée des tableaux de bord à partir des visualisations et des requêtes Elasticsearch.
Saved Objects : gère les objets enregistrés tels que les visualisations, les tableaux de bord et les requêtes.
Fonctionnalités communes

Logstash-forwarder : envoie des logs de façon sécurisée à Logstash.
Beats : envoie des données de métriques système à Elasticsearch.
Watcher : surveille les données et envoie des alertes basées sur des conditions prédéfinies.
Kibana plugins : étend les fonctionnalités de Kibana avec des plugins tiers.
Elasticsearch API : une interface RESTful pour interagir avec Elasticsearch.