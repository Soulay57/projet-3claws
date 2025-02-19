# Rapport : Projet Final AWS 

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
```
#!/bin/bash  
sudo apt update -y && sudo apt upgrade -y  
sudo apt install -y docker.io git default-mysql-client  
sudo systemctl start docker  
sudo systemctl enable docker  

sudo usermod -aG docker ubuntu  

git clone https://github.com/app-generator/flask-datta-able.git  

cd flask-datta-able  

docker build -t flask-datta-able . 

docker run -d -p 5085:5085 --name flask-app flask-datta-able
```
![image](https://github.com/user-attachments/assets/2b41ff51-3f0e-4b95-a8c7-bf4d5ac93e13)



# Partie 2 : Configuration sur la VM 

### Connexion en SSH sur le VM grâce à la clé généré 

![image](https://github.com/user-attachments/assets/b699835e-d7e0-495b-b906-1919c41530d9)
![image](https://github.com/user-attachments/assets/c77094ca-8d38-47d6-bba2-5c63c8263507)


### Modification du fichier .env pour établir la connexion avec la base de donnée

![image](https://github.com/user-attachments/assets/6e3c4b2b-378d-4651-80ef-6f9e8e325050)




