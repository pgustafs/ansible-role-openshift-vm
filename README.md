openshift_vm
===========

Ansible Role to automate common kubevirt tasks

Requirements
------------

Ansible 2.9 or higher

Red Hat OpenShift Container Platform or equivalent

Collections:
- kubernetes.core
- redhat.openshift
- community.general


Variables
--------------

Currently the following variables are supported:

### openshift_vm_action

What action to perform, currently the following actions are supported:

`create` Create a virtual machine.

`delete` Delete a virtual machine.

`start` Start a virtual machine.

`stop` Stop a virtual machine.

`start_all` Starts all virtual machines in the cluster, can be used together with `openshift_vm_namespace` to only start all virtual machines in a namespace.

`stop_all` Stops all virtual machines in the cluster, can be used together with `openshift_vm_namespace` to only stop all virtual machines in a namespace.

```
openshift_vm_action: create
```

### openshift_vm_name

Name of the virtual machine that should be created/deleted/modified.

```
openshift_vm_name: 'test-vm'
```

### openshift_vm_namespace

Name of the namespace/project that we should operate in.

```
openshift_vm_namespace: 'test-project'
```

Dependencies
------------

None

Example Playbooks
----------------

## Start action examples

Start a virtual machine:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: start
    openshift_vm_name: <vm_name>
    openshift_vm_namespace: <project_name>
```

Start all virtual machines in a namespace:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: start_all
    openshift_vm_namespace: <project_name>
```

Start all virtual machines in the cluster:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: start_all
```

## Stop action examples

Stop a virtual machine:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: stop
    openshift_vm_name: <vm_name>
    openshift_vm_namespace: <project_name>
```

Stop all virtual machines in a namespace:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: stop_all
    openshift_vm_namespace: <project_name>
```

Stop all virtual machines in the cluster:
```yaml
- name: "Include role openshift_vm"
  include_role:
    name: openshift_vm
  vars:
    openshift_vm_action: stop_all
```

License
-------

GPLv2+

Author Information
------------------

Peter Gustafsson <pgustafs@redhat.com>
