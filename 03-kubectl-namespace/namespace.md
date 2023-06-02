
namespce 
- 클러스터 하나를 여러개의 논리적인 단위로 나눠서 사용
- 쿠버테니스 클러스터 하나를 여러 팀이나 사용자가 함께 공유
- 용도에 따라 실행해야하는 앱을 구분할때 사용

kubectl create deploy ui --image=nginx --namespace kakao
kubectl create deploy ui --image=nginx --namespace estsoft


namespce 생성
- #cli
- kubectl create namespace blue
- kubectl get namespaces

- #yaml
- kubectl create namespace gren --dry-run -o yaml > green-ns.yaml
- vim green-ns.yaml
- kubectl create -f green-ns.yaml

namespace 관리
- kubectl get namespace
- kubectl delete namespace


kubectl get pods -n kube-system
kubectl get pods --all-namespaces

kubectl get pods 
- #디폴드값에서 조회

다른 네임스페이스에 pod실행
- kubectl create -f nginx.yaml -n blue
- kubectl create -f nginx.yaml -n orange
-# -n: 네임스페이스에서 실행


다른 네임스페이스 조회
- kubectl get namespaces
- kubectl get pods -n blue


사용할 네임스페이스를 switch 하기
- 기본으로 사용하는 namespace를 default가 아닌 다른 이름의 namespace로 switch하기
1. namespace를 포함한 context등록
- kubectl config --help
- kubectl config set-context NAME --cluster=kubernetes....
- kubectl config view

- kubectl config set-context orange@kubernetes --cluster=kubernetes --user=kubernetes-admin --namespace=orange
- kubectl config set-context blue@kubernetes --cluster=kubernetes --user=kubernetes-admin --namespace=blue

- kubectl config view 


2. 등록된 namespace로 context 변경
- kubectl config use-context NAME 

- kubectl config use-context blue@kubernetes
- #네임스페이스 변경함
- kubectl config current-context
- kubectl get pods 
- #blue pods만 나옴
- kubectl get pods -n default


3. kubectl delete [오브젝트]
- kubectl delete pods mypod -n default
- kubectl delete pods nginx -n blue 

4. namespace 삭제하기
- pod 실행중에 namespace를 삭제하면 pod도 삭제됨
- kubectl delete namespace blue
