# Vagrant docs

DescriptionVagrant is an open-source software product for building and maintaining portable virtual software development environments.

Vagrant uses boxes similar to the way docker uses containers.

## Initializing

Create your directory and cd into it.
```
$ mkdir vagrant_test
$ cd vagrant_test
$ vagrant init
```

This will create a `Vagrantfile` where the configuration for your box will be held.
To work in the box,

```
$ vagrant up
$ vagrant ssh
```

To close any open virtual boxes, run:
```
$ vagrant destroy
```

This will not completely remove the box, that can be done with
```
vagrant box remove
```

## Shared Directory

The directory with `Vagrantfile` is shared in the virtual machine in directory `/vagrant/`.
This can be used to copy software from the host to the guest machine.

## Debugging

## Example

