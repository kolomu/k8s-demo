# README

Sources:
[1. Creating the referenced Docker Image](https://www.youtube.com/watch?v=3c-iBn73dDE)
[2. Kubernetes Crash Course for Absolute Beginners](https://www.youtube.com/watch?v=s_o8dwzRlu4)

- mongo-config.yaml see: [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/)
- mongo-secret.yaml see: [Secret](https://kubernetes.io/docs/concepts/configuration/secret/)
  - encode value: `echo -n mongouser | base64`
- mongo.yaml see: [Creating a Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

**Label**
- labels do not provide uniquess
- e.g. all Pod replicas will have same label
- connecting Deployment to all Pod replicas
- each pod will have unique name but can share same label

| Name         | Pod1        | Pod2        | Pod3        |
| -------------| ----------- | ----------- | ----------- |
| Unique Name  | mongo-101   | mongo-111   | mongo-210   |
| Common Label | app:nginx   | app:nginx   | app:nginx   |


**Label Selectors**
- how does k8s know which Pod belong to it?
- `selector: matchLabels:`


**Yaml File**
3 dashes = `---` multiple YAML configuration files within 1 file

**Handling Secrets**
- mongodb creates `Username` and `Password` when it starts -> can be used in webapp

## Deploy WebApp with MongoDB
- `kubectl apply -f mongo-config.yaml`
- `kubectl apply -f mongo-secret.yaml`
- `kubectl apply -f mongo.yaml`
- `kubectl apply -f webapp.yaml`

- check configuration 
- `kubectl get all`
- `kubectl get configmap`
- `kubectl get secret`


get pod information: `kubectl get pod`
get logs for pod: `kubectl logs webapp-deployment-dcffd6bcc-9wjxf -f`

get service ip: `kubectl get svc` -> nodePort -> get ip address of minikube `minikube ip`