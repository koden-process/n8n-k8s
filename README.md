# n8n-k8s

echo -n 'mon-password' | base64 

```
kubectl apply -f namespace.yaml
kubectl apply -f secret.yaml
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
```


J'ai eu un problème de permissions sur le dossier /home/node/.n8n

pour le résoudre, j'ai lancé un pod pour le fixer
```sh
kubectl apply -f fix-permissions.yaml
```

puis j'ai ouvert un shell
```sh
kubectl exec -it fix-permissions -n n8n -- sh
```

pour exécuter les commandes suivantes
```sh
chown -R 1000:1000 /home/node/.n8n
chmod -R 755 /home/node/.n8n
```