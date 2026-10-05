# mistershell

```bash
kubectl create secret generic mistershell-secrets \
  --from-literal=db-encryption-key="$(openssl rand -hex 32)" \
  --dry-run=client \
  -o yaml > mistershell-secrets.yaml
```
