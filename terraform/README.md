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

## modules

Modules work the same as functions in a standard programming language

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

## Example

