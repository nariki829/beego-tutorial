# Create a deploy pipeline

## STEP
Create a [buildspeck.yml](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) file.

## STEP2
Add a secret value to the parameter store of AWS System Manager.  
`/CodeBuild/dockerLoginPassword`  
*It is your password for Docker Hub.*

## STEP3
Create a CodePipeline resource.  
https://aws.amazon.com/getting-started/tutorials/continuous-deployment-pipeline

## STEP4
Add an inline [policy](https://dev.classmethod.jp/cloud/codebuild-env/) to an IAM role for ec2.  

## STEP5
Push some commits and check pipeline behaviours.  
