# Enable X-Ray

## STEP1
Create a CloudWatch Log Stream.  
`/aws/elasticbeanstalk/beego-tutorial`


## Step2
Attach managed policy ([AWSXRayDaemonWriteAccess](https://docs.aws.amazon.com/xray/latest/devguide/xray-permissions.html#xray-permissions-managedpolicies)) to `aws-elasticbeanstalk-ec2-role`.

## STEP3
[Implement](https://github.com/aws/aws-xray-sdk-go#quick-start) X-Ray SDK to the application.  
Append a following line to the Dockerfile:

```
RUN go get github.com/aws/aws-xray-sdk-go/plugins/ecs
```

Append a following line to import section of quickstart/controllers/default.go:

```
"context"
"github.com/aws/aws-xray-sdk-go/xray"
_ "github.com/aws/aws-xray-sdk-go/plugins/beanstalk"
```

Append a following line into function of quickstart/controllers/default.go:

```
_, seg := xray.BeginSegment(context.Background(), "/")
seg.Close(nil)
```


## STEP4

[Build and push image](https://qiita.com/moru3/items/32931813db81d891effb) to Docker Hub.

```
# docker login
docker build --tag=<user_name>/beego-tutorial .
docker push <user_name>/beego-tutorial
```

*<user_name>* is your user name of Docker Hub.

## STEP5
Add X-Ray container and some settings to environment (Modify a [Dockerrun.aws.json](https://docs.aws.amazon.com/ja_jp/xray/latest/devguide/xray-daemon-ecs.html)).


## STEP6
Redeploy to running environment (Upload new Dockerrun.aws.json).


## STEP7
Access this site and check some traces in the X-Ray console.
