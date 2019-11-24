# Manifests


## Test using examples

Enable `istio` and give `default` service account correct roles in `default` namespace:
```bash
kubectl apply -f examples/namespace
```

Create example instance templates:
```bash
kubectl apply -f examples/instance-templates/instance-tmpl.yaml
```

Create example instance:
```bash
argo submit examples/instance-creator.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace>
```

To delete example instance:
```bash
argo submit examples/instance-deleter.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace>
```