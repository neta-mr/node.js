# Table of Contents

[Step-3](#Step-3)  
[Step-2](#Step-2)  
[Bonus](#Bonus)

## Step-3

In this step I used Ansible in order to

1. Package the application as a docker image.  
2. Run the app unit-tests.  
3. Run the container and check that http://local:8081 returns HTTP STATUS CODE 200.  
4. Send the docker image to DockerHub and tag it as latest.  

run `ansible-playbook ansible-node.yaml`

## Step-2

In this step I created new helm chart for deploying the app.\
I tested the deployment over minikube.

For minikube setup run:\
`minikube start`\
`minikube tunnel -c`

For app deployment using helm run:\
`helm dependency update nodeapp`\
`helm upgrade -i node-app-chart nodeapp/ --values nodeapp/values.yaml`

For testing the app:\
Modify `/etc/hosts` (add `<ip> node-app.local`)\
for the right ip you can run `kubectl get ingress --watch`\
run `curl http://node-app.local`

Uninstall the app by runnig:\
`helm uninstall node-app-chart`

## Bonus

I used ELK as centralized log system.\
Filebeat -> logstash -> elasticsearch -> kibana.
