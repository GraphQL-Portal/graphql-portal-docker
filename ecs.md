1. Install ecs-cli
   https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html

2. Configure ecs-cli
   `export AWS_ACCESS_KEY_ID="Your Access Key"`
   `export AWS_SECRET_ACCESS_KEY="Your Secret Access Key"`
   `export AWS_DEFAULT_REGION=us-west-2`

3. Configure profile ecs profile for cluster
   `configure.sh`

```
#!/bin/bash
set -e
PROFILE_NAME=tutorial
CLUSTER_NAME=tutorial-cluster
REGION=us-west-2
LAUNCH_TYPE=EC2
ecs-cli configure profile --profile-name "$PROFILE_NAME" --access-key "$AWS_ACCESS_KEY_ID" --secret-key "$AWS_SECRET_ACCESS_KEY"
ecs-cli configure --cluster "$CLUSTER_NAME" --default-launch-type "$LAUNCH_TYPE" --region "$REGION" --config-name "$PROFILE_NAME"
```

4. Create keypair
   `aws ec2 create-key-pair --key-name tutorial-cluster-key --query 'KeyMaterial' --output text > ~/.ssh/tutorial-cluster.pem`

5. Create cluster with 1 ec2 instance t2.micro
   `ecs-cli up --keypair tutorial-cluster-key --port 8080 --capability-iam --size 1 --instance-type t2.micro --cluster-config tutorial --ecs-profile tutorial`

6. Create task definition
   Prepare docker-compose.yml and ecs.params.yml then execute:
   `ecs-cli compose up --create-log-groups --cluster-config tutorial --ecs-profile tutorial`

7. Go to aws console GUI, you should have 1 running ec2 instance. Click at ec2 instance.
   Configure security groups add inbond rules: SSH port 22 and HTTP port 80 from any source.

8. Click at "Connect" button. Connect via ssh to the instance. Clone graphql-portal-docker repo or create own config. Copy this config directory to created volume
   `sudo cp -R . /var/lib/docker/volumes/gateway-data/_data`

9. In the aws console GUI go to Elastic Container Service -> Task Definitions
   Click at created task then open last revision. Click at "Create new revision", scroll down and click "configure via json".
   In the gateway task definition find `links:[]` field and fill it with: `["gql-portal-redis:gql-portal-redis", "gql-portal-dashboard:gql-portal-dashboard"]`
   In the dashboard task definition fill it with: `["gql-portal-redis:gql-portal-redis", "gql-portal-mongo:gql-portal-mongo"]`
   Then save and create new revision. Actions -> Run Task.

10. Go to running tasks, select task, scroll down to containers, go to logs.
