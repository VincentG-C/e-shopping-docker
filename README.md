I) Instructions pour construire et exécuter les containers
Les différentes variables d'environnement sont définies dans les fichiers .env. Bien qu'ils devraient être exclus du git pour préserver les secrets, ... je les ai laissés volontairement afin de faciliter l'exécution et que rien ne soit nécessaire. Les variables sont exactement celles qui étaient présentes dans les fichiers, rien n'a été ajouté dans ces fichiers.
Les container individuels sont présents afin d'être lancés dans le docker-compose, ils ne sont pas reliés ni configurés pour fonctionner vraiment en dehors du docker-compose.
1) Frontend
a) Production
Build: docker image build --target prod --tag ecommerce-front-vgc .
Run: docker run --publish 80:8080 ecommerce-front-vgc 
(le run ne marche plus quand lancé directement à cause de la configuration nginx faite pour le docker-compose)
b) Développement
Build: docker image build --target dev --tag ecommerce-front-vgc .
Run: docker run --publish 80:8080 ecommerce-front-vgc
2) Auth service
a) Production
Build: docker image build --target prod --tag ecommerce-auth-service-vgc .
Run: docker run ecommerce-auth-service-vgc
b) Développement
Build: docker image build --target dev --tag ecommerce-auth-service-vgc .
Run: docker run ecommerce-auth-service-vgc
3) Product service
a) Production
Build: docker image build --target prod --tag ecommerce-product-service-vgc .
Run: docker run ecommerce-product-service-vgc
b) Développement
Build: docker image build --target dev --tag ecommerce-product-service-vgc .
Run: docker run ecommerce-product-service-vgc
4) Order service
a) Production
Build: docker image build --target prod --tag ecommerce-order-service-vgc .
Run: docker run ecommerce-order-service-vgc
b) Développement
Build: docker image build --target dev --tag ecommerce-order-service-vgc .
Run: docker run ecommerce-order-service-vgc
5) Docker compose afin de lancer le tout et faire marcher les services
a) Développement
Build: docker compose build
Run: docker compose up
b) Production
Build: docker compose -f docker-compose.prod.yml build
Run: docker compose -f docker-compose.prod.yml up
II) Commandes de test
Je n'ai malheureusement pas fait cette partie.
III) Bonnes pratiques
Multi-stages builds, utilisation de variables d'environnement pour préserver les secrets, suppression des fichiers inutiles avec dockerignore, lancement des applications avec un user non root, réduction de la taille des images, dépôt des images en ligne (https://hub.docker.com/repositories/vgastonc).