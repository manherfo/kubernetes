# Probes

  kubelet tests the containers inside pods by:

  * command
  * tcp -> port x
  * http -> "/path" 200-399 responses

* ## kind of probes

  * liveness: if it works
  * readiness: if it stated as expected
  * start up: if it takes too long to start 

* sdf

You can create namespaces from a template writing the specification in a YAML file, the first example was taken from:

* [namespaces templates](https://kubernetes.io/docs/tasks/administer-cluster/namespaces/#creating-a-new-namespace)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`
`kubectl api-resources`

* ## Create namespace
  
  * By CLI: 

`kubectl create resource-quota`
`kubectl create namespace --show-labels`

  * By YAML:

`kubectl create -f .yaml`

* ## list namespaces

`kubectl get resourcequotas -n namespace`

* ## list nodes 

`kubectl get nodes`
`kubectl describe nodename`

* ## list all resources from each namespace

`kubectl get all -n namespace`

* ## Default kube-namespaces
  * kube-public:
  * kube-system: core resources
  
* ## delete pods from specific namespace

`kubectl delete pods $podname -n namespace`

* ## delete namespace

`kubectl delete namespaces namespace`
`kubectl delete -f namespace.yaml`

* ## namespaces dns

serviceName + namespaceName + service.cluster.local

* # Contexts


`kubectl config view`