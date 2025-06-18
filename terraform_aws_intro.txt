🚀 Introduction to Terraform on AWS

Welcome to the first lab of this completely hands-on course,
Learn by Doing - AWS Workshop with Terraform: Hands-On Cloud Infrastructure Management!

In this lab, we'll introduce you to the world of IaC with Terraform and explore the powerful combination of AWS with Terraform.

Navigating the Lab Environment:

Overview Tab: You are here! This is your starting point, with detailed information on the lab's topic. Make sure to review it thoroughly before moving on to the tasks.

Tasks Tab: When you're ready to put your knowledge to the test, switch to the Tasks tab. You'll find a mix of multiple-choice questions and hands-on tasks.

Toggle Panel Size: Click this to access the Terminal easily.

What is Terraform?

Terraform is an open-source infrastructure as code (IaC) tool developed by HashiCorp that allows users to define and provision infrastructure using a high-level configuration language.

It is powerful in managing cloud services, with AWS being one of the most widely used platforms with Terraform.

Benefits of Infrastructure as Code (IaC):

Infrastructure as Code (IaC) is a DevOps practice where infrastructure is managed through code files instead of manual setup.

Benefits include:
- Automation: Reduces manual deployment work.
- Consistency: Avoids "it works on my machine" issues.
- Version Control: Tracks changes, supports rollback.
- Cost Savings: Saves time and reduces management overhead.

Terraform Workflow:

1. Create: Write `.tf` configuration files.
2. Plan: Run `terraform plan` to preview changes.
3. Apply: Run `terraform apply` to provision resources.
4. Destroy: Run `terraform destroy` to clean up resources.

Basic Commands:
terraform init
terraform plan
terraform apply
terraform destroy

Managing AWS Services with Terraform:

Terraform uses providers to interact with services. The AWS provider enables managing AWS resources.

Example Provider Block:
provider "aws" {
  region     = "us-west-2"
  access_key = "your_access_key"
  secret_key = "your_secret_key"
}

Example EC2 Resource:
resource "aws_instance" "example" {
  ami           = "ami-01b799c439fd5516a"
  instance_type = "t2.micro"
}

AWS Services Managed by Terraform:
- EC2 Instances
- S3 Buckets
- VPCs and Networking
- IAM Roles and Policies
- DynamoDB
- Lambda Functions

Terraform Configuration Language (HCL):

HCL is Terraform's configuration language, designed to describe infrastructure declaratively.

Key Components:
- Resources: Actual infrastructure elements.
- Providers: Define the service (like AWS).
- Variables: Make configs dynamic and reusable.

Example Variable and Resource:
variable "instance_type" {
  description = "EC2 instance type"
  default     = "t2.micro"
}

resource "aws_instance" "my_instance" {
  ami           = "ami-01b799c439fd5516a"
  instance_type = var.instance_type
}

Structure of a Terraform Configuration File:
- Provider Configuration
- Resource Definitions
- Optional Variables
- Output Values

Conclusion:

Terraform makes managing AWS infrastructure more consistent, automated, and efficient through code. It's ideal for both simple deployments and complex environments.

What's Next?

Go to the Tasks tab to begin hands-on practice with Terraform and AWS.
