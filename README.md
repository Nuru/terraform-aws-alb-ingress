<!-- markdownlint-disable -->
# terraform-aws-alb-ingress [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-alb-ingress.svg)](https://github.com/cloudposse/terraform-aws-alb-ingress/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)
<!-- markdownlint-restore -->

[![README Header][readme_header_img]][readme_header_link]

[![Cloud Posse][logo]](https://cpco.io/homepage)

<!--




  ** DO NOT EDIT THIS FILE
  **
  ** This file was automatically generated by the `build-harness`.
  ** 1) Make all changes to `README.yaml`
  ** 2) Run `make init` (you only need to do this once)
  ** 3) Run`make readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **





-->

Terraform module to provision an HTTP style ALB ingress based on hostname and/or path.

ALB ingress can be provisioned without authentication, or using Cognito or OIDC authentication.


---

This project is part of our comprehensive ["SweetOps"](https://cpco.io/sweetops) approach towards DevOps.
[<img align="right" title="Share via Email" src="https://docs.cloudposse.com/images/ionicons/ios-email-outline-2.0.1-16x16-999999.svg"/>][share_email]
[<img align="right" title="Share on Google+" src="https://docs.cloudposse.com/images/ionicons/social-googleplus-outline-2.0.1-16x16-999999.svg" />][share_googleplus]
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on Reddit" src="https://docs.cloudposse.com/images/ionicons/social-reddit-outline-2.0.1-16x16-999999.svg" />][share_reddit]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]


[![Terraform Open Source Modules](https://docs.cloudposse.com/images/terraform-open-source-modules.svg)][terraform_modules]



It's 100% Open Source and licensed under the [APACHE2](LICENSE).







We literally have [*hundreds of terraform modules*][terraform_modules] that are Open Source and well-maintained. Check them out!







## Security & Compliance [<img src="https://cloudposse.com/wp-content/uploads/2020/11/bridgecrew.svg" width="250" align="right" />](https://bridgecrew.io/)

Security scanning is graciously provided by Bridgecrew. Bridgecrew is the leading fully hosted, cloud-native solution providing continuous Terraform security and compliance.

| Benchmark | Description |
|--------|---------------|
| [![Infrastructure Security](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/general)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=INFRASTRUCTURE+SECURITY) | Infrastructure Security Compliance |
| [![CIS KUBERNETES](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/cis_kubernetes)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=CIS+KUBERNETES+V1.5) | Center for Internet Security, KUBERNETES Compliance |
| [![CIS AWS](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/cis_aws)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=CIS+AWS+V1.2) | Center for Internet Security, AWS Compliance |
| [![CIS AZURE](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/cis_azure)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=CIS+AZURE+V1.1) | Center for Internet Security, AZURE Compliance |
| [![PCI-DSS](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/pci)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=PCI-DSS+V3.2) | Payment Card Industry Data Security Standards Compliance |
| [![NIST-800-53](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/nist)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=NIST-800-53) | National Institute of Standards and Technology Compliance |
| [![ISO27001](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/iso)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=ISO27001) | Information Security Management System, ISO/IEC 27001 Compliance |
| [![SOC2](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/soc2)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=SOC2)| Service Organization Control 2 Compliance |
| [![CIS GCP](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/cis_gcp)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=CIS+GCP+V1.1) | Center for Internet Security, GCP Compliance |
| [![HIPAA](https://www.bridgecrew.cloud/badges/github/cloudposse/terraform-aws-alb-ingress/hipaa)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=cloudposse%2Fterraform-aws-alb-ingress&benchmark=HIPAA) | Health Insurance Portability and Accountability Compliance |



## Usage


**IMPORTANT:** We do not pin modules to versions in our examples because of the
difficulty of keeping the versions in the documentation in sync with the latest released versions.
We highly recommend that in your code you pin the version to the exact version you are
using so that your infrastructure remains stable, and update versions in a
systematic way so that they do not catch you by surprise.

Also, because of a bug in the Terraform registry ([hashicorp/terraform#21417](https://github.com/hashicorp/terraform/issues/21417)),
the registry shows many of our inputs as required when in fact they are optional.
The table below correctly indicates which inputs are required.


For a complete example, see [examples/complete](examples/complete).

For automated test of the complete example using `bats` and `Terratest`, see [test](test).

```hcl
provider "aws" {
  region = var.region
}

module "vpc" {
  source     = "git::https://github.com/cloudposse/terraform-aws-vpc.git?ref=tags/0.8.1"
  namespace  = var.namespace
  stage      = var.stage
  name       = var.name
  delimiter  = var.delimiter
  attributes = var.attributes
  cidr_block = var.vpc_cidr_block
  tags       = var.tags
}

module "subnets" {
  source               = "git::https://github.com/cloudposse/terraform-aws-dynamic-subnets.git?ref=tags/0.16.1"
  availability_zones   = var.availability_zones
  namespace            = var.namespace
  stage                = var.stage
  name                 = var.name
  attributes           = var.attributes
  delimiter            = var.delimiter
  vpc_id               = module.vpc.vpc_id
  igw_id               = module.vpc.igw_id
  cidr_block           = module.vpc.vpc_cidr_block
  nat_gateway_enabled  = false
  nat_instance_enabled = false
  tags                 = var.tags
}

module "alb" {
  source                                  = "git::https://github.com/cloudposse/terraform-aws-alb.git?ref=tags/0.7.0"
  namespace                               = var.namespace
  stage                                   = var.stage
  name                                    = var.name
  attributes                              = var.attributes
  delimiter                               = var.delimiter
  vpc_id                                  = module.vpc.vpc_id
  security_group_ids                      = [module.vpc.vpc_default_security_group_id]
  subnet_ids                              = module.subnets.public_subnet_ids
  internal                                = var.internal
  http_enabled                            = var.http_enabled
  access_logs_enabled                     = var.access_logs_enabled
  alb_access_logs_s3_bucket_force_destroy = var.alb_access_logs_s3_bucket_force_destroy
  cross_zone_load_balancing_enabled       = var.cross_zone_load_balancing_enabled
  http2_enabled                           = var.http2_enabled
  idle_timeout                            = var.idle_timeout
  ip_address_type                         = var.ip_address_type
  deletion_protection_enabled             = var.deletion_protection_enabled
  deregistration_delay                    = var.deregistration_delay
  health_check_path                       = var.health_check_path
  health_check_timeout                    = var.health_check_timeout
  health_check_healthy_threshold          = var.health_check_healthy_threshold
  health_check_unhealthy_threshold        = var.health_check_unhealthy_threshold
  health_check_interval                   = var.health_check_interval
  health_check_matcher                    = var.health_check_matcher
  target_group_port                       = var.target_group_port
  target_group_target_type                = var.target_group_target_type
  tags                                    = var.tags
}

module "alb_ingress" {
  source = "cloudposse/alb-ingress/aws"
  # Cloud Posse recommends pinning every module to a specific version
  # version     = "x.x.x"
  namespace                           = var.namespace
  stage                               = var.stage
  name                                = var.name
  attributes                          = var.attributes
  delimiter                           = var.delimiter
  vpc_id                              = module.vpc.vpc_id
  authentication_type                 = var.authentication_type
  unauthenticated_priority            = var.unauthenticated_priority
  unauthenticated_paths               = var.unauthenticated_paths
  slow_start                          = var.slow_start
  stickiness_enabled                  = var.stickiness_enabled
  default_target_group_enabled        = false
  target_group_arn                    = module.alb.default_target_group_arn
  unauthenticated_listener_arns       = [module.alb.http_listener_arn]
  tags                                = var.tags
}
```






<!-- markdownlint-disable -->
## Makefile Targets
```text
Available targets:

  help                                Help screen
  help/all                            Display help for all targets
  help/short                          This help short screen
  lint                                Lint terraform code

```
<!-- markdownlint-restore -->
<!-- markdownlint-disable -->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13.0 |
| aws | >= 2.42 |
| local | >= 1.3 |
| null | >= 2.0 |
| template | >= 2.0 |

## Providers

| Name | Version |
|------|---------|
| aws | >= 2.42 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| this | cloudposse/label/null | 0.24.1 |

## Resources

| Name |
|------|
| [aws_lb_listener_rule](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb_listener_rule) |
| [aws_lb_target_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/lb_target_group) |
| [aws_lb_target_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb_target_group) |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| additional\_tag\_map | Additional tags for appending to tags\_as\_list\_of\_maps. Not added to `tags`. | `map(string)` | `{}` | no |
| attributes | Additional attributes (e.g. `1`) | `list(string)` | `[]` | no |
| authenticated\_hosts | Authenticated hosts to match in Hosts header | `list(string)` | `[]` | no |
| authenticated\_listener\_arns | A list of authenticated ALB listener ARNs to attach ALB listener rules to | `list(string)` | `[]` | no |
| authenticated\_paths | Authenticated path pattern to match (a maximum of 1 can be defined) | `list(string)` | `[]` | no |
| authenticated\_priority | The priority for the rules with authentication, between 1 and 50000 (1 being highest priority). Must be different from `unauthenticated_priority` since a listener can't have multiple rules with the same priority | `number` | `0` | no |
| authentication\_cognito\_scope | Cognito scope, which should be a space separated string of requested scopes (see https://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims) | `string` | `null` | no |
| authentication\_cognito\_user\_pool\_arn | Cognito User Pool ARN | `string` | `""` | no |
| authentication\_cognito\_user\_pool\_client\_id | Cognito User Pool Client ID | `string` | `""` | no |
| authentication\_cognito\_user\_pool\_domain | Cognito User Pool Domain. The User Pool Domain should be set to the domain prefix (`xxx`) instead of full domain (https://xxx.auth.us-west-2.amazoncognito.com) | `string` | `""` | no |
| authentication\_oidc\_authorization\_endpoint | OIDC Authorization Endpoint | `string` | `""` | no |
| authentication\_oidc\_client\_id | OIDC Client ID | `string` | `""` | no |
| authentication\_oidc\_client\_secret | OIDC Client Secret | `string` | `""` | no |
| authentication\_oidc\_issuer | OIDC Issuer | `string` | `""` | no |
| authentication\_oidc\_scope | OIDC scope, which should be a space separated string of requested scopes (see https://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims, and https://developers.google.com/identity/protocols/oauth2/openid-connect#scope-param for an example set of scopes when using Google as the IdP) | `string` | `null` | no |
| authentication\_oidc\_token\_endpoint | OIDC Token Endpoint | `string` | `""` | no |
| authentication\_oidc\_user\_info\_endpoint | OIDC User Info Endpoint | `string` | `""` | no |
| authentication\_type | Authentication type. Supported values are `COGNITO` and `OIDC` | `string` | `""` | no |
| context | Single object for setting entire context at once.<br>See description of individual variables for details.<br>Leave string and numeric variables as `null` to use default value.<br>Individual variable settings (non-null) override settings in context object,<br>except for attributes, tags, and additional\_tag\_map, which are merged. | `any` | <pre>{<br>  "additional_tag_map": {},<br>  "attributes": [],<br>  "delimiter": null,<br>  "enabled": true,<br>  "environment": null,<br>  "id_length_limit": null,<br>  "label_key_case": null,<br>  "label_order": [],<br>  "label_value_case": null,<br>  "name": null,<br>  "namespace": null,<br>  "regex_replace_chars": null,<br>  "stage": null,<br>  "tags": {}<br>}</pre> | no |
| default\_target\_group\_enabled | Enable/disable creation of the default target group | `bool` | `true` | no |
| delimiter | Delimiter to be used between `namespace`, `environment`, `stage`, `name` and `attributes`.<br>Defaults to `-` (hyphen). Set to `""` to use no delimiter at all. | `string` | `null` | no |
| deregistration\_delay | The amount of time to wait in seconds while deregistering target | `number` | `15` | no |
| enabled | Set to false to prevent the module from creating any resources | `bool` | `null` | no |
| environment | Environment, e.g. 'uw2', 'us-west-2', OR 'prod', 'staging', 'dev', 'UAT' | `string` | `null` | no |
| health\_check\_enabled | Indicates whether health checks are enabled. Defaults to `true` | `bool` | `true` | no |
| health\_check\_healthy\_threshold | The number of consecutive health checks successes required before healthy | `number` | `2` | no |
| health\_check\_interval | The duration in seconds in between health checks | `number` | `15` | no |
| health\_check\_matcher | The HTTP response codes to indicate a healthy check | `string` | `"200-399"` | no |
| health\_check\_path | The destination for the health check request | `string` | `"/"` | no |
| health\_check\_port | The port to use to connect with the target. Valid values are either ports 1-65536, or `traffic-port`. Defaults to `traffic-port` | `string` | `"traffic-port"` | no |
| health\_check\_protocol | The protocol to use to connect with the target. Defaults to `HTTP`. Not applicable when `target_type` is `lambda` | `string` | `"HTTP"` | no |
| health\_check\_timeout | The amount of time to wait in seconds before failing a health check request | `number` | `10` | no |
| health\_check\_unhealthy\_threshold | The number of consecutive health check failures required before unhealthy | `number` | `2` | no |
| id\_length\_limit | Limit `id` to this many characters (minimum 6).<br>Set to `0` for unlimited length.<br>Set to `null` for default, which is `0`.<br>Does not affect `id_full`. | `number` | `null` | no |
| label\_key\_case | The letter case of label keys (`tag` names) (i.e. `name`, `namespace`, `environment`, `stage`, `attributes`) to use in `tags`.<br>Possible values: `lower`, `title`, `upper`.<br>Default value: `title`. | `string` | `null` | no |
| label\_order | The naming order of the id output and Name tag.<br>Defaults to ["namespace", "environment", "stage", "name", "attributes"].<br>You can omit any of the 5 elements, but at least one must be present. | `list(string)` | `null` | no |
| label\_value\_case | The letter case of output label values (also used in `tags` and `id`).<br>Possible values: `lower`, `title`, `upper` and `none` (no transformation).<br>Default value: `lower`. | `string` | `null` | no |
| listener\_http\_header\_conditions | A list of http header conditions to apply to the listener. | <pre>list(object({<br>    name  = string<br>    value = list(string)<br>  }))</pre> | `[]` | no |
| load\_balancing\_algorithm\_type | Determines how the load balancer selects targets when routing requests. Only applicable for Application Load Balancer Target Groups. The value is round\_robin or least\_outstanding\_requests. The default is round\_robin. | `string` | `"round_robin"` | no |
| name | Solution name, e.g. 'app' or 'jenkins' | `string` | `null` | no |
| namespace | Namespace, which could be your organization name or abbreviation, e.g. 'eg' or 'cp' | `string` | `null` | no |
| port | The port for the created ALB target group (if `target_group_arn` is not set) | `number` | `80` | no |
| protocol | The protocol for the created ALB target group (if `target_group_arn` is not set) | `string` | `"HTTP"` | no |
| regex\_replace\_chars | Regex to replace chars with empty string in `namespace`, `environment`, `stage` and `name`.<br>If not set, `"/[^a-zA-Z0-9-]/"` is used to remove all characters other than hyphens, letters and digits. | `string` | `null` | no |
| slow\_start | The amount of time for targets to warm up before the load balancer sends them a full share of requests. The range is 30-900 seconds or 0 to disable. The default value is `0` seconds | `number` | `0` | no |
| stage | Stage, e.g. 'prod', 'staging', 'dev', OR 'source', 'build', 'test', 'deploy', 'release' | `string` | `null` | no |
| stickiness\_cookie\_duration | The time period, in seconds, during which requests from a client should be routed to the same target. After this time period expires, the load balancer-generated cookie is considered stale. The range is 1 second to 1 week (604800 seconds). The default value is 1 day (86400 seconds) | `number` | `86400` | no |
| stickiness\_enabled | Boolean to enable / disable `stickiness`. Default is `true` | `bool` | `true` | no |
| stickiness\_type | The type of sticky sessions. The only current possible value is `lb_cookie` | `string` | `"lb_cookie"` | no |
| tags | Additional tags (e.g. `map('BusinessUnit','XYZ')` | `map(string)` | `{}` | no |
| target\_group\_arn | Existing ALB target group ARN. If provided, set `default_target_group_enabled` to `false` to disable creation of the default target group | `string` | `""` | no |
| target\_type | The type (`instance`, `ip` or `lambda`) of targets that can be registered with the target group | `string` | `"ip"` | no |
| unauthenticated\_hosts | Unauthenticated hosts to match in Hosts header | `list(string)` | `[]` | no |
| unauthenticated\_listener\_arns | A list of unauthenticated ALB listener ARNs to attach ALB listener rules to | `list(string)` | `[]` | no |
| unauthenticated\_paths | Unauthenticated path pattern to match (a maximum of 1 can be defined) | `list(string)` | `[]` | no |
| unauthenticated\_priority | The priority for the rules without authentication, between 1 and 50000 (1 being highest priority). Must be different from `authenticated_priority` since a listener can't have multiple rules with the same priority | `number` | `0` | no |
| vpc\_id | The VPC ID where generated ALB target group will be provisioned (if `target_group_arn` is not set) | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| target\_group\_arn | ALB Target Group ARN |
| target\_group\_arn\_suffix | ALB Target Group ARN suffix |
| target\_group\_name | ALB Target Group name |
<!-- markdownlint-restore -->



## Share the Love

Like this project? Please give it a ★ on [our GitHub](https://github.com/cloudposse/terraform-aws-alb-ingress)! (it helps us **a lot**)

Are you using this project or any of our other projects? Consider [leaving a testimonial][testimonial]. =)


## Related Projects

Check out these related projects.

- [terraform-aws-alb](https://github.com/cloudposse/terraform-aws-alb) - Terraform module to create an ALB, default ALB listener(s), and a default ALB target and related security groups.



## Help

**Got a question?** We got answers.

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-alb-ingress/issues), send us an [email][email] or join our [Slack Community][slack].

[![README Commercial Support][readme_commercial_support_img]][readme_commercial_support_link]

## DevOps Accelerator for Startups


We are a [**DevOps Accelerator**][commercial_support]. We'll help you build your cloud infrastructure from the ground up so you can own it. Then we'll show you how to operate it and stick around for as long as you need us.

[![Learn More](https://img.shields.io/badge/learn%20more-success.svg?style=for-the-badge)][commercial_support]

Work directly with our team of DevOps experts via email, slack, and video conferencing.

We deliver 10x the value for a fraction of the cost of a full-time engineer. Our track record is not even funny. If you want things done right and you need it done FAST, then we're your best bet.

- **Reference Architecture.** You'll get everything you need from the ground up built using 100% infrastructure as code.
- **Release Engineering.** You'll have end-to-end CI/CD with unlimited staging environments.
- **Site Reliability Engineering.** You'll have total visibility into your apps and microservices.
- **Security Baseline.** You'll have built-in governance with accountability and audit logs for all changes.
- **GitOps.** You'll be able to operate your infrastructure via Pull Requests.
- **Training.** You'll receive hands-on training so your team can operate what we build.
- **Questions.** You'll have a direct line of communication between our teams via a Shared Slack channel.
- **Troubleshooting.** You'll get help to triage when things aren't working.
- **Code Reviews.** You'll receive constructive feedback on Pull Requests.
- **Bug Fixes.** We'll rapidly work with you to fix any bugs in our projects.

## Slack Community

Join our [Open Source Community][slack] on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

## Discourse Forums

Participate in our [Discourse Forums][discourse]. Here you'll find answers to commonly asked questions. Most questions will be related to the enormous number of projects we support on our GitHub. Come here to collaborate on answers, find solutions, and get ideas about the products and services we value. It only takes a minute to get started! Just sign in with SSO using your GitHub account.

## Newsletter

Sign up for [our newsletter][newsletter] that covers everything on our technology radar.  Receive updates on what we're up to on GitHub as well as awesome new projects we discover.

## Office Hours

[Join us every Wednesday via Zoom][office_hours] for our weekly "Lunch & Learn" sessions. It's **FREE** for everyone!

[![zoom](https://img.cloudposse.com/fit-in/200x200/https://cloudposse.com/wp-content/uploads/2019/08/Powered-by-Zoom.png")][office_hours]

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-alb-ingress/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://cpco.io/help-out) with our other projects, we would love to hear from you! Shoot us an [email][email].

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


## Copyright

Copyright © 2017-2021 [Cloud Posse, LLC](https://cpco.io/copyright)



## License

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

See [LICENSE](LICENSE) for full details.

```text
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
```









## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know by [leaving a testimonial][testimonial]!

[![Cloud Posse][logo]][website]

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We ❤️  [Open Source Software][we_love_open_source].

We offer [paid support][commercial_support] on all of our projects.

Check out [our other projects][github], [follow us on twitter][twitter], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.



### Contributors

<!-- markdownlint-disable -->
|  [![Erik Osterman][osterman_avatar]][osterman_homepage]<br/>[Erik Osterman][osterman_homepage] | [![Igor Rodionov][goruha_avatar]][goruha_homepage]<br/>[Igor Rodionov][goruha_homepage] | [![Andriy Knysh][aknysh_avatar]][aknysh_homepage]<br/>[Andriy Knysh][aknysh_homepage] | [![Sarkis Varozian][sarkis_avatar]][sarkis_homepage]<br/>[Sarkis Varozian][sarkis_homepage] |
|---|---|---|---|
<!-- markdownlint-restore -->

  [osterman_homepage]: https://github.com/osterman
  [osterman_avatar]: https://img.cloudposse.com/150x150/https://github.com/osterman.png
  [goruha_homepage]: https://github.com/goruha
  [goruha_avatar]: https://img.cloudposse.com/150x150/https://github.com/goruha.png
  [aknysh_homepage]: https://github.com/aknysh
  [aknysh_avatar]: https://img.cloudposse.com/150x150/https://github.com/aknysh.png
  [sarkis_homepage]: https://github.com/sarkis
  [sarkis_avatar]: https://img.cloudposse.com/150x150/https://github.com/sarkis.png

[![README Footer][readme_footer_img]][readme_footer_link]
[![Beacon][beacon]][website]

  [logo]: https://cloudposse.com/logo-300x69.svg
  [docs]: https://cpco.io/docs?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=docs
  [website]: https://cpco.io/homepage?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=website
  [github]: https://cpco.io/github?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=github
  [jobs]: https://cpco.io/jobs?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=jobs
  [hire]: https://cpco.io/hire?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=hire
  [slack]: https://cpco.io/slack?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=slack
  [linkedin]: https://cpco.io/linkedin?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=linkedin
  [twitter]: https://cpco.io/twitter?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=twitter
  [testimonial]: https://cpco.io/leave-testimonial?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=testimonial
  [office_hours]: https://cloudposse.com/office-hours?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=office_hours
  [newsletter]: https://cpco.io/newsletter?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=newsletter
  [discourse]: https://ask.sweetops.com/?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=discourse
  [email]: https://cpco.io/email?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=email
  [commercial_support]: https://cpco.io/commercial-support?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=commercial_support
  [we_love_open_source]: https://cpco.io/we-love-open-source?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=we_love_open_source
  [terraform_modules]: https://cpco.io/terraform-modules?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=terraform_modules
  [readme_header_img]: https://cloudposse.com/readme/header/img
  [readme_header_link]: https://cloudposse.com/readme/header/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=readme_header_link
  [readme_footer_img]: https://cloudposse.com/readme/footer/img
  [readme_footer_link]: https://cloudposse.com/readme/footer/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=readme_footer_link
  [readme_commercial_support_img]: https://cloudposse.com/readme/commercial-support/img
  [readme_commercial_support_link]: https://cloudposse.com/readme/commercial-support/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-aws-alb-ingress&utm_content=readme_commercial_support_link
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-aws-alb-ingress&url=https://github.com/cloudposse/terraform-aws-alb-ingress
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-aws-alb-ingress&url=https://github.com/cloudposse/terraform-aws-alb-ingress
  [share_reddit]: https://reddit.com/submit/?url=https://github.com/cloudposse/terraform-aws-alb-ingress
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/cloudposse/terraform-aws-alb-ingress
  [share_googleplus]: https://plus.google.com/share?url=https://github.com/cloudposse/terraform-aws-alb-ingress
  [share_email]: mailto:?subject=terraform-aws-alb-ingress&body=https://github.com/cloudposse/terraform-aws-alb-ingress
  [beacon]: https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse/terraform-aws-alb-ingress?pixel&cs=github&cm=readme&an=terraform-aws-alb-ingress
