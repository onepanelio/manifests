# Manifests


## Test using examples

Enable `istio` and give `default` service account correct roles in `default` namespace:
```bash
kubectl apply -f examples/namespace
```

Create example instance:
```bash
argo submit examples/<template-name>.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace> -p action=create
```

Change instance machine-type:
```bash
argo submit examples/<template-name>.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace> -p action=apply -p machine-type=cpu-1-4
```

Delete example instance:
```bash
argo submit examples/<template-name>.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace> -p action=delete
```

## Useful commands

Verifying that a `service` is pointed correctly:
```bash
kubectl run -i --tty --rm debug --image=busybox --restart=Never -- wget <service-name>
```