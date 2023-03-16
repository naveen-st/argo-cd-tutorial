### prerequisite :
- Docker
- Kubectl


Mac users : 
```
brew install minikube
```

Linux (Debian) : 
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```
or Visit for https://minikube.sigs.k8s.io/docs/start/ 


## Running 
Make sure docker is running before running following command.

For single node cluster :
```
minikube start 
```
For multinode node cluster :
```
minikube start --nodes 3 -p multinode-demo
```

Test if installation is working fine.
```
kubectl get po -A
```

It should return similar output.
```
NAMESPACE     NAME                               READY   STATUS    RESTARTS   AGE
kube-system   coredns-565d847f94-7kn57           1/1     Running   0          23s
kube-system   etcd-minikube                      1/1     Running   0          35s
kube-system   kube-apiserver-minikube            1/1     Running   0          37s
kube-system   kube-controller-manager-minikube   1/1     Running   0          35s
kube-system   kube-proxy-sl6t6                   1/1     Running   0          23s
kube-system   kube-scheduler-minikube            1/1     Running   0          37s
kube-system   storage-provisioner                1/1     Running   0          33s
```

### Troubleshoot

IF_VBOX_NOT_VISIBLE error

```
❌  Exiting due to IF_VBOX_NOT_VISIBLE: Failed to start host: driver start: Error setting up host only network on machine start: The host-only adapter we just created is not visible. This is a well known VirtualBox bug. You might want to uninstall it and reinstall at least version 5.0.12 that is is supposed to fix this issue
```

- Check if docker is up and running 
- Try recreating the minikube cluster :
```
minikube delete && minikube start
```