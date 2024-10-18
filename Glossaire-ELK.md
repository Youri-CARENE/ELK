# Glossaire ELK (Elasticsearch, Logstash, Kibana)

## 1. **ELK Stack**
**Définition**: Suite d'outils composée de trois projets open-source : Elasticsearch, Logstash, et Kibana, utilisés pour la gestion des logs et l'analyse de données.
**Utilité**: Permet de collecter, analyser, et visualiser de grandes quantités de données en temps réel.

---

## 2. **Elasticsearch**
**Définition**: Moteur de recherche et d'analyse distribué basé sur Apache Lucene, utilisé pour stocker et interroger de grandes quantités de données.
**Utilité**: Permet d'effectuer des recherches rapides et des analyses sur des données volumineuses.
**Exemple**: Utilisation pour stocker des logs d'application et effectuer des recherches dessus.
**Commande**:
    ```bash
    curl -X GET "localhost:9200/_search"
    ```

---

## 3. **Logstash**
**Définition**: Pipeline de traitement de données servant à collecter, filtrer, transformer, et acheminer les données vers une destination (comme Elasticsearch).
**Utilité**: Centralise et transforme les logs provenant de diverses sources avant de les envoyer à Elasticsearch.
**Exemple**: Collecter des logs depuis un serveur, les transformer (parsing) et les envoyer à Elasticsearch.
**Configuration**:
    ```bash
    input { stdin { } }
    output { elasticsearch { hosts => ["localhost:9200"] } }
    ```

---

## 4. **Kibana**
**Définition**: Outil de visualisation et d'exploration de données pour Elasticsearch, utilisé pour créer des tableaux de bord et visualiser des données en temps réel.
**Utilité**: Crée des visualisations interactives basées sur les données indexées dans Elasticsearch.
**Exemple**: Création d'un tableau de bord pour surveiller l'activité d'une application en temps réel.
**Accès**:
    ```bash
    http://localhost:5601
    ```

---

## 5. **Beats**
**Définition**: Collection d'agents légers envoyant des données à Logstash ou Elasticsearch directement.
**Utilité**: Collecte de données légères comme les logs, les métriques de systèmes, ou les paquets réseaux, et envoie ces informations à ELK.
**Exemple**: Utilisation de Filebeat pour collecter les logs d'un fichier et les envoyer à Elasticsearch.
**Configuration**:
    ```yaml
    filebeat.inputs:
      - type: log
        paths:
          - /var/log/*.log
    output.elasticsearch:
      hosts: ["localhost:9200"]
    ```

---

## 6. **Index**
**Définition**: Structure utilisée par Elasticsearch pour stocker et organiser les documents.
**Utilité**: Stocke les données de manière organisée, facilitant les recherches et l'analytique.
**Commande**:
    ```bash
    curl -X PUT "localhost:9200/my-index"
    ```

---

## 7. **Document**
**Définition**: Unité de base d'informations stockée dans Elasticsearch, généralement représentée en JSON.
**Utilité**: Contient les données qui sont indexées et recherchées.
**Exemple**:
    ```json
    {
      "user": "John Doe",
      "message": "This is a log message"
    }
    ```

---

## 8. **Mapping**
**Définition**: Processus qui permet de définir la structure des documents et le type des données qu'ils contiennent dans un index Elasticsearch.
**Utilité**: Contrôle la manière dont les documents et les champs sont stockés et indexés.
**Exemple**:
    ```json
    {
      "mappings": {
        "properties": {
          "user": { "type": "text" },
          "message": { "type": "text" }
        }
      }
    }
    ```

---

## 9. **Shards**
**Définition**: Partition de données dans un index Elasticsearch, permettant de distribuer les données sur plusieurs nœuds pour assurer la scalabilité et la haute disponibilité.
**Utilité**: Améliore les performances en distribuant les requêtes sur plusieurs machines.
**Exemple**: Un index peut être divisé en 5 shards par défaut.

---

## 10. **Replica**
**Définition**: Copie d'un shard dans Elasticsearch, utilisée pour assurer la redondance et la haute disponibilité des données.
**Utilité**: Permet la tolérance aux pannes en assurant qu'il existe des copies supplémentaires des données.
**Exemple**: Un index avec 1 shard peut avoir 1 replica, ce qui double la disponibilité des données.

---

## 11. **Cluster**
**Définition**: Ensemble de nœuds Elasticsearch travaillant ensemble pour partager les données et fournir une redondance.
**Utilité**: Permet de distribuer les données et les requêtes sur plusieurs serveurs pour améliorer la résilience et les performances.
**Commande**:
    ```bash
    curl -X GET "localhost:9200/_cluster/health"
    ```

---

## 12. **Ingest Pipeline**
**Définition**: Mécanisme dans Elasticsearch qui permet de traiter les documents avant qu'ils ne soient indexés.
**Utilité**: Applique des transformations aux documents avant leur stockage dans Elasticsearch, sans avoir besoin de passer par Logstash.
**Exemple**:
    ```json
    {
      "processors": [
        {
          "set": {
            "field": "field_name",
            "value": "new_value"
          }
        }
      ]
    }
    ```

---

## 13. **Query DSL (Domain Specific Language)**
**Définition**: Langage utilisé par Elasticsearch pour interroger les données. Il permet de construire des requêtes complexes.
**Utilité**: Permet de rechercher et d'analyser les données stockées dans Elasticsearch avec des requêtes simples ou complexes.
**Exemple**:
    ```json
    {
      "query": {
        "match": {
          "message": "error"
        }
      }
    }
    ```

---

## 14. **Dashboard**
**Définition**: Ensemble de visualisations dans Kibana, souvent organisées sur une même page pour fournir un aperçu global des données.
**Utilité**: Permet de surveiller les données et de prendre des décisions en temps réel grâce à des graphiques interactifs.
**Exemple**: Création d'un tableau de bord pour visualiser les erreurs d'une application.

---

## 15. **Filter**
**Définition**: Méthode utilisée dans Logstash pour transformer ou enrichir les données pendant leur transit.
**Utilité**: Permet d'ajouter, de supprimer, ou de transformer des champs dans les logs avant qu'ils ne soient envoyés à Elasticsearch.
**Exemple**:
    ```bash
    filter {
      grok {
        match => { "message" => "%{COMBINEDAPACHELOG}" }
      }
    }
    ```

---

## 16. **Grok**
**Définition**: Filtre utilisé dans Logstash pour analyser et extraire des informations de chaînes de caractères en fonction de modèles.
**Utilité**: Simplifie l'extraction d'informations structurées à partir de logs non structurés.
**Exemple**:
    ```bash
    filter {
      grok {
        match => { "message" => "%{COMBINEDAPACHELOG}" }
      }
    }
    ```

---

## 17. **Metricbeat**
**Définition**: Agent de collecte de métriques faisant partie de Beats, utilisé pour envoyer des métriques de performance à Elasticsearch.
**Utilité**: Collecte des métriques système ou application et les envoie à Elasticsearch pour l'analyse.
**Exemple**: Utilisé pour surveiller la santé des serveurs et des services.
**Configuration**:
    ```yaml
    metricbeat.modules:
    - module: system
      metricsets:
        - cpu
        - memory
    output.elasticsearch:
      hosts: ["localhost:9200"]
    ```

---

## 18. **Filebeat**
**Définition**: Agent léger de Beats utilisé pour collecter et expédier des logs à Logstash ou directement à Elasticsearch.
**Utilité**: Utile pour collecter les fichiers journaux à partir de systèmes distribués et les envoyer à ELK.
**Exemple**:
    ```yaml
    filebeat.inputs:
      - type: log
        paths:
          - /var/log/*.log
    output.elasticsearch:
      hosts: ["localhost:9200"]
    ```

---

## 19. **Alerting**
**Définition**: Fonctionnalité permettant de créer des alertes dans Kibana basées sur des seuils ou des conditions spécifiques dans les données.
**Utilité**: Alerte les utilisateurs en cas d'événements anormaux ou critiques (ex: une montée en flèche des erreurs d'application).
**Exemple**: Création d'une alerte pour notifier si le nombre de requêtes échouées dépasse un seuil.

---

## 20. **Timelion**
**Définition**: Outil de visualisation de séries temporelles dans Kibana, permettant de créer des graphiques basés sur des données chronologiques.
**Utilité**: Utile pour analyser les tendances dans les données sur une période de temps.
**Exemple**: Visualisation des erreurs d'application sur les 7 derniers jours.

---
