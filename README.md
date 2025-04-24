
# Set kubernetes cluster up
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server" sh -s - --disable=traefik --disable=servicelb --write-kubeconfig-mode=644
Mene kubernetes/bootstrap/argocd/
kubectl apply -k .

Apply cloudflare secret with kubectl 

## TODO
External secret manager