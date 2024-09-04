# Install k3s in MacOS M3 chip
Install homebrew first from https://brew.sh/
Then Install Docker Desktop from https://docs.docker.com/desktop/install/mac-install/
Then install k3d with homebrew. k3d is a wrapper for rancher k3s for MacOS
```
brew install k3d
```
if this doesn't work, try,
```
/opt/homebrew/bin/brew install k3d
```
# Install a new cluster with 3 servers and 3 agents,
```
/opt/homebrew/bin/k3d cluster create mac-local --servers 3 --agents 3
```
Verify my typing either,
```
kubectl cluster-info
```
or,
```
kubectl get nodes
```
# Install Heml on Macos
```
/opt/homebrew/bin/brew install helm
```
# Install cert-manager on your k3d cluster,
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.2/cert-manager.crds.yaml
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager \
--namespace cert-manager \
--create-namespace \
--version v1.13.2
kubectl get pods --namespace cert-manager
```