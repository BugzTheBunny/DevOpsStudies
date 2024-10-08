# Some basics about utility container idea.

### Using docker
- build - `docker build -t node-utils .`
- init - `docker run -it -v <path>/Project_3:/app node-utils init`
- install - `docker run -it -v <path>/Project_3:/app node-utils install`

### Using docker-compose
This allows us to run a single command int oa single service, in this case, the `npm` service we define in `docker-compose.yml`.
- init -  `docker-compose run --rm npm init`
- install - `docker-compose run --rm npm init`
