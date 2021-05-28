// create keypair
aws ec2 create-key-pair --key-name ec2-tutorial-key --query 'KeyMaterial' --output text > ~/.ssh/ec2-tutorial-key.pem

// create cluster
ecs-cli up --port 8080 --keypair ec2-tutorial-key --capability-iam --size 1 --instance-type t2.micro --cluster-config ec2-tutorial --ecs-profile ec2-tutorial-profile

ecs-cli compose up --create-log-groups --cluster-config ec2-tutorial --ecs-profile ec2-tutorial-profile

connect via ssh clone repo and copy to volume
sudo cp -R . /var/lib/docker/volumes/gateway-data/\_data

git clone https://github.com/GraphQL-Portal/graphql-portal-docker
