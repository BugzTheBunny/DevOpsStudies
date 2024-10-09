# Deploying Docker Containers (AWS)

- Local
    - Build : `docker build -t node-dep-example .`
    - Run   : `docker run -d --rm --name node-dep -p 80:80 node-dep-example`