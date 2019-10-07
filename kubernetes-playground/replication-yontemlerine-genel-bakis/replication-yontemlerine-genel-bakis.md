**Kullanilan yaml dosyalarini replication klasoru altinda bulabilirsiniz**  

**REPLICATION CONTROLLER**  
```kubectl apply -f rc.yaml```  
```kubectl get rc```  
```kubectl get pods```  
```kubectl delete rc hello-rc```  

**REPLICASET**  
```kubectl apply -f rs.yaml```  
```kubectl get rs```  
```kubectl get pods```  
```kubectl delete rs hello-rs```  

**DEPLOYMENT**  
```kubectl apply -f deploment.yaml```  
```kubectl get deployments```  
```kubectl get pods```  
```kubectl delete deployment hello-dep```  
