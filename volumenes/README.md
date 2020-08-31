# volumes

  Created to persis data in an object

  * ## types:

    * EmptyDir: creates a volume as pod level, and not as container
    * hostPath: creates a volume as nod lavel
    * cloud: external volume (aws: ebs)
      * pv: create volume in cloud
      * pvc: volume claimer
        * reclaim:
        * delete: deletes pv and volume
        * recycle: reuse a volume
        * retain: de volume previously created

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