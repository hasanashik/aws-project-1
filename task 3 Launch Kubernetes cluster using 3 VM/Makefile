CLUSTER_NAME := zaman-cluster
AWS_REGION := us-east-1
NODE_COUNT := 3

.PHONY: create-cluster
create-cluster:
	eksctl create cluster \
		--name=$(CLUSTER_NAME) \
		--region=$(AWS_REGION) \
		--nodegroup-name=standard-workers \
		--node-type=t3.medium \
		--nodes=$(NODE_COUNT) \
		--nodes-min=$(NODE_COUNT) \
		--nodes-max=$(NODE_COUNT) \
		--managed

.PHONY: delete-cluster
delete-cluster:
	eksctl delete cluster --name=$(CLUSTER_NAME) --region=$(AWS_REGION)
