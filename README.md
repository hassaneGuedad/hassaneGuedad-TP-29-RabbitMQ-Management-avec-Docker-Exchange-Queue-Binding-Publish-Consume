RabbitMQ Messaging avec Docker (Management UI)


📌 Présentation

Ce projet illustre la mise en place d’un broker de messages RabbitMQ à l’aide de Docker, ainsi que la manipulation des principaux concepts de messagerie via l’interface RabbitMQ Management.

L’objectif est de démontrer le cycle complet d’un message :
Exchange → Routing → Queue → Consumption, sans utiliser de code applicatif.


🧩 Architecture utilisée


Docker : isolation et déploiement rapide du broker

RabbitMQ Management Plugin : administration via interface web

Exchange (direct) : routage des messages

Queue (durable) : stockage des messages

Binding : lien logique entre exchange et queue

Producer
   |
   v
[ Exchange : direct ]
   |
   v
[ Queue ]
   |
   v
Consumer



🚀 Démarrage rapide


Lancer RabbitMQ avec Docker
docker run -d \
  --name rabbit-server \
  --hostname rabbit \
  -p 15672:15672 \
  -p 5672:5672 \
  rabbitmq:3.12.9-management


Interface web : http://localhost:15672

Identifiants par défaut : guest / guest


🧠 Concepts manipulés


🔁 Exchange


Un exchange reçoit les messages et décide vers quelles queues les rediriger.

Type utilisé : direct

Routage basé sur la routing key


📥 Queue


Une queue stocke les messages jusqu’à leur consommation.

Type : classic

Mode : durable


🔗 Binding



Le binding relie un exchange à une queue.

Associe une routing key à une destination


🛠️ Configuration fonctionnelle

Élément	Nom utilisé	Configuration
Exchange	2iteExchange	direct, durable
Queue	2iteQueue	classic, durable
Binding	Exchange → Queue	routing key vide
Payload	Message texte	UTF-8


✉️ Publication des messages


Les messages sont publiés depuis l’interface web de RabbitMQ :

L’exchange reçoit le message

Le binding applique la règle de routage

La queue stocke le message jusqu’à lecture

Ce mécanisme permet :

le découplage entre producteurs et consommateurs

une meilleure fiabilité du transport de données


📖 Consommation des messages

Les messages sont récupérés directement depuis la queue via l’UI :

Mode ACK : suppression définitive

Mode NACK + requeue : remise en file (tests)

Cela permet de visualiser le comportement réel d’une file de messages.


✅ Résultats obtenus

RabbitMQ opérationnel dans un conteneur Docker

Création et gestion des entités de messagerie

Transmission réussie de messages

Observation du flux et de l’état des messages


🎯 Intérêt pédagogique

Ce projet permet de :

Comprendre les bases de la messagerie asynchrone

Manipuler RabbitMQ sans écrire de code

Découvrir l’administration d’un broker de messages

Se préparer à une intégration backend (Spring, Node.js, etc.)


👤 Auteur
Hassane Guedad
Full-Stack Developer


<img width="957" height="540" alt="1" src="https://github.com/user-attachments/assets/778a2244-90bd-42c9-8d49-c990127d08de" />

<img width="960" height="540" alt="2" src="https://github.com/user-attachments/assets/7de5ca7e-8ba5-4423-8ede-dfabe4c4b70d" />

<img width="960" height="539" alt="3" src="https://github.com/user-attachments/assets/f3575589-b876-4a42-9a39-ab9d8e6c50a2" />

<img width="960" height="540" alt="5" src="https://github.com/user-attachments/assets/9140ee14-06c0-4051-a03b-0ee97e43e11e" />

<img width="960" height="540" alt="6" src="https://github.com/user-attachments/assets/fcfed0e5-b458-40cc-9d64-4316c5a18861" />

