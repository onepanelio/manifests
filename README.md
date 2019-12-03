# Manifests

## Instance workflow parameters


`name` Name of the the instance.

`action` Action to perform on the instance, values are:
- `create` Create an instance
- `apply` Update an instance, combined with:
    - `machine-type` It will change the machine type for an instance.
    - `replicas` It will pause (set to `0`) and resume (set to `1`) an instance.
- `delete` Delete an instance.


## System-wide parameters

`host` The domain name of application. Example: cluster.onepanel.io

## Test using examples

Enable `istio` and give `default` service account correct roles in `default` namespace:
```bash
kubectl apply -f examples/namespace
```

**Note:** the following parameters need to be appeneded to all of the actions below:
```
-p host=test-cluster-6.onepanel.io
```

Create an instance:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p action=create -p machine-type=<machine-type>
```

Change instance machine type:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p action=apply -p machine-type=<new-machine-type>
```

Pause an instance:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p replicas=0 action=apply -p machine-type=cpu-1-4 -p machine-type=<existing-machine-type>
```

Resume an instance with existing machine type:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p replicas=1 action=apply -p machine-type=cpu-1-4 -p machine-type=<existing-machine-type>
```

Resume an instance with new machine-type:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p replicas=1 action=apply -p machine-type=cpu-1-4 -p machine-type=<new-machine-type>
```

Delete example instance:
```bash
argo submit examples/<template-name>.yaml -p name=<name> -p action=delete
```

## Useful commands

Verifying that a `service` is pointed correctly:
```bash
kubectl run -i --tty --rm debug --image=busybox --restart=Never -- wget <service-name>
```