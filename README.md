# mistershell

Reset the admin user to log in for the first time (login is admin@mistershell.local). I didn't run it because it prints a password:
```bash
kubectl -n mistershell exec -it deploy/mistershell -- msh -y reset admin-user
```

Back up the encryption key. You need the same key to restore any database backup:
```bash
kubectl -n mistershell get secret mistershell-secrets -o jsonpath='{.data.db-encryption-key}' | base64 -d
```

---

```bash
kubectl create secret generic mistershell-secrets \
  --from-literal=db-encryption-key="$(openssl rand -hex 32)" \
  --dry-run=client \
  -o yaml > mistershell-secrets.yaml
```
