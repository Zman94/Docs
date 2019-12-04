# Terraform docs

Terraform is an open-source infrastructure as code software tool created by HashiCorp. It enables users to define and provision a datacenter infrastructure using a high-level configuration language known as Hashicorp Configuration Language, or optionally JSON.

## Initializing
```
vim main.tf
> Add terraform docs
$ terraform init
$ terraform plan
$ terraform apply
$ terraform destroy
```

## tf files

To use terraform, you will most likely be using `output.tf`, `variables.tf`, and `main.tf`. `main.tf` will hold your resource declarations (systems you're deploying). When using resources, most of the configuration help will be found in that resources docs. `variables.tf` is used to set variables to be used by resources. Most common data structures are supported including maps for templatized deployments. Example can be seen below. `output.tf` is used to print variables after deployment.

## tf input

There are a couple ways developers can ask users for input (like cluster names). Users can override variables with environment variables `TF_VAR_<var>` or command line input with terraform commands. Additionally, developers can require input with an `input.tf` file that works similar to `variables.tf` but without values.

## modules

Modules work the same as functions in a standard programming language and are useful for templatizing common systems.

## Notes

Terraform files are idempotent.

## Debugging

To print statements for debugging during execution, store the value to a register and print during a debug task:
```
- name: find docker binary
  raw: "pwd; ls"
  register: debug_msg2

- debug:
    msg: "{{ debug_msg2 }}"
```

To further debug terraform issues, you can follow the instructions [here](https://www.terraform.io/docs/internals/debugging.html).

There are 5 levels of debugging that can be accessed by setting the `TF_LOG` environment variable. Those levels are `TRACE`, `DEBUG`, `INFO`, `WARN` or `ERROR` where `TRACE` is the most verbose.

## Terraform Functions

Within terraform, there are several functions that can be used to access the local file system or execute some commands. Two that I frequently run into for copying ssh keys are `pathexpand` and `file`. `pathexpand` will expand the `~` in commands and `file` outputs the contents of the input file.

## Example

Example of templatized variables:
`variables.tf`
```
variable "master_count" {
    description = "Int: Number of master"
    type        = "map"

    default = {
        test  = 1
        perf  = 3
        dev   = 1
    }
}
```

`input.tf`
```
variable "deployment_type" {
  description = "What type of deployment is this?\n Options: test perf dev"
}
```
