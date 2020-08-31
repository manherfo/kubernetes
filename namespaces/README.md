# namespaces and Contexts

It is a logical split to create "virtual clusters" within a "global cluster" and you can specify for each "virtual cluster/namespace" the limits and user access for each namespace. There is a default namespace called "default"

* ## namespaces templates

You can create namespaces from a template writing the specification in a YAML file, the first example was taken from:

* [namespaces templates](https://kubernetes.io/docs/tasks/administer-cluster/namespaces/#creating-a-new-namespace)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`
`kubectl api-resources`

* ## Create namespace
  
  * By CLI: 

`kubectl create namespace`
`kubectl create namespace --show-labels`

  * By YAML:

`kubectl create -f namespace.yaml`

* ## list namespaces

`kubectl get namespace`

* ## list pods by namespace

`kubectl get pods --namespace default`
`kubectl get pods -n default`

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