# Installation steps

```bash
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=gitops-environment \
  --branch=main \
  --path=./clusters/my-cluster \
  --personal
```