AWS_PROFILE = default
REGION = us-east-1
VPC_CIDR_BLOCK = 10.10.0.0/16
SUBNET_CIDR_BLOCK = 10.10.1.0/24
VPC_NAME = zaman_vpc
SUBNET_NAME = zaman_subnet

create-vpc:
	aws ec2 create-vpc --cidr-block $(VPC_CIDR_BLOCK) --region $(REGION) --profile $(AWS_PROFILE) \
	--output json > vpc.json

create-tags-vpc:
	aws ec2 create-tags --resources $(shell jq -r '.Vpc.VpcId' vpc.json) \
	--tags Key=Name,Value=$(VPC_NAME) --region $(REGION) --profile $(AWS_PROFILE)

retrieve-subnet-id:
    $(eval SUBNET_ID := $(shell aws ec2 describe-subnets --filters Name=vpc-id,Values=$(shell jq -r '.Vpc.VpcId' vpc.json) --region $(REGION) --profile $(AWS_PROFILE) --query 'Subnets[0].SubnetId' --output text))

create-subnet:
	aws ec2 create-subnet --vpc-id $(shell jq -r '.Vpc.VpcId' vpc.json) \
	--cidr-block $(SUBNET_CIDR_BLOCK) --region $(REGION) --profile $(AWS_PROFILE) --output json > subnet.json

create-tags-subnet:
	aws ec2 create-tags --resources $(SUBNET_ID) \
	--tags Key=Name,Value=$(SUBNET_NAME) --region $(REGION) --profile $(AWS_PROFILE)
create-igw:
	aws ec2 create-internet-gateway --region $(REGION) --profile $(AWS_PROFILE) \
	--output json | tee igw.json

	
attach-igw:
	$(eval IGW_ID := $(shell jq -r '.InternetGateway.InternetGatewayId' igw.json))
	aws ec2 attach-internet-gateway --vpc-id $(shell jq -r '.Vpc.VpcId' vpc.json) \
	--internet-gateway-id $(IGW_ID) --region $(REGION) --profile $(AWS_PROFILE)


.PHONY: create-vpc create-tags-vpc retrieve-subnet-id create-subnet create-tags-subnet create-igw attach-igw
