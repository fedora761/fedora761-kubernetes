kubectl run webserver -image=nginx:1.14 --port 80

kubectl create deployment mainui --image=httpd:latest --replicas=3
#create deployment = 여러개의 pod를 생성할때 사용 / replicas = 3  총 3개 만들기
curl localhost 

kubectl get pod webserver -o yaml 
#yaml 형식으로 출력
kubectl get pod webserver -o json
#json 형식으로 출력 

실행한 pod 로 접속해서 내용 바꾸기 
1. kubectl run webserver -image=nginx --port 80
2. kubectl exec webserver -it --bahs
3. cd /usr/share/nginx/html
4. echo "fedora761 web" > index.html
5. exit
6. curl localhost

kubectl logs webserver

kubectl port-forward webserver 8080:80
curl localhost:8080


kubectl create deployment mainui --image=httpd:latest --replicas=3
kubectl get deployments.apps
kubectl edit deployments.apps mainui
#실행중인 pods 설정 바꿀때 사용
#spec의 replicas 갯수 조정3 -> 2
kubectl get pods

kubectl run webserver --image=nginx:1.14 --port 80 --dry-run
#실행 체크만 확인 

kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml
#yaml 포멧으로 출력 

kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml > webserver.yaml 
#yaml 포멧으로 저장

kubectl delete pod webserver

kubectl create -f webserver.yaml

