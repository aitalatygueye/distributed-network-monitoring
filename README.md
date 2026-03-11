# Système de Monitoring Réseau Distribué

## Description

Ce projet implémente un système de monitoring réseau distribué développé en Python.
Plusieurs agents clients collectent des informations système (CPU, mémoire, disque, uptime) et les envoient à un serveur central.

Le serveur reçoit ces données, les enregistre dans une base de données SQLite et vérifie si certaines valeurs dépassent des seuils afin de générer des alertes.

Ce projet illustre les concepts suivants :

* systèmes distribués
* programmation réseau avec sockets
* multithreading
* stockage de données avec SQLite
* architecture client-serveur

---

## Architecture du projet

Le système est composé de trois parties principales :

1. **Agents clients**

* collectent les métriques système
* envoient les données au serveur

2. **Serveur de monitoring**

* reçoit les données des clients
* traite les métriques
* génère des alertes

3. **Base de données**

* stocke l’historique des métriques
* stocke les alertes

Architecture simplifiée :

Clients → Serveur de monitoring → Base de données

---

## Structure du projet

distributed-network-monitoring

client

* agent_client.py

server

* server.py
* client_handler.py
* alert_manager.py
* node_monitor.py

database

* database.py

config

* init_db.py

README.md

---

## Technologies utilisées

* Python
* SQLite
* Programmation Socket
* Multithreading

---

## Fonctionnalités

* collecte des métriques système
* communication client-serveur
* stockage des données dans une base SQL
* génération d’alertes si les seuils sont dépassés
* simulation de plusieurs machines

---

## Installation

1. Cloner le projet depuis GitHub :

git clone https://github.com/ton-repository/distributed-network-monitoring.git

2. Ouvrir le projet dans PyCharm.

3. Vérifier que Python est installé sur votre machine.

---

## Exécution du projet

### 1 Initialiser la base de données

python config/init_db.py

Cela va créer la base :

monitoring.db

---

### 2 Lancer le serveur

python server/server.py

Le serveur démarre et attend les connexions des clients.

---

### 3 Lancer un agent client

python client/agent_client.py

Le client envoie périodiquement les métriques au serveur.

---

### 4 Simuler plusieurs clients

Pour simuler plusieurs machines :

for i in {1..20}
do
python client/agent_client.py &
done

---

## Exemple de métriques envoyées

{
"node": "node1",
"cpu": 45,
"memory": 60,
"disk": 70,
"uptime": 12000
}

---

## Auteur

Projet réalisé dans le cadre du Master Systèmes, Réseaux et Infrastructures Virtuelles.
