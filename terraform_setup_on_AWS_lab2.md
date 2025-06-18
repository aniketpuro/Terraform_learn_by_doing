
# 🇮🇳 Terraform on AWS: Beginner Lab 2 (Remote State + Secrets Manager)

Welcome to **Lab 2** of your hands-on journey with Terraform and AWS. In this lab, we’ll go beyond basic provisioning and introduce:
- 🔒 Secure secrets management
- 🪣 Remote state storage
- 🛠️ RDS provisioning using Terraform

---

## 🧠 Task Overview

### ✅ Task 1: Configure AWS Provider
To establish a connection between Terraform and AWS:

📄 Create a file: `provider.tf` inside the `terraform-projects` folder.

🔍 First, inspect:
```bash
cat /root/.aws/config
cat /root/.aws/credentials
````

✍️ Then create `provider.tf`:

```hcl
provider "aws" {
  region     = "us-east-1"
  access_key = "<aws_access_key_id>"
  secret_key = "<aws_secret_access_key>"
}
```

---

### ✅ Task 2: Create S3 Bucket for Remote State

📄 Create `main.tf` in the same folder.

💡 Bucket name must be globally unique.

```hcl
resource "aws_s3_bucket" "terraform_state" {
  bucket = "my-terraform-state-aniket123"  # Replace with your unique name
  acl    = "private"

  versioning {
    enabled = true
  }
}
```

🚀 Initialize and apply:

```bash
terraform init
terraform apply
```

---

### ✅ Task 3: Configure Remote Backend for State Storage

📄 Create a new file: `backend.tf`

```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state-aniket123"  # Your S3 bucket name
    key    = "terraform-state-file"
    region = "us-east-1"
  }
}
```

📌 *Don't apply this yet — Terraform will automatically configure it on `init`.*

---

### ✅ Task 4: Store DB Password in AWS Secrets Manager

💡 Use AWS CLI to securely create a secret:

```bash
aws secretsmanager create-secret \
  --name my-database-password \
  --secret-string "YourSecurePassword"
```

---

### ✅ Task 5: Provision RDS DB using Terraform + Secrets Manager

✍️ Append this to `main.tf`:

```hcl
data "aws_secretsmanager_secret_version" "database_password" {
  secret_id = "my-database-password"
}

resource "aws_db_instance" "my_secret_db" {
  identifier        = "rds-db-instance"
  allocated_storage = 20
  storage_type      = "gp2"
  engine            = "mysql"
  engine_version    = "5.7"
  instance_class    = "db.t3.micro"
  username          = "admin"
  password          = data.aws_secretsmanager_secret_version.database_password.secret_string
}
```

⚙️ Initialize, Plan, and Apply:

```bash
terraform init
terraform plan
terraform apply
```

⏳ *Note: RDS instances take a few minutes to provision.*

---

### ✅ Task 6: Verify Resources

📦 S3 Bucket:

* Go to your S3 bucket named `my-terraform-state-*`
* Check for a file with key: `terraform-state-file`
* Explore version history

🛢️ RDS Dashboard:

* Visit AWS Console → RDS
* Ensure your instance `rds-db-instance` is running

---

## 🧩 Outcome

You’ve successfully:

* Connected Terraform to AWS
* Created and used a secure S3 remote backend
* Stored secrets in AWS Secrets Manager
* Deployed an RDS MySQL instance securely using Terraform

---



