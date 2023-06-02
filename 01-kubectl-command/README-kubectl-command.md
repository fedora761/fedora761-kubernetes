kubectl --help
kubectl command --help

kubectl run <자원이름> <옵션>
- kubectl run webserver --image=nginx:1.14 --port 80
- kubectl run webserver --image=nginx:1.14 --port 80 --dry-run
- kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml
- kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml > webserpod.yml

kubectl create
- kubectl create deployment mainui --image=httpd --replicas=3
- kubectl create namespace product
- kubectl create -f webserpod.yml


kubectl apply -f obj.yaml
- kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

kubectl get <자원이름> <객체이름>
- kubectl get nodes
- kubectl get nodes -o wide
- kubectl get deployments
- kubectl get pods
- kubectl get pods -o wide
- kubectl get pods --all-namespaces

kubectl edit <자원이름> <객체이름>


kubectl describe <자원이름> <객체이름>
- - kubectl describe node kubernetes-master

kubectl delete pod main
- kubectl delete pods webserver
- kubectl delete pod --all

kubectl exec
- kubectl exec webserver -it --/bin/bash

kubectl logs
- kubectl logs webserver

kubectl api-resources
