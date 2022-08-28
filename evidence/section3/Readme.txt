* GIT URL: https://github.com/shikanara/Lession-3-Build-CI-CD-Pipelines-Monitoring-Logging
1. create database rds - should choose create new VPC

cd ./circleci/files aws cloudformation deploy --template-file cloudfront.yml --stack-name production-distro --parameter-overrides WorkflowID="udapeople-shika87dhjppmz437"


2. Use the workflow id to mark your CloudFormation stacks so that you can reference them later on (ex: rollback). 
+ backend: aws cloudformation deploy --template-file .circleci/files/backend.yml --stack-name "udapeople-backend-udapeople-shika87dhjppmz437" --parameter-overrides ID="udapeople-shika87dhjppmz437" --tags project=udapeople
+ frontend: aws cloudformation deploy --template-file frontend.yml --stack-name "udapeople-frontend-udapeople-shika87dhjppmz437" --parameter-overrides ID="udapeople-shika87dhjppmz437" --tags project=udapeople
# to fix An error occurred (InvalidClientTokenId) when calling the DescribeStacks operation: The security token included in the request is invalid.
-> should update user centificate by using comandline "aws configure" and update "aws_access_key_id" and "aws_secret_access_key" when u had created new IAM user 

3. to fetch all public ip from EC
aws ec2 describe-instances --query 'Reservations[*].Instances[*].PublicIpAddress' --output text >> inventory.txt