<!-- minikube image build -t node-app:1.0.0 -f dockerfile.prod .\ -->
minikube tunnel -c\

helm dependency build/update nodeapp\
helm upgrade -i node-app-chart nodeapp/ --values nodeapp/values.yaml\
helm test node-app-chart\
helm uninstall node-app-chart\

modify /etc/hosts
