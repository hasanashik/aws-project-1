# Launch Kubernetes cluster using 3 VMs

CLUSTER_NAME := zaman-cluster

AWS_REGION := us-east-1

NODE_COUNT := 3

.PHONY: create-cluster

create-cluster:

    eksctl create cluster \\

        \--name=\$(CLUSTER_NAME) \\

        \--region=\$(AWS_REGION) \\

        \--nodegroup-name=standard-workers \\

        \--node-type=t3.medium \\

        \--nodes=\$(NODE_COUNT) \\

        \--nodes-min=\$(NODE_COUNT) \\

        \--nodes-max=\$(NODE_COUNT) \\

        \--managed

.PHONY: delete-cluster

delete-cluster:

    eksctl delete cluster \--name=\$(CLUSTER_NAME)
\--region=\$(AWS_REGION)

To run: make create-cluster

![](./image1.png){width="6.5in" height="3.165277777777778in"}

![](./image2.png){width="6.5in" height="2.707638888888889in"}

![](./image3.png){width="6.5in" height="3.035416666666667in"}
