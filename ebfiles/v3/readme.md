# Enable X-Ray

## STEP1
Import X-Ray SDK to the application.  
Append a following line to the Dockerfile:

```
RUN go get github.com/aws/aws-xray-sdk-go/plugins/beanstalk
```

Append a following line to import section of quickstart/main.go:

```
_ "github.com/aws/aws-xray-sdk-go/plugins/ecs"
```


## STEP2

[Build and push image](https://qiita.com/moru3/items/32931813db81d891effb) to Docker Hub.

```
# docker login
docker build --tag=<user_name>/beego-tutorial .
docker push <user_name>/beego-tutorial
```

*<user_name>* is your user name of Docker Hub.

## STEP3
Add X-Ray container and some settings to environment (Modify a Dockerrun.aws.json).


## STEP4
Redeploy to running environment (Upload new Dockerrun.aws.json).
