
# Manifests

* ## Pod templates

You can run PODs from a template writing the specification in a YAML file, the first example was taken from:

* [POD templates](https://kubernetes.io/docs/concepts/workloads/pods/#pod-templates)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`

`kubectl api-resources`

* ### Run PODs from templates

`kubectl apply -f pods/pod.yaml`

* ### Delete PODs from templates

`kubectl delete -f pods/pod.yaml`

* ## Run 2 PODS

* ## Run 1 POD with n containers

* ## View logs from different cointainers in a single POD

`kubectl logs ${podname} -c ${containername}`

* ## Execute commands inside different containers in a single POD

`kubectl exec -ti ${podname} -c ${containername} -- sh`

* ## view logs from POD by its label

`kubectl get pods -l app=${label}`
