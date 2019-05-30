# Convert environment type and enable CloudWatch Logs

## STEP1
[Build and push image](https://qiita.com/moru3/items/32931813db81d891effb) to Docker Hub.

```
docker login
docker build --tag=<user_name>/beego-tutorial .
docker push <user_name>/beego-tutorial
```

*<user_name>* is your user name of Docker Hub.

## STEP2
Create application and deploy environment to Elastic Beanstalk.
Select following options and refer [AWS document](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_docker_ecstutorial.html#create_deploy_docker_ecstutorial_deploy):

- Platform : Multi-container Docker
- Application code : Upload your code
  - Source code origin : Local File (zip compressed Dockerrun.aws.json)
