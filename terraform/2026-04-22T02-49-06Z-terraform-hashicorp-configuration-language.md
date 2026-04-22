# Terrform | Hashicorp Configuration Language

HCL:
- machine & human readable config language
- used for provisioning "infrastructure" (i.e. cloud resources, firewalls, networking, DB, etc.)

```hcl
<BLOCK TYPE> "<BLOCK LABEL>" "<BLOCK LABEL>" {
    # Block body
    <IDENTIFIER> = <EXPRESSION> # Argument
}


resource "aws_instance" "web_server" {
    ami             = "ami-04d29b"          # Amazon machine image
    instance_type   = var.instance_type     # Arg w/ value as expression
}
```

Block Types:
1. Settings
2. Provider
3. Resource
4. Data
5. Input Variables
6. Local Variables
7. Output Values
8. Modules

