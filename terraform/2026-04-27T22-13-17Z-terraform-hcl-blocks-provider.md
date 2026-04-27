# Terraform | HCL - Provider Block

Providers:
- main interface into some API that terraform can interact with (i.e. GCP, AWS, DigitalOcean, etc.)
- enables configuration & provisiong of resources

```terraform
# Configure the AWS provider.
provider "aws" {
    region = "us-east-1"
}

data "aws_availability_zones" "available" {}
data "aws_region" "current" {}

# Create a VPC.
resource "aws_vpc" "vpc" {
    cidr_block = var.vpc_cidr

    tags = {
        Name = "var.vpc_name
        Environment = "dev"
        Terraform = "true"
    }
}
```
