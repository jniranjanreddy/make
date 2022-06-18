## makefile

Command should be followed by make example: make deploy-backend-apps
```
USER_NAME=nirulabs
DEPLOYMENT_DIR=./auto_scripts
check-user:
        echo ${USER_NAME}
        echo ${NODE_ENV_PRODUCTION}
        echo ${NODE_ENV_DEVELOPMENT}

deploy-backend-apps:
        ${DEPLOYMENT_DIR}/deploy-backend.sh

deploy-frontend-apps:
        ${DEPLOYMENT_DIR}/deploy-forntend.sh
        
install-java:
        yum install open-jdk

maven-install:
        make install-java
        yum install maven
        
DOCKER_CONTAINER_NAME=FrontEnd-API
docker-image-with-tar:
	npm ci
	make build-docker-image
	docker save ${DOCKER_CONTAINER_NAME}:latest > ${DOCKER_CONTAINER_NAME}_latest.tar

build-docker-image:
	rm -rf node_modules dist logs
	docker build --no-cache -t ${DOCKER_CONTAINER_NAME} .
   
npm-pre-check:
	npm run format-build-test

npm-build:
	npm run build:no-emit

npm-check:
	npm run check

format-build-test-and-start:
	npm run format && npm run build && npm run test && npm run start

npm-test-and-start:
	npm run test && npm run start
```
# How to load variables from a file, # Prod.env file should exist in the same path as makefile
```
prod_config = prod.env
include $(prod_config)
export $(shell sed 's/=.*//' $(prod_config))

hello-env:
	@echo ${AWS_EKS_CLUSTER_NAME}   # without @echo, echo command will be displayed in command output" 
	env | wc -l


```
