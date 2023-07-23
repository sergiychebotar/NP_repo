# NP_repo
This is sample docker-compose repo to launch LEMP and wordpress locally or with presented Jenkins pipelines.
Be sure to create .env file from .env.sample and DON'T FORGET to change variables. This file is used by docker-compose.
Pipeline from Jenkinsfile is used to build custom wordpress image. Pipeline from Jenkinsfile1 is used to redeploy all services from docker-compose.yml file.
