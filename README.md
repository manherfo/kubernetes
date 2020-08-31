
# kubernetes

* ## Kubernetes cluster

You will need to install a cluster emulator to create a kubernetes cluster, you will see two options (we'll use Mac's solution):

* ### Mac's kubernetes feature

Download Docker for mac:

* [Install Docker for mac](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/2.39.0)

then, you will have to enable de kubernetes feature:

Click the Docker icon in the status bar, go to “Preferences”, and on the “Kubernetes”-tab, check “Enable Kubernetes”. This will start a single node Kubernetes cluster for you and install the kubectl command line utility. This might take a while, but the dialog will let you know once the Kubernetes cluster is ready.

* ### Minikube

Install minikube following the instructions:

* [Install minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)

#### You can also use the mac's kubernetes feature

* ## install kubectl

Then you will have to install the kubernetes controller comman **kubectl**, following:

* [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

* ## PODS
  
The minimun kubernetes unity.

One or more continers sharing namespaces between them:

* network
* IPC(inter process communication)
* UTS (hostmane).
* One only ip for every single POD.

* ### creating our first POD

`kubectl run --generator=run-POD/v1 podtest --image=nginx:alpine`

the output of this command should look like this:

`POD/podtest created`

We can run `kubectl get PODs` and the output should look like this:

```$ kubectl get PODs
NAME      READY   STATUS    RESTARTS   AGE
podtest   1/1     Running   0          12m
```

Now what is that mean?

* **NAME**: the name of the POD created.
* **READY**: the number of running containers inside the POD.
* **STATUS**: the status of the POD.
* **RESTARTS**: the number of restarts of the POD.
* **AGE**: the age of the POD since it was created.

If something is wrong with the POD's creation, the **STATUS** field will tell you that something is wrong but to know read something clearer you can run (you can run this commando not just to do troubleshoot but you can see the POD's configuration):

`kubectl describe POD $POD_name`, in this case replace **$POD_name** for podtest

```$ kubectl describe POD podtest
Name:         podtest
Namespace:    default
Priority:     0
Node:         docker-desktop/192.168.65.3
Start Time:   Sun, 26 Jul 2020 18:54:02 -0500
Labels:       run=podtest
Annotations:  <none>
Status:       Running
IP:           10.1.0.9
IPs:
  IP:  10.1.0.9
Containers:
  podtest:
    Container ID:   docker://45f0741dc386505bca4fe6930856f8cbc83adf1449b5da889a53bf617188ca74
    Image:          nginx:alpine
    Image ID:       docker-pullable://nginx@sha256:ee8c35a6944eb3cc415cd4cbeddef13927895d4ffa50b976886e3abe48b3f35a
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Sun, 26 Jul 2020 18:54:02 -0500
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-2cczl (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PODScheduled      True
Volumes:
  default-token-2cczl:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-2cczl
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age    From                     Message
  ----    ------     ----   ----                     -------
  Normal  Scheduled  2m58s  default-scheduler        Successfully assigned default/podtest to docker-desktop
  Normal  Pulled     2m58s  kubelet, docker-desktop  Container image "nginx:alpine" already present on machine
  Normal  Created    2m58s  kubelet, docker-desktop  Created container podtest
  Normal  Started    2m58s  kubelet, docker-desktop  Started container podtest
```

* ### deleting POD

`kubectl delete POD podtest`, the output should look like this:

`POD "podtest" deleted`

* ## PODS from YAML file

You can define a YAML file where the POD configuration will be written, but first, you can ask with **kubectl** for the YAML of the POD created without one with the following command:

`kubectl get POD podtest -o yaml`

* ## Execute commands inside container POD
  
you can go inside a container and execute some comands in order to do some workarounds and test things.

`kubctl exec -ti podtest -- sh`

* ## Se the logs from your aplication running in a POD

`kubectl logs podtest`

or if you want to follow in real time the logs:

`kubectl logs podtest -f`
