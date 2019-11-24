# Manifests


## Test using examples

Enable `istio` and give `default` service account correct roles in `default` namespace:
```bash
kubectl apply -f examples/namespace
```

Create example instance:
```bash
argo submit examples/instance-tmpl.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace> -p action=create
```

To delete example instance:
```bash
argo submit examples/instance-tmpl.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace> -p action=delete
```

## Useful commands

Verifying that a `service` is pointed correctly:
```bash
kubectl run -i --tty --rm debug --image=busybox --restart=Never -- wget <service-name>
```