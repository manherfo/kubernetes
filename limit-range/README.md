# limits ranges

  ## requests

  It is a request from pods for hardware resources at namespace level for each resourse inside the namespace

  ## limits
  
  It is a limit for pods regarding hardware

* ## namespaces templates

You can create namespaces from a template writing the specification in a YAML file, the first example was taken from:

* [limit ranges templates](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/memory-default-namespace/)

The values written in this pod.yaml were selected executing the following commands:

`kubectl api-versions`
`kubectl api-resources`

* ## list limitranges

`kubectl get limitranges -n namespace`

* ## describe limit ranges
`kubectl describe limitrange -n namespace`