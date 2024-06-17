### Requirement
- Ubuntu 18.04+
- MySQL server
- MySQL database and user for K3S

### Install Kubernetes On First Master Node
````
curl -sfL https://get.k3s.io | sh -s - server --cluster-init --disable=traefik \
  --token=SECRET \
  --datastore-endpoint="mysql://$DATABASE-USERNAME:$DATABASE-PASSWORD@tcp($DATABASE-HOSTNAME:$DATABASE-PORT)/$DATABASE_NAME"
````

### Get Server Token on First Master Node
````
cat /var/lib/rancher/k3s/server/token
````

### Add Another Master Node
````
curl -sfL https://get.k3s.io | sh -s - server --cluster-init --disable=traefik \
  --token=$SERVER-TOKEn \
  --datastore-endpoint="mysql://$DATABASE-USERNAME:$DATABASE-PASSWORD@tcp($DATABASE-HOSTNAME:$DATABASE-PORT)/$DATABASE_NAME"
````

### Check Avaibility Node

Run this command at first master node and another master node
````
sudo k3s kubectl get nodes
````

or

````
sudo kubectl get nodes
````