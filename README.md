## Comandos para ejecutar
1. Verifica que Ansible funciona contra tus hosts:
```bash
ansible -i inventory.ini all -m ping
```

2. Ejecuta el bootstrap (instalación + init + join):
```bash
ansible-playbook -i inventory.ini bootstrap-cluster.yml
```
> Si algo falla revisa logs con ansible-playbook -i inventory.ini bootstrap-cluster.yml -vvv

3. Despliega la app en k8s:
```bash
ansible-playbook -i inventory.ini deploy-k8s.yml
```

4. Prueba la app en el navegador:
```bash
http://<WORKER_PUBLIC_IP>:30007
```

## Verificaciones y comandos útiles (debug / sanity checks)

1. Ver nodos (desde master):
```bash
KUBECONFIG=/etc/kubernetes/admin.conf kubectl get nodes -o wide
```

2. Ver pods en todos los namespaces:
```bash
KUBECONFIG=/etc/kubernetes/admin.conf kubectl get pods --all-namespaces
```

3. Ver pods/servicios del namespace default:
```bash
KUBECONFIG=/etc/kubernetes/admin.conf kubectl get all -n default
```

4. Si no ves los workers Ready, revisa kubelet en el worker:
```bash
sudo systemctl status kubelet
sudo journalctl -u kubelet -f
```

Logs del pod:
```bash
KUBECONFIG=/etc/kubernetes/admin.conf kubectl logs <pod-name>
```