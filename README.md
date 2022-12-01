# Installation steps

```bash
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=gitops-environment \
  --branch=main \
  --path=./clusters/my-cluster \
  --personal
```

```bash
flux create source git gitops-demo \
  --url=https://github.com/$GITHUB_USER/gitops-environment \
  --branch=main \
  --interval=30s \
  --export > ./clusters/my-cluster/gitops-demo.yaml
```

```bash
flux create kustomization gitops-demo \
  --target-namespace=default \
  --source=gitops-demo \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ./clusters/my-cluster/gitops-kustomization.yaml
```