# Selenium Terraform AWS Kubernetes  Integration (STAKI)

## Credits to EKS Getting Started Guide Configuration

This is the full configuration from https://www.terraform.io/docs/providers/aws/guides/eks-getting-started.html

See that guide for additional information.

NOTE: This full configuration utilizes the [Terraform Http provider](https://www.terraform.io/docs/providers/http/index.html) to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes master servers. Feel free to replace this as necessary.

## Credits to Execute Automation getting started Kubernetes tutorial

This is the full repo link https://github.com/executeautomation/kubernetes

## Prerequisite

1. Make sure that you have installed the kubectl locally

## Steps for configuring the selenium hub and node

1. Install the AWS CLI on local machine
    e.g. pip install awscli

2. Configure the AWS CLI (while configuration using AWS us-east-1 region as it is low cost)
    e.g. aws configure (provide the access key and the ID)

3. Install aws-iam-authenticator mentioned as below
    e.g. https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html

4. git clone https://github.com/omkarkhatavkar/selenium-terraform-aws-kubernetes.git

5. cd terraform_iac

6. terraform apply (this creates the aws eks cluster)

7. terraform output kubeconfig > ~/.kube/config

8. kubectl cluster-info (this should work)

9. cd ..

10. kubectl create -f selenium_deployment.yml

11. kubectl create -f service.yml

12. kubectl create -f selenium_node.yml

13. kubectl create -f cluster-autoscaler.yml

14. kubectl get pods (this should show you the list of the pods)

## Running the tests

1. update the selenium hub url in tests/test.py and then run python /tests/parallel.py

## YouTube Demo
https://youtu.be/uBOwc0BwbOs
