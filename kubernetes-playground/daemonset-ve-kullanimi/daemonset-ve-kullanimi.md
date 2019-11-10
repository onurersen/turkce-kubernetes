# check cluster  
```kubectl get nodes```  
```kubectl describe node docker-desktop```  

# create daemonset  
```kubectl create -f fluentd-ds.yaml```  

# attach label  
```kubectl describe node docker-desktop```  
```kubectl label node docker-desktop app=collector-node```  
```kubectl label node docker-desktop --overwrite app=collector-node```  

# check  
```kubectl get ds```  
```kubectl get pods```  
```kubectl describe node docker-desktop```  

# clear  
```kubectl delete ds collector-node```  
```kubectl label node docker-desktop --overwrite app=nothing```  