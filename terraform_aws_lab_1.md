

---

# 🇮🇳 Terraform on AWS: Beginner Lab 1 (Learn by Doing)

**Welcome to the first hands-on lab on Terraform with AWS.**
This is designed specifically for **Indian tech learners** who want to build practical **DevOps** and **Cloud** skills through real-world tasks.

---

## 🔧 TASKS

### ✅ Task 1: Install Terraform (v1.8.5)

Install Terraform version `1.8.5` on your local machine (Linux preferred).

```bash
# Download Terraform
curl -LO https://releases.hashicorp.com/terraform/1.8.5/terraform_1.8.5_linux_amd64.zip

# Unzip
unzip terraform_1.8.5_linux_amd64.zip -d terraform_1.8.5

# Move to /usr/local/bin
sudo mv terraform_1.8.5/terraform /usr/local/bin/

# Verify
terraform version
```

---

### ✅ Task 2: Configure AWS Provider

Create a folder named `terraform-projects`. Inside it, create a file (e.g., `provider.tf`) to configure your AWS provider.

Fill in the values for:

* `region`
* `access_key`
* `secret_key`

👉 **Hint:** Check these using:

```bash
cat ~/.aws/config
cat ~/.aws/credentials
```

**Sample:**

```hcl
provider "aws" {
  region     = "us-east-1"
  access_key = "YOUR_ACCESS_KEY"
  secret_key = "YOUR_SECRET_KEY"
}
```

---

### ✅ Task 3: Create a Terraform Configuration File

Create a `main.tf` file inside the `terraform-projects` folder.

This should define:

* One EC2 instance with name `ec2_instance`
* AMI ID: `ami-01b799c439fd5516a`
* Instance type: `t2.micro`

**main.tf:**

```hcl
resource "aws_instance" "ec2_instance" {
  ami           = "ami-01b799c439fd5516a"
  instance_type = "t2.micro"
}
```

---

### ✅ Task 4: Initialize Terraform

Navigate to the project directory and run:

```bash
cd terraform-projects
terraform init
```

---

### ✅ Task 5: Plan and Apply

Execute the following:

```bash
terraform plan
terraform apply
```

Then, verify the EC2 instance using:

```bash
aws ec2 describe-instances --region us-east-1
```

---

### ✅ Task 6: Verify via Console

Login to the AWS Management Console and navigate to:

👉 [EC2 Dashboard](https://console.aws.amazon.com/ec2)

✅ Make sure your instance is in the **running** state.

---

## 📷 Terraform Architecture Diagram

![Terraform AWS Diagram](https://res.cloudinary.com/dezmljkdo/image/upload/v1719562349/LBD/ocmc1upuyd9aqni7oskh.png)



