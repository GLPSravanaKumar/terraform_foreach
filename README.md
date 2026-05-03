# Terraform Foreach

## Project Description
This project demonstrates the usage of the `for_each` construct in Terraform. It provides a comprehensive guide on how to effectively utilize `for_each` to manage resources dynamically in your infrastructure as code.

## Setup Instructions
1. **Prerequisites**: Ensure you have Terraform installed. You can download it from [terraform.io](https://www.terraform.io/downloads.html).
2. **Clone the Repository**:
   ```bash
   git clone https://github.com/GLPSravanaKumar/terraform_foreach.git
   cd terraform_foreach
   ```
3. **Initialize Terraform**:
   ```bash
   terraform init
   ```

## Usage Examples
### Example 1: Creating Multiple Instances
```hcl
variable "instance_count" {
  default = 3
}

resource "aws_instance" "example" {
  count         = var.instance_count
  ami           = "ami-0c55b159cbfafe01e"
  instance_type = "t2.micro"
}
```

### Example 2: Using for_each with Maps
```hcl
variable "availability_zones" {
  default = {"az1" = "us-east-1a", "az2" = "us-east-1b"}
}

resource "aws_instance" "example" {
  for_each = var.availability_zones
  ami           = "ami-0c55b159cbfafe01e"
  instance_type = "t2.micro"
  availability_zone = each.value
}
```

## Best Practices
- **Use for_each over count**: Prefer `for_each` when working with maps or sets for better readability.
- **Consistent Naming**: Ensure that resource names are consistent and follow a naming convention to avoid confusion when utilizing multiple resources.
- **Reference with each.key**: When accessing keys in `for_each`, use the `each.key` syntax to ensure clarity in your code.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

---
Date created: 2026-05-03 07:02:04 UTC
