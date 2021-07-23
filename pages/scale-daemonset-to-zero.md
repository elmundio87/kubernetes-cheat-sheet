[Home](../index.md)

# Scale a daemonset up/down

Scale daemonset down
```
kubectl -n <namespace> patch daemonset <name-of-daemon-set> -p '{"spec": {"template": {"spec": {"nodeSelector": {"non-existing": "true"}}}}}'
```

Bring the daemonset back up
```
kubectl -n <namespace> psatch daemonset <name-of-daemon-set> --type json -p='[{"op": "remove", "path": "/spec/template/spec/nodeSelector/non-existing"}]'
```

Source: [https://stackoverflow.com/a/57533340](https://stackoverflow.com/a/57533340)
