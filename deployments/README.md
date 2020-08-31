# Deployments

It will create Replica Set versions and will deploy it by a percentage con los `max unavailable` and `max surge` parameters.

* ## Replica Set templates

You can run Deployments from a template writing the specification in a YAML file, the first example was taken from:

* [deployment templates](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#creating-a-deployment)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`
`kubectl api-resources`

* ### Run deployments from templates

`kubectl apply -f deployment.yaml`

* ### Delete Replica sets from templates

`kubectl delete -f deployment.yaml`

* ## View logs from different cointainers in a single POD

`kubectl logs ${podname} -c ${containername}`

* ## Execute commands inside different containers in a single POD

`kubectl exec -ti ${podname} -c ${containername} -- sh`

* ## list deployments

`kubectl get deployment`
`kubectl get deploy`

* ## See Yaml from a deployment

`kubectl get deploy deployment -o yaml`

* ## show deployment's labels

`kubectl get deploy --show-labels`

* ## show status and kind of changes from a deployment

`kubectl rollout status deployment ${deploymentname}`

* ## show history of deployment versions

`kubectl rollout history deployment ${deploymentname}`

* ## show history of deployment versions adding cause

  * Annotating the Deployment with kubectl annotate deployment.v1.apps/nginx-deployment kubernetes.io/change-cause="image updated to 1.16.1"
  * Append the --record flag to save the kubectl command that is making changes to the resource.
  * Manually editing the manifest of the resource.
  
`kubectl apply -f deployment.yaml --record`

adding an annotation in the deployment template:

```Note: You can specify the --record flag to write the command executed in the resource annotation kubernetes.io/change-cause. The recorded change is useful for future introspection. For example, to see the commands executed in each Deployment revision.
```

and in de deployment yaml put:

```---
kind:
metadata:
  annotations:
    kubernetes.io/change-cause: "add your change"
```

or

`kubectl annotate deployment.v1.apps/nginx-deployment kubernetes.io/change-cause="image updated to 1.16.1"`

* ## show history of deployment within specific version

`kubectl rollout history deployment ${deploymentname} --revision=n`

* ## rollback deployment to a previous version

`kubectl rollout undo deployment ${deploymentname --to-revision=n`
