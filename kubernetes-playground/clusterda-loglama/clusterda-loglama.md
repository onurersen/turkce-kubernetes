```kubectl create ns logging-ns```  

```kubectl create -f logger.yaml```  
//pod name: logger-pod  
//container name: logger-container  

```kubectl get pods```  
```kubectl get pods --namespace=logging-ns```  
```kubectl describe pod logger-pod```  
```kubectl logs -n logging-ns --tail=5 logger-pod -c logger-container```  
```kubectl logs -f -n logging-ns --since=10s logger-pod -c logger-container```  

```kubectl apply -f one-time.yaml```  
//pod name: one-time-pod  
//container name: one-time-container  

```kubectl get pods --namespace=logging-ns```  
```kubectl describe pod one-time-pod -n logging-ns```  
```kubectl logs  -n logging-ns --tail=5 one-time-pod -c one-time-container```  
```kubectl logs -f -n logging-ns --since=10s one-time-pod -c one-time-container```  

//Check events  
```kubectl get events --namespace=logging-ns```  