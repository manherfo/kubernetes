# configmap

  It is a key, value file and it's posible to change the pod config with a config map

  * It can be created from a file or from a manifest.
  * The Pods can consume its content from a file (config.file.key) or from a shared volume

* ## Create configmap
  
  * By CLI: 

`kubectl create configmap nginx-config --from-file=nginx-cm-from-file.conf`

  you are able to create a configmap with the conten from an entire folder

`kubectl create configmap nginx-config --from-file=.`

  * By YAML:

`kubectl create -f .yaml`

* ## list configmaps

`kubectl get cm(configmaps)`

* ## describ configmaps 

`kubectl describe configmaps name`

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