jaime@Jaimes-MBP sre-task-repo % minikube service upcommerce-service -n sre  

|-----------|--------------------|-------------|---------------------------|
| NAMESPACE |        NAME        | TARGET PORT |            URL            |
|-----------|--------------------|-------------|---------------------------|
| sre       | upcommerce-service |        5000 | http://192.168.49.2:31439 |
|-----------|--------------------|-------------|---------------------------|
🏃  Starting tunnel for service upcommerce-service.
|-----------|--------------------|-------------|------------------------|
| NAMESPACE |        NAME        | TARGET PORT |          URL           |
|-----------|--------------------|-------------|------------------------|
| sre       | upcommerce-service |             | http://127.0.0.1:65163 |
|-----------|--------------------|-------------|------------------------|
🎉  Opening service sre/upcommerce-service in default browser...
❗  Because you are using a Docker driver on darwin, the terminal needs to be open to run it.


Jaimes-MBP:sre-task-repo jaime$ kubectl --namespace sre port-forward $POD_NAME 9093

Forwarding from 127.0.0.1:9093 -> 9093
Forwarding from [::1]:9093 -> 9093

Jaimes-MBP:sre-task-repo jaime$ kubectl --namespace sre port-forward $POD_NAME 9090

Forwarding from 127.0.0.1:9090 -> 9090
Forwarding from [::1]:9090 -> 9090

Jaimes-MBP:sre-task-repo jaime$ kubectl port-forward service/upcommerce-service -n sre 30768:5000

Forwarding from 127.0.0.1:30768 -> 5000
Forwarding from [::1]:30768 -> 5000

Jaimes-MBP:sre-task-repo jaime$ docker ps

CONTAINER ID   IMAGE                                 COMMAND                  CREATED          STATUS          PORTS                                                                                                                                  NAMES

8670c015c69e   gcr.io/k8s-minikube/kicbase:v0.0.42   "/usr/local/bin/entr…"   24 minutes ago   Up 24 minutes   127.0.0.1:64869->22/tcp, 127.0.0.1:64870->2376/tcp, 127.0.0.1:64872->5000/tcp, 127.0.0.1:64873->8443/tcp, 127.0.0.1:64871->32443/tcp   minikube

Jaimes-MBP:sre-task-repo jaime$ kubectl get nodes

NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   24m   v1.28.3

Jaimes-MBP:sre-task-repo jaime$ kubectl get svc

NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   24m

Jaimes-MBP:sre-task-repo jaime$ kubectl get pods --all-namespaces

NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-5dd5756b68-fplpx           1/1     Running   0             24m
kube-system   etcd-minikube                      1/1     Running   0             24m
kube-system   kube-apiserver-minikube            1/1     Running   0             24m
kube-system   kube-controller-manager-minikube   1/1     Running   0             24m
kube-system   kube-proxy-65rzl                   1/1     Running   0             24m
kube-system   kube-scheduler-minikube            1/1     Running   0             24m
kube-system   storage-provisioner                1/1     Running   1 (23m ago)   24m
sre           upcommerce-app-584d94f948-rgm4g    1/1     Running   0             22m

Jaimes-MBP:sre-task-repo jaime$ kubectl get deployments -n sre

NAME             READY   UP-TO-DATE   AVAILABLE   AGE
upcommerce-app   1/1     1            1           23m

Jaimes-MBP:sre-task-repo jaime$ kubectl get deployments --all-namespaces

NAMESPACE     NAME             READY   UP-TO-DATE   AVAILABLE   AGE
kube-system   coredns          1/1     1            1           26m
sre           upcommerce-app   1/1     1            1           24m
Jaimes-MBP:sre-task-repo jaime$ 

jaime@Jaimes-MBP ~ % minikube status

minikube
type: Control Plane
host: Stopped
kubelet: Stopped
apiserver: Stopped
kubeconfig: Stopped

jaime@Jaimes-MBP ~ % 
