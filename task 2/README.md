# Terraform Task: VPC, Subnet, and EC2 Instance Creation

In this task, we create an AWS VPC, a subnet, and an EC2 instance using a modular approach. It separates resources into individual modules (`vpc`, `subnet`, and `ec2`) and uses variable files to customize deployments.

---

## Directory Structure


```bash
Task2/
│
├── modules/
│   ├── vpc/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── subnet/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── ec2/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
│
├── main.tf
├── variables.tf
├── terraform.tfvars
└── outputs.tf
```

## Step 1: Setting Up the Child Modules
###  VPC Module

- **`main.tf`** – Creates a VPC using the provided CIDR block and name
- **`variables.tf`** – Declares input variables like `cidr_block`, `name` etc.
- **`outputs.tf`** – Outputs the created VPC's ID


###  EC2 Module

- **`main.tf`** – Launches an EC2 instance with the given config.  
- **`variables.tf`** – Declares variables like `ami`, `instance_type`, `subnet_id`, and `name`.  
- **`outputs.tf`** – Outputs the EC2 instance ID.


###  Subnet Module

- **`main.tf`** – Creates a subnet in the specified VPC with the given CIDR and AZ  
- **`variables.tf`** – Declares input variables like `vpc_id`, `cidr_block` etc.  
- **`outputs.tf`** – Outputs the created Subnet ID

## Step 2: Setting Up the Root Module
###  Root Module

- **`main.tf`** – Calls child modules (VPC, Subnet, EC2) and passes variables  
- **`variables.tf`** – Declares input variables (region, VPC/Subnet/EC2 configs)  
- **`terraform.tfvars`** – Assigns actual values to the declared variables
- **`outputs.tf`** – Outputs VPC ID, Subnet ID, EC2 instance ID, and public IP


## Step 3: Executing the Configurations 


### 1. Initialize the project
```bash
terraform init
```

### 2. Validate the configuration
```bash
terraform validate
```

### 3. Preview the changes
```bash
terraform plan
```

### 4.Apply the changes
```bash
terraform apply -auto-approve
```

### 5. Destroy resources (optional)
```bash
terraform destroy -auto-approve
```
![image](https://github.com/user-attachments/assets/a60ad9d3-1e83-48c9-af6b-3a0c9fb358bb)
