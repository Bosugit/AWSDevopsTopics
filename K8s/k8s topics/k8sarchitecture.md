Kubernets:


By default it is cluster nature

autohealing capability

autoscaing capbility.

architecutre :

Control Plane:
    ApiServer,etcd,schedular,controller,cloducontrollermanager 

Data plane or workernode:
    kubelet,kubeproxy,container runtime.

Control plane:

  Apisrever:  
           The purpose of API server is it takes all the incoming request ,that basically exposes to kuberntes to the external world.
           the heart of k8s is Apiserver.

   schedular:
          schedular is resposible for go this pod node1 or node2

  etcd: it is basically key value store.it is backup.

  controllermanager:     






Data plane or workernode:
    kubelet,kube proxy,container runtime.

kubelet:
  Basicaly kubelet is resposible for running your pod or creation of your pod.it always ensure that pod is always running state if it not running state it takes the necessary action.

kubeproxy:
  Basically resposible for networking like  generating ipaddress ,load balancing ,iptables in your linux machines.

container runtime:

   which is respobile for running your container.



notes:

when you running a container ,you need run time enviornment that is containerruntime.

in docker container runtime enviornment is dockershim

request alway go through controlplane.

similar to docker your pod got deployed.you have componebt kublet.Basicaly kubelet is resposible for running your pod.

In docker basically we have docker engine or dockershim.In kubernets younhave kubelet which is respooble for maintianing pod.

inside pod you have container.

in docker zero or Default network in docker is bridge networking.this networking is mandatory for runnin gyour pod.

similary in kubenets is kuberpoxy,basically it provides networking.it has to be allocated with ipaddress.


