# ReplicaSet

It will create PODs and will be the owner of the specific pod it creates, managing them by `labels`.

* ## Replica Set templates

You can run Replica Sets from a template writing the specification in a YAML file, the first example was taken from:

* [POD templates](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/#example)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`
`kubectl api-resources`

* ### Run Replica sets from templates

`kubectl apply -f replicaset.yaml`

* ### Delete Replica sets from templates

`kubectl delete -f replicaset.yaml`

* ## View logs from different cointainers in a single POD

`kubectl logs ${podname} -c ${containername}`

* ## Execute commands inside different containers in a single POD

`kubectl exec -ti ${podname} -c ${containername} -- sh`

* ## list Replica sets

`kubectl get replicaset`
`kubectl get rs`

* ## See Yaml from a Replica Set

`kubectl get rs rs-test -o yaml`

if you look for the owner reference from the POD metadata, you'll find that it'll match with the replicaset metadata.

* ## add label to a POD

`kubectl label pods ${podname} ${key}=${value}`

* ## Replica Sets problems

  * you can't update pods configurations (like the image or # of containers)
