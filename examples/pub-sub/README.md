<!-- BEGIN_TF_DOCS -->
# Publisher/subscriber (pub/sub) example

If deployed with the default values, this example will create two [content libraries](https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-vm-administration/GUID-254B2CE8-20A8-43F0-90E8-3F6776C2C896.html) named: 1/&nbsp;`example-pub` and 2/&nbsp;`example-sub` in your [VMware Cloud on AWS](https://aws.amazon.com/vmware/) or [VMware vSphere](https://docs.vmware.com/en/VMware-vSphere/index.html) on&#8209;premises environment.

## Usage

### Configure the provider

One way to configure the VMware vSphere provider is with [environment variables](https://registry.terraform.io/providers/hashicorp/vsphere/latest/docs#argument-reference), for example:

* Required
  * `VSPHERE_USER`: Username for vSphere API operations.
  * `VSPHERE_PASSWORD`: Password for vSphere API operations.
  * `VSPHERE_SERVER`: vCenter Server fully qualified domain name (FQDN) or IP address for vSphere API operations.
* Optional
  * `VSPHERE_ALLOW_UNVERIFIED_SSL`: Boolean that can be set to `true` to disable TLS certificate verification.
    This should be used with care as it could allow an attacker to intercept your auth token.
    If omitted, the default value is `false`.

### Configure the input variables

All of the variables in this example have default values, but if you would like to override any of these, one way to do so is to create a [`terraform.tfvars` variable definition file](https://www.terraform.io/language/values/variables#variable-definitions-tfvars-files) in this directory.

#### Example `terraform.tfvars`

```hcl
content_library_name = "Content library"
```

### Deploy

  To deploy this example, execute the following: 1/&nbsp;[`terraform init`](https://www.terraform.io/cli/commands/init), 2/&nbsp;[`terraform plan`](https://www.terraform.io/cli/commands/plan), and 3/&nbsp;[`terraform apply`](https://www.terraform.io/cli/commands/apply).

### Clean-up

When you want to remove the resources, execute the following: [`terraform destroy`](https://www.terraform.io/cli/commands/destroy).

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.1.0 |
| <a name="requirement_vsphere"></a> [vsphere](#requirement\_vsphere) | >= 2.1.0 |

## Providers

No providers.

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_publisher"></a> [publisher](#module\_publisher) | aws-ia/content-library/vsphere | >= 0.0.1 |
| <a name="module_subscriber"></a> [subscriber](#module\_subscriber) | aws-ia/content-library/vsphere | >= 0.0.1 |

## Resources

No resources.

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_password"></a> [password](#input\_password) | Password if creating a publication/subscription relationship between content libraries with authentication. | `string` | n/a | yes |
| <a name="input_datacenter_name"></a> [datacenter\_name](#input\_datacenter\_name) | The name of the vSphere datacenter object where the content library will be created (https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-vcenter-esxi-management/GUID-7FDFBDBE-F8AC-4D00-AE5E-3F14D7472FAF.html). | `string` | `"SDDC-Datacenter"` | no |
| <a name="input_datastore_name"></a> [datastore\_name](#input\_datastore\_name) | The name of the vSphere datastore object where the content library items will be stored (https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-storage/GUID-7BED10DD-3EF2-4670-BA7F-0EEB4EC6EB85.html). | `string` | `"WorkloadDatastore"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_publisher"></a> [publisher](#output\_publisher) | The publisher vSphere content library. |
| <a name="output_subscriber"></a> [subscriber](#output\_subscriber) | The subscriber vSphere content library. |
<!-- END_TF_DOCS -->
