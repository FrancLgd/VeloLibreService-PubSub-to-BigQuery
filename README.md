
<h2 align="center">Mise en place d'un pipeline ETL depuis une base MongoDB</h2>


<div align="center"><img src="https://cdn.static-media.blent.ai/images/projects/badge_mongodb.svg" width="120" alt="Badge du projet" /></div>

<h2 align="center">François Legland</h2>

## Description


## Étapes de réalisation

### 0. Se connecter avec la commande `gcloud`

```shell
gcloud config set project genial-wonder-440610-d4
```

### 1. Créer l'environnement `venv`

```shell
conda deactivate
python -m venv venv
source ./venv/bin/activate
```

Et y installer les dépendances

```shell
pip install google-cloud-pubsub
```

### 2. Créer le topic `bike-sharing-trips` sur PubSub

```shell
gcloud pubsub topics create bike-sharing-trips
gcloud pubsub topics describe bike-sharing-trips
```

### 3. Exécuter 

```shell
python ./src/pubsub_publisher.py
```

### 4. Créer un abonnement au topic

```shell
gcloud pubsub subscriptions create bike-sharing-trips-subs-1 \
    --topic=bike-sharing-trips
```