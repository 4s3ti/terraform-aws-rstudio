# ezRStudio

[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) 

ezRStudio uses terraform and a set of pre-build cloud specific server images to create all the required resources on AWS and get you up and running with RStudio server on an instance with the specs you need.

With ezRStudio you don't need to worry about learning all the AWS specifics and repeat the same steps over and over again every time you want to start or stop your server. 

Its fully customizable and You can define what types of servers and images you want to use, however by default this are the resources it spins up for you

* VPC
* SSH Key Pair
* Security group
* EC2 Instance
    * rstudio AMI: g4dn.xlarge (This AMI only supports instances with Graphics cards)
    * relevancelab AMI: t2.large (This AMI only supports t2.large instances)
    * Custom AMI: t3.micro

There are multiple ways you can use ezRStudio

* locally on your machine with [terraform](https://www.terraform.io/)
* [terraform cloud](https://cloud.hashicorp.com/products/terraform)
* [env0](https://www.env0.com/)
* As part of another module


**NOTE:** Please be aware this is not intended to be used in production and secure environments. All the AWS Cloud images (AMI) are provided as is by 3rd parties and I assume no responsability over any costs.

# Support & Feedback

Feel free to open github issue with your questions or suggestions.

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.13.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~>4.28.0 |
| <a name="requirement_tls"></a> [tls](#requirement\_tls) | 3.4.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 4.28.0 |
| <a name="provider_tls"></a> [tls](#provider\_tls) | 3.4.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_ec2_instance"></a> [ec2\_instance](#module\_ec2\_instance) | terraform-aws-modules/ec2-instance/aws | ~> 3.0 |
| <a name="module_key_pair"></a> [key\_pair](#module\_key\_pair) | terraform-aws-modules/key-pair/aws | >=2.0.0 |
| <a name="module_rstudio_sg"></a> [rstudio\_sg](#module\_rstudio\_sg) | terraform-aws-modules/security-group/aws | ~> 4.9.0 |
| <a name="module_vpc"></a> [vpc](#module\_vpc) | terraform-aws-modules/vpc/aws | >=3.14.2 |

## Resources

| Name | Type |
|------|------|
| [tls_private_key.this](https://registry.terraform.io/providers/hashicorp/tls/3.4.0/docs/resources/private_key) | resource |
| [aws_ami.relevance](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ami) | data source |
| [aws_ami.rstudio](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ami) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_ami_type"></a> [ami\_type](#input\_ami\_type) | Type of AMI to use, cuda, tensorflow, custom | `string` | `"rstudio"` | no |
| <a name="input_az"></a> [az](#input\_az) | Availability zone to place the instance at | `string` | `null` | no |
| <a name="input_create_key"></a> [create\_key](#input\_create\_key) | Defines if ssh privatekey is going to be created | `bool` | `true` | no |
| <a name="input_custom_ami"></a> [custom\_ami](#input\_custom\_ami) | Custom AMI Id to be used | `any` | `null` | no |
| <a name="input_instance_type"></a> [instance\_type](#input\_instance\_type) | The type of ec2 instance to be used | `string` | `"t3.micro"` | no |
| <a name="input_key_name"></a> [key\_name](#input\_key\_name) | The ssh keypair name | `string` | `"RSTudio-SSH"` | no |
| <a name="input_monitoring"></a> [monitoring](#input\_monitoring) | enables monitoring on the instance | `bool` | `false` | no |
| <a name="input_region"></a> [region](#input\_region) | Region to place resources | `string` | `"eu-central-1"` | no |
| <a name="input_rstudio_instance_type"></a> [rstudio\_instance\_type](#input\_rstudio\_instance\_type) | Instance type to be used by rstudio AMI, use only GPU instances | `string` | `"g4dn.xlarge"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_address"></a> [address](#output\_address) | n/a |
| <a name="output_dns_name"></a> [dns\_name](#output\_dns\_name) | n/a |
| <a name="output_instance_id"></a> [instance\_id](#output\_instance\_id) | n/a |
| <a name="output_ip_address"></a> [ip\_address](#output\_ip\_address) | n/a |
<!-- END_TF_DOCS -->

# Contribute

Suggestions and Pull Requests are always welcome. 
If you find a bug or run into any issues, feel free to open an Issue and I will help you as soon as possible. 


If you like this project and you want to contribute in a different way, you can always consider to:

[![BuyMeCoffee](https://cdn.buymeacoffee.com/buttons/default-yellow.png)](https://www.buymeacoffee.com/4s3ti)