# Project 1

- Network
    - `docker network create goals-net`

- Mongo  
    `docker run --name mongodb -v data:/data/db --rm -d --network goals-net -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=admin mongo`

- Backend
    - `docker build -t goals-node .`
    - `docker run --name goals-backend -v /app/node_modules -v C:/Projects/DevOpsCourse/DockerKubernetesThePracticalGuide/Project_1/backend:/app -v logs:/app/logs -p 80:80 --rm -d --network goals-net goals-node`

- Frontend
    - `docker build -t goals-react .`
    - `docker run --name goals-frontend --name goals-front --rm -p 3000:3000 -t goals-react`