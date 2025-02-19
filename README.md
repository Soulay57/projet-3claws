Rapport : Projet Final AWS 

Date : 19/02/2025 

Crée par : KADI Soulaymane, HOMBOURGER Tomy, BERNARD Jonathan, AHMADI Rateb et FIGAROLI Romain 




# Partie 1 : Configuration sur AWS 

## Création du VPC : 
![image](https://github.com/user-attachments/assets/bb9d68e6-f875-49fe-99aa-d2fe516e7272)


## Création de la base de données : 
![image](https://github.com/user-attachments/assets/a15bdc78-1419-4ea7-87b9-795f48ee5b3c)


## Création de l'instance EC2
![image](https://github.com/user-attachments/assets/1575cd57-e7c2-44bc-8091-3cf3b9ff71f3)
![image](https://github.com/user-attachments/assets/0db8aea7-2b88-4124-957d-2d2b105d7dbf)
![image](https://github.com/user-attachments/assets/0d024bc8-1a18-49bc-95aa-f5f04ed6b9bd)

Cloudinit à mettre dans la création de l'instance EC2 
`#!/bin/bash  

# Mise à jour du système  

sudo apt update -y && sudo apt upgrade -y  

# Installation des dépendances  

sudo apt install -y docker.io git default-mysql-client  

# Démarrer et activer Docker  

sudo systemctl start docker  

sudo systemctl enable docker  

# Ajouter l'utilisateur ubuntu au groupe Docker pour éviter les problèmes de permissions  

sudo usermod -aG docker ubuntu  

# Cloner le projet depuis GitHub  

git clone https://github.com/app-generator/flask-datta-able.git  

# Naviguer dans le dossier du projet cloné  

cd flask-datta-able  

# Construire et lancer l'application avec Docker Compose 

docker build -t flask-datta-able . 

docker run -d -p 5085:5085 --name flask-app flask-datta-able `
