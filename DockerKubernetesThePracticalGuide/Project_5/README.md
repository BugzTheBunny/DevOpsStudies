# Deploying Docker Containers (AWS)

- Local
    - Build : `docker build -t node-dep-example .`
    - Run   : `docker run -d --rm --name node-dep -p 80:80 node-dep-example`

- EC2 instnace Preps [If having issues](https://stackoverflow.com/questions/53918841/how-to-install-docker-on-amazon-linux2/61708497#61708497)
    - Connecting to instance example: `ssh -i "exampleapp.pem" ec2-user@<user>.compute-1.amazonaws.com`
    - Install all what is required: `sudo yum update -y`
    - Install docker : `sudo yum -y install docker`
    - Start docker

- Dockerhub
    - Create repo.
    - Tag the images created with the repo name, for example : `docker tag node-dep-example bugzthebunny/node-example-1`
    - Push to repo : `docker push bugzthebunny/node-example-1 `

- Runnig app in instance
    - `docker run -d --rm -p 80:80 bugzthebunny/node-example-1`

- Updates / Rebuild
    - Rebuild the image
    - Tag it
    - Push to Docekr Hub
    - Pull / Run again in EC2