
![terraform-logo](https://github.com/vishnu1002/cmd-help/assets/145321614/93d621b4-3d48-42f4-99cd-abd40f247cd9)

Terraform is an infrastructure as code tool that lets you build, change, and version cloud and on-prem resources safely and efficiently.

With HashiCorp Terraform, you can specify on-premises and cloud resources in human-readable configuration files that you can share, reuse, and version. Terraform is an infrastructure as code tool. After that, you can provide and manage all of your infrastructure over the course of its lifetime using a standardized methodology. Both high-level elements like DNS records and SaaS features as well as low-level elements like processing, storage, and networking resources can be managed via Terraform.
Learn more [developer.hashicorp.com/terraform/intro](https://developer.hashicorp.com/terraform/intro)

*Youtube Video to learn more:*
- [# Terraform in 100 Seconds - Fireship](https://www.youtube.com/watch?v=tomUWcQ0P3k&t=13s)

## Terraform for AWS

### Prerequisites
Install **Terraform** for respective platform:
- [Install for Linux](https://developer.hashicorp.com/terraform/install#linux)
- [Install for macOS](https://developer.hashicorp.com/terraform/install#darwin)
- [Install for Windows](https://developer.hashicorp.com/terraform/install#windows)

Install **AWS CLI V2** for respective platform:
- [AWS CLI V2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

Create new access key:

-   [AWS account](https://aws.amazon.com/free)  and  [associated credentials](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html)  that allow you to create resources.

Verify the installation:

    terraform --version

    aws --version

## Authenticate the Terraform AWS provider

    aws configure

Provide the credentials:
 - `AWS Access Key ID [None]: <access-key>` 
 - `AWS Secret Access Key [None]: <secret-key>`
 - `Default region name [None]: <enter-keep-default>` 
 - `Default output format [None]: <enter-keep-default>`

### Write configuration

Each Terraform configuration must be in its own working directory.
Create directory for the congif and change directory:

    mkdir terraform-aws-instance

    cd terraform-aws-instance

Create new file `main.tf` and open in vscode

    code main.tf

## Define Terraform and AWS

> Make sure region "us-east-1" is given correctly or 

    terraform {
	    required_providers {
		    aws =  {
			    source  =  "hashicorp/aws"
			    version  =  "~> 4.16"
		    }
	    }
	    required_version =  ">= 1.2.0"
    }
    
    provider "aws" {
	    region =  "us-east-1"
    }

## Create AWS EC2 Instance

> - Make sure to prove the correct AMI ID from the currect region.
> - The given AMI ID is Ubuntu server in us-east-1 region.

        resource "aws_instance"  "tf_server" {
    	    ami =  "ami-080e1f13689e07408"
    	    instance_type =  "t2.micro"
    	    subnet_id =  aws_subnet.tf_subnet_1.id
    	    tags =  {
    		    Name  =  "tf_server"
    	    }
        }
  
  > EC2 will be create in the default VPC
    
### Initialize the directory

    terraform init

### Create infrastructure

    terraform apply
    
    yes

### List the created infrastructure

    terraform state list

### Destroy infrastructure

    terraform destroy
  
## Create Custom VPC with Subnet
 
    # Define custom VPC
    resource "aws_vpc" "tf-vpc" {
	    cidr_block = "10.0.0.0/24"
	    instance_tenancy = "default"
	    tags = {
		    Name = "tf_vpc"
	    }
    }
    
    # Define Subnet
    resource "aws_subnet" "tf_subnet_1" {
	    vpc_id = aws_vpc.tf-vpc.id
	    cidr_block = "10.0.0.0/25"
	    availability_zone = "us-east-1a"
	    tags = {
		    Name = "tf_subnet_1"
	    }
    }


## Create Output file

Create new file `outputs.tf` in the same directory

    output "instance_id" {
	    description = "EC2 ID: "
	    value = aws_instance.tf_server.id
    }
    
    output "instance_public_ip" {
	    description = "EC2 Public IP: "
	    value = aws_instance.tf_server.public_ip
    }
    
    output "instance_host_id" {
	    description = "EC2 Host ID: "
	    value = aws_instance.tf_server.host_id
    }
    
    output "instance_subnet_id" {
	    description = "EC2 Subnet ID: "
	    value = aws_instance.tf_server.subnet_id
    }

To view the output, either run `terraform apply` or

    terraform output

