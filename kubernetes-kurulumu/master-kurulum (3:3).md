**NODE ICIN YAPILACAKLAR LISTESI**  

**kubelet ve container runtime service lerini kontrol ederim**  
```sudo systemctl status kubelet.service```  
```sudo systemctl status docker.service  ```

**Sistem basladigi zaman baslayacak sekilde set edelim**  
```sudo systemctl enable kubelet.service  ```
```sudo systemctl enable docker.service```

**Master'da token bilgisi verilmisti eger not almadiysak su sekilde listeleyebiliriz**  
```kubeadm token list```

**Yeniden bir token generate etmek istiyorsak**   
```kubeadm token create```

**Master ¸zerinde ca cert hash bulunmakta**  
```openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | openssl rsa -pubin -outform der 2>/dev/null | openssl dgst -sha256 -hex | sed 's/^.* //'```

**Api Server in IP adresi ya da adi, token imiz ve cert ile Node'umuzu cluster a dahil edelim**  
```sudo kubeadm join <ip>:6443 --token<token> --discovery-token-ca-cert-hash <ca_cert_hash>```

**Master a donecek olursak networking pod u yaratilana kadar NotReady state de gorulecektir**  
Pod un schedule edilip container inin indirilmesini bekliyor  
```kubectl get nodes ```

**Master'da calico pod ve kube-proxy nin yeni eklenen node larda calisir hale gelmesini gozlemleyelim**  
```kubectl get pods --all-namespaces --watch```

**Master da eklenen node umuz status unun Ready e donmesini gozlemleriz**  
```kubectl get nodes```