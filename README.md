# jenkins-k8s
Jenkins-K8s playground

## Steps

### Start Jenkins: https://www.jenkins.io/doc/book/installing/kubernetes/#setup-jenkins-on-kubernetes
* kubectl create namespace devops-tools
* kubectl apply -f serviceAccount.yml
* kubectl create -f volume.yaml
* kubectl apply -f deployment.yaml
* kubectl describe deployments --namespace=devops-tools
* kubectl apply -f service.yaml
* Jenkins will be up at http://<node-ip>:32000

### Configure k8s cloud
* kubectl cluster-info -> Capture k8s url
* kubectl get pods -n devops-tools | grep jenkins -> Capture pod name
* kubectl describe pod -n devops-tools jenkins-5fdbf5d7c5-dj2rq |grep -i ip -> Capture Jenkins IP Adress
* In UI while configuring k8s cloud, enter the values for k8s url and jenkins url
* Add pod template with container template having name as 'jnlp' and image as 'jenkins/inbound-agent'
* Save and create new job

