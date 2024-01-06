AWS_PROFILE = default
REGION = us-east-1

INSTANCE_TYPE = t2.micro

AMI_ID := $(shell aws ec2 describe-images --owners amazon --filters "Name=architecture,Values=x86_64" "Name=root-device-type,Values=ebs" "Name=virtualization-type,Values=hvm" --query "Images[0].ImageId" --output text)

create-key-pair:
	aws ec2 create-key-pair --key-name zaman_key --query 'KeyMaterial' --output text > zaman_key.pem
	chmod 400 zaman_key.pem

retrieve-subnet-id:
    $(eval SUBNET_ID := $(shell aws ec2 describe-subnets --filters Name=vpc-id,Values=$(shell jq -r '.Vpc.VpcId' vpc.json) --region $(REGION) --profile $(AWS_PROFILE) --query 'Subnets[0].SubnetId' --output text))

create-instance-1:
	aws ec2 run-instances --image-id $(AMI_ID) --count 1 --instance-type $(INSTANCE_TYPE) \
	--key-name zaman_key --subnet-id $(SUBNET_ID) --region $(REGION) \
	--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=VM1}]' \
	--profile $(AWS_PROFILE)

create-instance-2:
	aws ec2 run-instances --image-id $(AMI_ID) --count 1 --instance-type $(INSTANCE_TYPE) \
	--key-name zaman_key --subnet-id $(SUBNET_ID) --region $(REGION) \
	--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=VM2}]' \
	--profile $(AWS_PROFILE)

create-instance-3:
	aws ec2 run-instances --image-id $(AMI_ID) --count 1 --instance-type $(INSTANCE_TYPE) \
	--key-name zaman_key --subnet-id $(SUBNET_ID) --region $(REGION) \
	--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=VM3}]' \
	--profile $(AWS_PROFILE)

create-instance-4:
	aws ec2 run-instances --image-id $(AMI_ID) --count 1 --instance-type $(INSTANCE_TYPE) \
	--key-name zaman_key --subnet-id $(SUBNET_ID) --region $(REGION) \
	--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=VM4}]' \
	--profile $(AWS_PROFILE)

.PHONY:  retrieve-ami-id create-key-pair retrieve-subnet-id create-instance-1 create-instance-2 create-instance-3 create-instance-4
