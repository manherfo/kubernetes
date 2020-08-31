# secrets

  environment variables as sensitive values

  * It can be created from a file or from a manifest.
  * The Pods can consume its content from a file (config.file.key) or from a shared volume

* ## Create configmap
  
  * By CLI: 

`kubectl create secret generic mysecret --from-file=secrets.txt`

  you are able to create a configmap with the conten from an entire folder

`kubectl create secret nginx-config --from-file=.`

  * By YAML:

`kubectl create -f .yaml`

* ## list configmaps

`kubectl get csecrets`

* ## describ configmaps 

`kubectl describe secrets name`

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