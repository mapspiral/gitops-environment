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