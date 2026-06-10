Clone repository
git clone repository
go to folder repository
create namespace
kubectl apply -f namespace.yml
check namespaces
kubectl get ns
create deployment
kubectl apply -f deployment.yml
check replica
kubectl get pods -n mateapp -o wide
create horisontal autoscal
kubectl apply -f hpa.yml
check replica
kubectl get pods -n mateapp -o wide
create busybox
kubectl apply -f busybox.yml
create service clusterip
kubectl apply -f clusterIp.yml
create node port
kubectl apply -f nodeport.yml


test clusterip
kubectl port-forward service/todoapp-service 8080:80 -n mateapp
go to page http://localhost:8080
or use busybox app
kubectl -n mateapp exec -it busybox -- sh
curl http://todoapp-service.todoapp.mateapp.svc.cluster.local
test nodeport
go to page http://localhost:30080



min replica 2 need for stability work and max replica 5 for managing resources with stress activity,  
maxUnavailable: 1, maxSurge: 1 for rolling update with zero downtime
and 70% resources for efectiv scale 
0.25 CPU and 64MB RAM full for our app
