code source from:Docker

minikube ssh

curl -L http:/nodeipaddress:8000/demo



nodeport:

we can do inside the cluster: 

minikube ssh
curl http://ipaddress:80/demo -L

outside the clsuter

>>>minikube ip

curl -L http://minikuneipaddress:30007/demo




