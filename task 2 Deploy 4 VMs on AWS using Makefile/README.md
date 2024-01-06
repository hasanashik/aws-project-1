# Deploying 4 VMs on AWS using Makefile

**To run the makefile:**

- Define necessary variables:

    ```makefile
    AWS_PROFILE = default
    REGION = us-east-1
    INSTANCE_TYPE = t2.micro
    AMI_ID := $(shell aws ec2 describe-images --owners amazon --filters "Name=architecture,Values=x86_64" "Name=root-device-type,Values=ebs" "Name=virtualization-type,Values=hvm" --query "Images[0].ImageId" --output text)
    ```

- Create a key-pair

![image1](./image1.png)

- Copy the previously generated vpc.json file into this directory

- Get subnet ID and create VM-1

![image2](./image2.png)

- Similarly create other VMs using:

    ```makefile
    make create-instance-2
    make create-instance-3
    make create-instance-4
    ```

![image3](./image3.png)
