

🇮🇳 Terraform on AWS: Beginner Lab 1 (Learn by Doing)
Welcome to the first hands-on lab on Terraform with AWS. This is designed for Indian tech learners who want to build practical DevOps and cloud skills through real tasks.

🔧 TASKS
✅ Task 1: Install Terraform (v1.8.5)
Download and install Terraform version 1.8.5 on your local machine (Linux preferred).
Once installed, verify the version.

✅ Task 2: Configure AWS Provider
Inside a folder named terraform-projects, create a file to configure your AWS provider.
Fill in values for:

region

access_key

secret_key

👉 Hint: Check your credentials inside ~/.aws/config and ~/.aws/credentials.

✅ Task 3: Create a Terraform Configuration File
Inside the same terraform-projects folder, create a file named main.tf.

It should define:

One EC2 instance with name ec2_instance

Use this AMI ID: ami-01b799c439fd5516a

Use instance type: t2.micro

Just create the file in this task.

✅ Task 4: Initialize Terraform
Inside the folder with your .tf files, initialize Terraform.

✅ Task 5: Plan and Apply
Run the Terraform commands to:

Plan the changes

Apply and provision your EC2 instance

Once applied, verify the instance using the AWS CLI.

✅ Task 6: Console Verification
Go to AWS EC2 Dashboard
Check that the EC2 instance is in a running state.

✅ SOLUTIONS (Check After Attempting)
✔️ Task 1 Solution:
bash
Copy
Edit
curl -LO https://releases.hashicorp.com/terraform/1.8.5/terraform_1.8.5_linux_amd64.zip
unzip terraform_1.8.5_linux_amd64.zip -d terraform_1.8.5
mv terraform_1.8.5/terraform /usr/local/bin/
terraform version
✔️ Task 2 Solution:
Inspect credentials:

bash
Copy
Edit
cat /root/.aws/config
cat /root/.aws/credentials
Create provider.tf:

hcl
Copy
Edit
provider "aws" {
  region     = "us-east-1"
  access_key = "YOUR_ACCESS_KEY"
  secret_key = "YOUR_SECRET_KEY"
}
✔️ Task 3 Solution:
Create main.tf:

hcl
Copy
Edit
resource "aws_instance" "ec2_instance" {
  ami           = "ami-01b799c439fd5516a"
  instance_type = "t2.micro"
}
✔️ Task 4 Solution:
bash
Copy
Edit
cd terraform-projects
terraform init
✔️ Task 5 Solution:
bash
Copy
Edit
terraform plan
terraform apply
aws ec2 describe-instances --region us-east-1
✔️ Task 6 Solution:
Visit:
👉 https://console.aws.amazon.com/ec2
Navigate to EC2 Dashboard and confirm that the instance is running.
