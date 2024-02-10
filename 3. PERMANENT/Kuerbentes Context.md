---
type: evidence
topic: kubernetes
---
- Topic : #kubernetes 
- Tags : #VeilleIT/Sysadmin #VeilleIT/devops 

# Idea

Manage multiple Kubernetes cluster into the same kubectl config file to be able to switch between context

## Use context 

```Bash
kubectl get-contexts
kubectl use-context medtra-dev
```

## Merge a new cluster into an existing kubeconfig file

Copy all section of the kubeconfig file provided into your own kubeconfig file
- cluster 
- context
- user

```yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: XXXXX
    server: https://kubernetes.docker.internal:6443
  name: docker-desktop
- cluster:
    insecure-skip-tls-verify: true
    server: https://kube.cluster1.test.fake:6443
  name: medtra-dev
- cluster:
    certificate-authority: C:\Users\AMON\.minikube\ca.crt
    server: https://172.28.76.45:8443
  name: minikube
- cluster:
    certificate-authority-data: L0K
    server: https://172.21.235.10:6443
  name: rancher-desktop
contexts:
- context:
    cluster: docker-desktop
    user: docker-desktop
  name: docker-desktop
- context:
    cluster: medtra-dev
    user: medtra-dev
  name: medtra-dev
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
- context:
    cluster: rancher-desktop
    user: rancher-desktop
  name: rancher-desktop
current-context: medtra-dev
kind: Config
preferences: {}
users:
- name: docker-desktop
  user:
    client-certificate-data: LXXXX
    client-key-data: XXXXQXXX
- name: medtra-dev
  user:
    token: XXX
- name: minikube
  user:
    client-certificate: C:\Users\AMON\.minikube\profiles\minikube\client.crt
    client-key: C:\Users\AMON\.minikube\profiles\minikube\client.key
- name: rancher-desktop
  user:
    client-certificate-data: XXXXX
    client-key-data: AXXo=

```

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to manage all kubernetes clusters]]

## South : What does it lead to

