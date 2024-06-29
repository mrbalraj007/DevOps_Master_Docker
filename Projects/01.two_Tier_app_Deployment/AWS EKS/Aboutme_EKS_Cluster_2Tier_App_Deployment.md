# Two-tier Application Deployment on AWS EKS

- + Prerequisites for AWS EKS
    - Should have a AWS Account
    - Should have AWS CLI install on machine
    - Should have IAM roles for EKS

* On-Prem Let Setup

| Hostname | IP Address | OS |
|-----------------|-----------------|-----------------|
| eks  | 192.168.1.103  | Ubuntu 24.04 LTS  |

* Install AWS Cli on ```eks```machine. [ref link](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
```yaml
sudo apt update -y
sudo apt install curl -y
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update # we can move to binary so that it can be accessible anywhere.
```
![alt text](image.png)

### Create an IAM Role for EKS
  - Create an IAM role with the necessary permissions for EKS.
    01. ___Create an IAM User__:
        * Go to the AWS IAM console.
        * Create a new IAM user named ```eks-cli-admin.```
        * Attach the ```AdministratorAccess``` policy to this user.
    02. Create Security Credentials:
        * After creating the user, generate an ```Access``` and ```Secret Access``` Key for ``eks-cli-admin`` user.

### Configure AWS:
![alt text](image-1.png)

* Will try to access the S3 
```sh
$ aws s3 ls
```

## Kubectl is a tool you use from the command line to work with Kubernetes clusters. It helps you manage and control the different parts of your Kubernetes system.

With Kubectl, you can do things like:

- Deploy applications
- Check and update cluster resources
- Scale up or down your deployments
- Troubleshoot problems

### Kubernetes tools setup: 

01. Will install the ```kubectl``` on machine. [Ref Link](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
# for AWS machine you can use (curl -o kubectl https://amazon-eks.s3.us-west2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl )
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
```
* Test to ensure the version you installed is up-to-date:
```sh
kubectl version --client

or

use this for detailed view of version:

kubectl version --client --output=yaml
```
![alt text](image-2.png)

02. Install ```eksctl``` tool: [Ref Link](https://docs.aws.amazon.com/emr/latest/EMR-on-EKS-DevelopmentGuide/setting-up-eksctl.html)

```sh
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```
![alt text](image-3.png)

```sh
$ eksctl version
0.183.0
```

03. Will setup ```EKS Cluster``` Setup now:

- Use eksctl to create the EKS cluster

```sh
eksctl create cluster --name demo-singh-eks --region us-east-1 --node-type t2.micro --nodes-min 2 --nodes-max 3

```
__NOTE__: Make sure to replace ```<cluster-name>``` and ```<region>``` when execute the command.

__*Note__:* Clustering will take approximately ```20–30``` minutes to create a cluster.

![alt text](image-4.png)

