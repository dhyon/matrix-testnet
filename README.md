# Matrix Test Networks

Deploy and configure a remote, Tendermint-flavored Matrix testnet on AWS. Let's use an Ansible playbook to trigger Terraform.

### Requirements

* An [AWS](https://aws.amazon.com/) account
* [AWS CLI](https://aws.amazon.com/cli/)
* [Terraform](https://www.terraform.io/)
* Ansible

### AWS Setup

```bash
# First make sure you set up your AWS access and secret keys via CLI
aws configure
```
Create your own keypair and upload it to all the supported regions:
* us-east-1
* us-east-2
* us-west-1
* ap-northeast-2
* ap-southeast-2
* eu-central-1
* eu-west-1

Note: There exists an AWS test keypair already on all the supported regions. If you're my friend I'll send it to you in private.

### Configuration

Configure the number of nodes in each region, keypair_name, instance_types and more in the root main.tf file.

### Initialize Terraform modules
```bash
terraform init
```

### Deploy the network

```bash
ansible-playbook deploy.yaml
```

This command will:
1. Create the necessary AWS EC2 resources in each region (using Terraform).
2. On the first (0th) node, install requirements and initialize the network (with Starport)
3. On the rest of the nodes, install the app binary, do configurations and join the network [WIP]

You can also only run the deploy:
```bash
terraform apply
```

Check what's deployed:
```
terraform output
```

### Destroy the network

```bash
terraform destroy
```

### Logs

[WIP]

### Monitoring + Metrics

[WIP]