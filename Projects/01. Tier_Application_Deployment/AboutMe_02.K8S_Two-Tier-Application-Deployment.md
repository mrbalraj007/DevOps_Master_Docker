# [Kubeadm Installation Guide for 2 tier application](https://github.com/LondheShubham153/kubestarter/blob/main/kubeadm_installation.md)

Execute on Both "Master" & "Worker Node"

```bash
sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install docker.io -y

sudo systemctl enable --now docker # enable and start in single command

# Adding GPG Keys
sudo curl -fsSL https://pkgs.k8s.io/addons:/cri-o:/prerelease:/main/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/cri-o-apt-keyring.gpg

# Add the repository to the sourselist
echo "deb [signed-by=/etc/apt/keyrings/cri-o-apt-keyring.gpg] https://pkgs.k8s.io/addons:/cri-o:/prerelease:/main/deb/ /" | sudo tee /etc/apt/sources.list.d/cri-o.list

sudo apt-get update -y
sudo apt-get install -y kubelet="1.29.0-*" kubectl="1.29.0-*" kubeadm="1.29.0-*"
sudo systemctl enable --now kubelet
sudo systemctl start kubelet
```


- Master node:
```bash
kubeadm token create --print-join-command
```

- Client node:

```bash
$ sudo kubeadm join 172.31.49.46:6443 --token gxd09z.wg682jdial5h57lr --discovery-token-ca-cert-hash sha256:a831854669c32ec8cdd4d4146a8922c602bb2753f52acd3072a453def1f081c2 --v=5
```

On- master:
```bash
kubectl get nodes
```



https://github.com/LondheShubham153/two-tier-flask-app/tree/master/k8s

clone this repo: https://github.com/LondheShubham153/two-tier-flask-app.git

