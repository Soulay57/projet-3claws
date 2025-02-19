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

### Cloudinit à mettre dans la création de l'instance EC2
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


### Pull de l'image grâce à la commande : 
```docker-compose up -d```
![image](https://github.com/user-attachments/assets/b81c0db5-29b9-4e83-8417-123cbc8133c9)


### Vérification de l'image grâce à la commande : 
```docker ps```

![image](https://github.com/user-attachments/assets/86041d11-767d-4f91-9d17-7a78d96cf3ac)

### Vérification de l'accès à l'application grâce à la commande curl et avec l'interface web

![commane curl](https://github.com/user-attachments/assets/79170b9d-bafa-4c87-8692-f758134c8b7c)
![interface web](https://github.com/user-attachments/assets/9e2fd872-b2c8-4248-a1f6-b8b648bc3063)

# Partie 3 : Modification du virtual env pour connecter la DB et l'application

### Mettre à jour le config.py ;:

![image](https://github.com/user-attachments/assets/c6b27351-513f-489f-9d3e-7299c8649111)

### Création et activation d'un environnement virtuel Python : 

```
bash 
CopierModifier 
python3 -m venv venv 
source venv/bin/activate 
```
![image](https://github.com/user-attachments/assets/e5d6e57b-1c74-4ddf-95d3-45fdf2b861f4)

### Modifier requirement.txt pour ajouter pymysql :
![image](https://github.com/user-attachments/assets/0fb4ca54-209a-4759-b930-3462b92d5361)

Ensuite lancer la commande : 
```
pip install -r requirements.txt
```

### À cause des erreurs d’environnement on a dû installer :  

```
pip install flask-migrate 
```

### Mettre à jour pip, setuptools et wheel  

Cette commande : 
```pip install --upgrade pip setuptools wheel ``` 

remplace : python3-distutils qui est requit pour la migration 

nous  avons eu des erreurs car la python3-distutils n’était pas reconnu 

### Connexion de la DB et l'application
![image](https://github.com/user-attachments/assets/c5f2bbf7-c815-41f8-b087-4fa1ffce2335)
![image](https://github.com/user-attachments/assets/1d31abd6-1349-4b59-92a5-24162bd2f23c)
![image](https://github.com/user-attachments/assets/2d782320-5e33-4683-a40e-f7b2fdc9e683)

### Connexion à la DB et vérification des tâbles

![image](https://github.com/user-attachments/assets/db936769-8bb1-4b00-8080-5b6f8f833f5b)
![image](https://github.com/user-attachments/assets/8b1713ce-a8a5-4602-ac0b-dfae13062031)

# Partie 4 : Test de la connexion entre la DB et l'application

### Création d'un compte utilisateur sur l'interface web 

![image](https://github.com/user-attachments/assets/e37c8da1-7b04-4a70-9b20-cf51687dc182)

### Vérification de l'utilisateur crée en amont dans la DB

![image](https://github.com/user-attachments/assets/836dfe09-d5d8-42f3-994b-e5125f593b47)

