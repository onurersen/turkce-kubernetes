#Swap disable et
swapoff -a

#Google apt repository key ekle
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

#Kubernetes apt repository i ekle
sudo bash -c 'cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF'

#Package listemizi g¸ncelleyelim  
sudo apt-get update

#Repository deki versiyonlari daha sonra incelemek icin apt-cache ile cachleyelim
apt-cache policy kubelet | head -n 20 
apt-cache policy docker.io | head -n 20 

#Gerekli paketleri repository den makinelerimize Áekelim
sudo apt-get install -y docker.io kubelet kubeadm kubectl

#Kubelet, container runtime'imiz olan docker status lerini kontrol edelim 
sudo systemctl status kubelet.service 
sudo systemctl status docker.service 

#Sistem ayaga kalktigi zaman calisacak sekilde ayarlayalim
sudo systemctl enable kubelet.service
sudo systemctl enable docker.service