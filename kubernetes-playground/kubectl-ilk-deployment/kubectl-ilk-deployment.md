**INFO**  
```kubectl version```  
```kubectl get cs```  

**DEMO-ROLLOUT**  
```kubectl run hello-k8s --image=gcr.io/google_containers/echoserver:1.4 --port=8080```  
```kubectl expose deployment hello-k8s --type=NodePort```  
```kubectl port-forward hello-k8s-555c87cddd-5wvxt 8080:8080```  
```kubectl scale deployment.v1.apps/hello-k8s  --replicas=2```  

**CONTEXT**  
```kubectl config get-contexts```  
```kubectl config use-context docker-for-desktop```  
