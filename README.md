# MongoDB + mongo-express + Docker Compose: montando rapidamente um ambiente para uso

    version: '3'

    services:
    mongo-express:
        image: mongo-express
        ports:
        - 8081:8081
        environment:
        ME_CONFIG_BASICAUTH_USERNAME: renatogroffe
        ME_CONFIG_BASICAUTH_PASSWORD: MongoExpress2019!
        ME_CONFIG_MONGODB_PORT: 27017
        ME_CONFIG_MONGODB_ADMINUSERNAME: root
        ME_CONFIG_MONGODB_ADMINPASSWORD: MongoDB2019!
        links:
        - mongo
        networks:
        - mongo-compose-network

    mongo:
        image: mongo
        environment:
        MONGO_INITDB_ROOT_USERNAME: root
        MONGO_INITDB_ROOT_PASSWORD: MongoDB2019!
        ports:
        - "27017:27017"
        volumes:
        - /home/renatogroffe/Desenvolvimento/Docker/Volumes/MongoDB:/data/db
        networks:
        - mongo-compose-network

    networks:
        mongo-compose-network:
        driver: bridge

Ao acessar o endereço http://localhost:8081 via browser aparecerá inicialmente uma janela solicitando as credenciais para uso do mongo-express.

OBS: Caso o express não subir junto com o mongo, executar novamente o container do express após a execução do contaienr do mongo.
