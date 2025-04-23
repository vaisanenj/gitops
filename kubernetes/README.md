# Set kubernetes cluster up
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server" sh -s - --disable=traefik --disable=servicelb --write-kubeconfig-mode=644
git clone <repo>
Mene kubernetes/bootstrap/argocd/
kubectl kustomize --enable-helm . | kubectl apply -f -


sudo kubectl create namespace argocd
--> Asennus toista kautta?
# sudo kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

2. Apply applicationsets
sudo kubectl apply -f kubernetes/argocd/


Apps
Argocd
    - Ingress
    - Admin password
    - High availablity
longhorn-system - OK
traefik
    - Kopio k3s nykyisestä?
cert-manager
    - clusterIssuer puuttuu

TODO:
Argocd --> Helm + Kustomization?
    --> https://github.com/argoproj/argocd-example-apps/tree/master/plugins/kustomized-helm apua?
cert-manager --> ClusterIssuer
traefik --> Koko paska puuttuu
longhorn-system  --> Asennus on
    --> longhorn engine v2 voisi konfata
    --> Pyörimään tiettyillä nodeilla (Mikä kombo?)
    --> Ingress asettaminen myös (gateway?)

node-role.kubernetes.io/control-plane=true,
node-role.kubernetes.io/master=true

gitea                               Active   483d

openldap
    nextcloud
    jellyfin

kube-prometheus-stack               Active   33d
arr-stack                           Active   518d
automation                          Active   457d
argocd                              Active   56d
cert-manager                        Active   530d
databases                           Active   524d
download                            Active   517d
lyrion-media-server                 Active   66d
wireguard                           Active   451d
gameserver-enshrouded               Active   435d
gameserver-enshrouded-default       Active   2d2h
gameserver-enshrouded-kids          Active   2d2h
gameserver-enshrouded-kids-server   Active   2d2h
gameserver-satisfactory             Active   386d
gameserver-valheim                  Active   435d


Argocd sync phases
    - Voi antaa negatiivisia ja posiitivia lukuja
    - Seuraava vaihe aloitetaan kun edellisen vaiheen kaikki ovat helthy
    - Kaikilla on oletuksena 0
    - Voidaan asettaa käyttämällä argocd.argoproj.io/sync-wave annotationia
    - Oletus viive vaiheilla on 2 sekuntia
    - 