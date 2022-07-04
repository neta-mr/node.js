minikube image build -t node-app:1.0.0 -f dockerfile.prod .
minikube addons enable ingress

helm dependency build/update nodeapp
helm upgrade -i node-app-chart nodeapp/ --values nodeapp/values.yaml
helm uninstall node-app-chart 
