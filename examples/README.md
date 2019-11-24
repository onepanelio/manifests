## Running Workflow examples

### Argo

First, create the instance templates:
```bash
kubectl apply -f examples/instance-templates/instance-tmpl.yaml
```

To create an instance:
```bash
argo submit examples/instance-creator.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace>
```

To delete an instance:
```bash
argo submit examples/instance-deleter.yaml -p instance-name=<instance-name> -p instance-namespace=<namespace>
```