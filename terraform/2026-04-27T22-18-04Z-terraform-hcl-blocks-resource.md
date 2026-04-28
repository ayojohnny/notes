# Terraform | HCL - Resource Block

Resource
- anything that is exposed by the underlying provider's API (DNS records, firewalls, storage buckets, compute, etc.)
- deployed via `resource blocks`

Resource Block is the only block that creates infrastructure. All other blocks (provider, terraform, etc.)
are "supporting blocks". If I had a TF file with now resource blocks, then no resources would actually
be deployed.


Example of "resources" exposed from the AWS provider (for TF), mapped to AWS infrastructure

Resource    | AWS Provider          | AWS Infrastructure
--          | --                    | --
1           | aws_instance          | EC2 instance
2           | aws_security_group    | Security Groupd
3           | aws_s3_bucket         | Amazon S3 Bucket (Block storage)
4           | aws_key_pair          | EC2 Key Pair

```terraform
resource "aws_route_table" "public_route_table" {
    vpc_id = aws_vpc.vpc.id

    route {
        cidr_block = "0.0.0.0/0"
        gateway_id = aws_internet_gateway.internet_gateway.id
        # nat_gateway_id = aws_nat_gateway.nat_gateway.id
    }

    tags = {
        Name = "demo_route_table_public"
        Terraform = "true"
    }
}
```

```terraform
# Using random number to make globally unique S3 buckets.
resource "aws_s3_bucket" "my_bucket" {
    bucket = "my-globally-unqiue-bucket-${random_id.randomness.hex}"
    
    tags = {
        Name = "My S3 Bucket"
        Purpise = "Testing TF + S3 buckets"
    }
}

resource "aws_s3_bucket_acl" "my_new_bucket_acl" {
    bucket = aws_s3_bucket.my_bucket.id
    acl = "private"
}

random "random_id" "randomness" {
    byte_length = 16
}
```
