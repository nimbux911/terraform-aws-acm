[![Maintained by Nimbux911](https://img.shields.io/badge/maintained%20by-nimbux911.com-%235849a6.svg)](https://www.nimbux911.com/)

# terraform-aws-acm
Terraform module to create ACM Certificates

The module will create a Cert, a Cert Validation and a Record Set in Route 53.

**NOTES:**

* To use this module, the Hosted Zone must be located in the same account where the certificate will be created

## Example:
```

module "acm_certificate" {
  source        = "../../terraform-aws-modules/terraform-aws-acm/"
  domain_name   = data.terraform_remote_state.route53.outputs.zone_name
  zone_name     = data.terraform_remote_state.route53.outputs.zone_name
  wildcard      = true
  environment   = var.environment
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| zone\_name | Route53 public zone name to use for ACM certificate. | string | `""` | yes |
| domain\_name | Domain to create for use the Certificate | string | `""`  | yes |
| environment | Environment, e.g. `prd`, `stg`, `dev` | string | `""` | no |
| wildcard |  | Specifies if should includea wildcard | bool | false | no |


## Outputs

| Name | Description |
|------|-------------|
| certificate\_arn | The arn of the certificate |
