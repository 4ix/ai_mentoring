# 멘토링
## 2023-03-11(토)
- 쿠버네티스
1. 하이퍼바이저 플랫폼: 가상화를 지원하려면 필요함
2. 클라우드 네이티브: 컨테이너 기반에서 개발, 운영, 배포를 한다. (클라우드 와의 차이점 알아두면 좋음)
3. IAAS 
4. 컨테이너 기반에서 개발을 해 봤습니다. 써보면 좋음.
5. kublet: c advisor monitoring이 있음.

```bash
kubectl config use-context k8s
kubectl get nodes
kubectl get nodes -o wide
kubectl describe nodes k8s-worker1
kubectl get pod --all-namespaces

watch kubectl get pods -o wide
kubectl describe pods web
kubectl run web2 --image=nginx:1.14
kubectl run web3 --image=nginx:1.15 --dry-run=client -o yaml > webserver3.yaml
kubectl run web3 --image=nginx:1.15 --dry-run=client -o json

# yaml 파일 수정해서 컨테이너를 생성하고 삭제를 한다.
kubectl apply -f webserver3.yaml
kubectl delete -f webserver3.yaml

```


## 2023-03-04(토)
- 쿠버네티스
1. 도커 컨테이너 배포를 자동화시킬 수 있음.
2. 퍼블릭 클라우드에 적용 되어있으므로 배워야 함. 시대가 원함.
3. 효율적인 자원 활용 및 비용 절감 가능.

- Xshell 7
1. console: 10.0.2.5
2. k8s-master: 10.0.2.10
3. k8s-worker1: 10.0.2.11
4. k8s-worker2: 10.0.2.12
5. account / password : ubuntu, ubuntu

- Docker 명령어
```bash
docker search nginx
docker pull nginx:latest
docker run -d --name web -p 80:80 nginx # create + start

docker ps
docker ps -a -q # image id 반환
docker top webserver
docker logs webserver (logs -f webserver)
docker exec -it webserver /bin/bash # webserver로 직접 들어갈 때
docker stop webserver
docker rm webserver

# 일괄 진행
docker rm $(docker ps -a -q)
docker stop $(docker ps -a -q) 
docker rmi $(docker ps -a -q)
docker histroy nginx:1.14
docker inspect nginx:1.14
docker images --no-trunc
```

- Kubectl 명령어
```bash
kubectl create namespace green
kubectl get namespaces
kubectl run webserver3 --image=nginx -n green
kubectl get pods
kubectl get pods -n green # 특정한 namespace에서 정보를 볼 때
kubectl get pods -n gree -o wide # 자세히 볼 때
kubectl describe po -n green

kubectl get pods -o yaml > webserver3.yaml

```
