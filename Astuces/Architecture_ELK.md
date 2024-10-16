# Architecture de la Stack ELK

## Aperçu de l'architecture
L'architecture de la stack ELK est composée de trois éléments principaux qui interagissent de manière fluide pour gérer des données volumineuses et complexes.

### 1. Elasticsearch
- **Cluster** : Elasticsearch fonctionne en cluster, chaque instance étant un nœud. Un cluster est un ensemble de nœuds qui coopèrent pour stocker et indexer les données. Le cluster peut être scalé horizontalement en ajoutant des nœuds supplémentaires.
- **Sharding** : Les données sont divisées en fragments (shards) qui sont répartis entre plusieurs nœuds. Chaque shard peut être répliqué pour tolérance de pannes.
- **Index** : Un index est une collection de documents partageant des caractéristiques similaires. Chaque document est une entité JSON dans Elasticsearch.

### 2. Logstash
- **Pipeline** : Logstash suit une architecture en pipeline. Il a des entrées (input), des filtres (filter) et des sorties (output). Un exemple d'entrée pourrait être un fichier de logs, un filtre pourrait être l'extraction de champs particuliers, et une sortie pourrait être Elasticsearch ou un fichier.
- **Filtres** : Les filtres permettent de transformer les données collectées. Par exemple, on peut parser des logs Apache pour extraire des informations comme l'adresse IP, l'utilisateur, ou la durée de la requête.

### 3. Kibana
- **Visualisation** : Kibana est l'outil de visualisation et d'interaction avec les données dans Elasticsearch. Il offre des graphiques variés et des tableaux de bord dynamiques.
- **Dashboards** : Les tableaux de bord dans Kibana permettent de regrouper plusieurs visualisations pour donner une vue d'ensemble des données d'intérêt.



