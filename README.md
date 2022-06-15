## make

```
USER_NAME=nirulabs
NODE_ENV_PRODUCTION=NODE_ENV=production
NODE_ENV_DEVELOPMENT=NODE_ENV=development
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
        
```     
 
