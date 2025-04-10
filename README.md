# terraform-simple-project
#  Terraform Project: AWS EC2 Instance Setup

##  Project Structure

```bash
terraform/
├── main.tf              # EC2 resource definition
├── providers.tf         # AWS provider configuration
├── terraform.tfstate    # Terraform state file (auto-generated)
```
## Requirements
 Terraform CLI Installation
➡️ Install Guide:  
[Terraform CLI Installation Guide](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

##   AWS CLI installed & configured
# . Download installer
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install
```
## Configure AWS CLI Credentials
```
aws configure
```
Required values:

    AWS Access Key ID

    AWS Secret Access Key

    Default region name (ap-southeast-1)

    Default output format (json)
   

## 📄 main.tf

```hcl
resource "aws_instance" "lab-server" {
  ami           = "ami-01938df366ac2d954" # Amazon Linux 2 AMI
  instance_type = "t2.micro"

  tags = {
    Name = "WebAppServer"
  }
}
```
## 📄 providers.tf

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "ap-southeast-1"
}

```
## Terraform Commands deploy
```
# Initialize Terraform project (download providers, create .terraform dir)
terraform init

# See what changes will be made before applying
terraform plan

# Apply configuration and create resources
terraform apply

# Apply without manual approval
terraform apply -auto-approve

# Destroy resources manually
terraform destroy

# Destroy without asking
terraform destroy -auto-approve

```
