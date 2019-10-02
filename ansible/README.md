# Ansible docs

Ansible is open source software that automates software provisioning, configuration management, and application deployment.

## Initializing

## YAML

## Jinja2

Jinja 2 is a templating engine used to generate python-like expressions. For a tutorial on Jinja 2, see [this](../jinja2/README.md) tutorial.

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

