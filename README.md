# Ansible AWX

## Clone git Repo
- git clone git@gitlab.uoldiveo.intranet:automation-aiops/kubernetes-applications/ansible-awx.git

## Add helm repo
- helm repo add awx-operator https://ansible.github.io/awx-operator/

## Update helm repo
- helm repo update

## Install awx-operator
- helm install -n ansible-awx --create-namespace awx-operator awx-operator/awx-operator

### Wait awx-task and awx-web 
- kubectl get pods -l "app.kubernetes.io/managed-by=awx-operator" -w -n ansible-awx

## Install pvc
- kubectl apply -f awx-operator/pvc.yaml

## Install deployment
- kubectl apply -f awx-operator/deployment.yaml
