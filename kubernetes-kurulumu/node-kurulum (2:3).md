MASTER ICIN UYGULANACAKLAR LISTESI

#Pod network yaratmak icin calico yaml lari indirelim

wget https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/rbac-kdd.yaml

wget https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml

#Inen calico.yaml dosyasinin icini inceleyelim

vi calico.yaml

# Calico yaml file daki ip bilgisine uygun olarak, bir pod network range i belirleyerek Kubernetes cluster imizi olusturalim

sudo kubeadm init --pod-network-cidr=192.168.0.0/16

#API server a admin erisim yetkisine sahip bir hesap yaratalim 

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

#Pod network olusturmak icin gerekli yaml dosyalarini calistiralim

kubectl apply -f rbac-kdd.yaml
kubectl apply -f calico.yaml

# Sistem specific podlari ve calico podlarini inceleyelim  
# Not : DNS pod umuz network deploy olup calisir halene kadar aktif olmayacak.

kubectl get pods --all-namespaces

#--watch flag kullanabiliriz

kubectl get pods --all-namespaces --watch

#All system pods should be Running

kubectl get pods --all-namespaces

#Cluster da mevcut podlarin listesine bakalim - sadece master gorunecek

kubectl get nodes 

#kubelet static pod manifestleri calistiriyor yani bir anlamda core cluster podlari calisir hale geliyor 

sudo systemctl status kubelet.service 

#kubeconfig dosyasinin bulundugu directory i inceleyelim
ls /etc/kubernetes

#master daki manifestleri inceleyelim
ls /etc/kubernetes/manifests

#api-server ve etcd nin manifestlerini incelemek istersek..
sudo more /etc/kubernetes/manifests/etcd.yaml
sudo more /etc/kubernetes/manifests/kube-apiserver.yaml