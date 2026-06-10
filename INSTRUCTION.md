Clone repository
git clone repository
go to folder repositiry
create namespace
kubectl apply -f namespace.yml
check namespases
kubectl get ns
create deploymenr
kubectl apply -f deployment.yml
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
check replica
kubectl get pods -n mateapp -o wide
min replica 2 and max replica 5,  for rolling update and 70% resources for stabylity work
0.25 CPU and 64MB RAM full for our app
