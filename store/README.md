
```docker build -t samba:4.10.0 .```

```helm install --name store --namespace store ./helm/samba```

Avahi has to be deployed with 'hostNetwork: true'. However, not in my case.
