#minikube node express webb app

eval $(minikube docker-env)

docker build -t node-web-app:0.1 .

kubectl run node-web-app --image=node-web-app:0.1 --image-pull-policy=Never

kubectl expose deployment node-web-app --type=LoadBalancer --port=3000

kubectl scale --replicas=3 deployment/node-web-app


kubectl expose deployment node-web-app --type=LoadBalancer --port=3000

kubectl set image deployment/node-web-app node-web-app=node-web-app:0.1

minikube service node-web-app


