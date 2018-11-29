# YAML docs

YAML is a human-readable data serialization language. It is commonly used for configuration files, but could be used in many applications where data is being stored or transmitted.

## Initializing

## Example

```YAML
---
# Starts with '---'
- list entry 0 that's a dict: dict value
  another key: another value

- list entry 1: value
  key: value
  lint correct boolean: false
  another correct boolean: true
  another key:
    - list value: more values
      yaml continues:
        using indents for level: it's similar to json

# ends with '...'
...
```
