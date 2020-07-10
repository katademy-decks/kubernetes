# Nodes 

<details>
<summary>
Convert the "nginx" ClusterIP service to NodePort and find the NodePort port. Hit it using Node's IP.
</summary>
<i>kubectl edit svc nginx</i>
change the <i>spec.type </i>value to NodePort
<i>spec:</i><div><i>&nbsp; type: NodePort</i>
Find the port and IP with
<i>kubectl get svc</i>
then hit the service with
<i>wget -O- &lt;NodeIP&gt;:&lt;Port&gt;</i></div>
</details>

<details>
<summary>
<div style="">List 3 components that every Kubernetes Node has</div>
</summary>
<div style="">1. *kubelet*, a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
2. *kube-proxy*, a proxy that maintains network rules on nodes.</div>3.&nbsp;<div style="display: inline !important;">*container runtime *(like Docker) responsible for pulling the container image from a registry, unpacking the container, and running the application.
</div>
<img src="paste-0d78f3f9993df127ff9365555478608a03a8904f.jpg">

</details>

<details>
<summary>
What is a node pool?

</summary>
*A group of nodes within a cluster that all have the same configuration*

<img src="paste-3d68d8e58746cbf4aed5beb32f7857fc7601156f.jpg">
<img src="paste-75313fe7c14867e5f60723d98b3f6c0f00afb66a.jpg">

</details>

<details>
<summary>
How many master nodes does a Kubernetes cluster contain (assuming no high availability features)?

</summary>
1

<img src="paste-331274bc09622c2e5c6b92c3e36981ae6931f602.jpg">

</details>

<details>
<summary>
To list your busiest nodes, by the number of Pods running on each:

</summary>
kubectl get pods -o json --all-namespaces | 
jq '.items | group_by(.spec.nodeName) | 
map({"nodeName": .[0].spec.nodeName, "count": length}) | 
sort_by(.count) | 
reverse'

</details>

<details>
<summary>
Add AntiAffinity such that Pod will&nbsp;<em>not</em>&nbsp;be scheduled on any node matching this rule.

</summary>
affinity:
 &nbsp;&nbsp;&nbsp;podAntiAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;labelSelector:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: app
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["server"]
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;topologyKey: kubernetes.io/hostname

</details>

<details>
<summary>
How to add/remove taint to a node?
</summary>
<strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule</strong><div><strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule-
</strong>*
*apiVersion: v1
kind: Pod
...
spec:
 &nbsp;tolerations:
 &nbsp;- key: "dedicated"
 &nbsp;&nbsp;&nbsp;operator: "Equal"
 &nbsp;&nbsp;&nbsp;value: "true"
 &nbsp;&nbsp;&nbsp;effect: "NoSchedule"*
*<div><strong>
</strong></div></div>
</details>

<details>
<summary>
Kubernetes runs your workload by placing containers into Pods to run on...
</summary>
Nodes
</details>

<details>
<summary>
Are nodes virtual machines?
</summary>
Not always<div>
</div><div>They can be physical machines</div>
</details>

<details>
<summary>
When a node self-registers to the control plane, which component is responsible?
</summary>
kubelet
</details>

<details>
<summary>
To prevent a node from self-registering on the control-plane, you could...
</summary>
<div>Pass this flag to the kubelet:</div><div>*--register-node=false*
</div>
</details>

<details>
<summary>
kubectl cordon NODE
</summary>
Mark a node unschedulable
</details>

<details>
<summary>
kubectl drain NODE
</summary>
Cordons the node then evicts/deletes all pods.<div>
</div><div>Does not deleted mirror pods or DaemonSet pods (DS controller ignores unschedulable markings)</div><div>
</div><div>*--ignore-daemonsets*</div><div>Ignore DS managed pods</div><div>
</div><div>*--force*</div><div>Continue even if there are dangling pods</div><div>
</div><div>*--delete-local-data*</div><div>Continue even if there are pods with *EmptyDir*&nbsp;(local data that is removed upon draining)</div>
</details>

<details>
<summary>
kubectl taint (?)
</summary>
<div>kubectl taint NODE KEY=VAL:EFFECT</div><div>
</div><div>*--overwrite*</div>
</details>

<details>
<summary>
todo
</summary>
<div>Sent by kubelets, help determine the availability of a node.&nbsp;</div><div>
</div><div>1) updates of&nbsp;<code>NodeStatus</code>&nbsp;</div><div>2)&nbsp;<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#lease-v1-coordination-k8s-io">Lease object</a>.&nbsp;</div><div>
</div><div>Each Node has an associated Lease object in the&nbsp;<code>kube-node-lease</code>&nbsp;<a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces">namespace</a>&nbsp;which improves the performance of the node heartbeats as the cluster scales.</div>
</details>

<details>
<summary>
What is Node Affinities?&nbsp;

</summary>
<div>Schedule pods on selector'd nodes preferentially or not</div><div>
</div><div>*requiredDuringSchedulingIgnoredDuringExecution*</div><div>*preferredDuringSchedulingIgnoredDuringExecution*&nbsp;</div><div>
*spec:
 &nbsp;affinity:
 &nbsp;&nbsp;&nbsp;nodeAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nodeSelectorTerms:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: "failure-domain.beta.kubernetes.io/zone"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["us-central1-a"]*
</div>
</details>

<details>
<summary>
Worker node components
</summary>
*kubelet*<div>Controls node, provides api for control plane</div><div>
</div><div>*kube-proxy*</div><div>Configs iptables and virtual network</div><div>
</div><div>*Container runtime*</div><div>Downloads and runs containers
</div>
</details>

<details>
<summary>
kubectl uncordon
</summary>
Mark a node schedulable
</details>

<details>
<summary>
kubectl top node NODE_NAME
</summary>
Display resource usage of nodes
</details>

<details>
<summary>
A node's status containts four domains of information.<div>These are...</div>
</summary>
Addresses<div>
</div><div>Conditions</div><div>
</div><div>Capacity and Allocatable</div><div>
</div><div>Info</div>
</details>

<details>
<summary>
kubectl command to view a Node's status and other details
</summary>
*kubectl describe node &lt;node-name&gt;*
</details>

<details>
<summary>
The usage of the "Addresses" status fields depends on...
</summary>
your cloud provider or bare metal configuration
</details>

<details>
<summary>
Addresses in a node's status include...
</summary>
<div>ExternalIP
</div><div>
</div><div>InternalIP</div><div>
</div><div>HostName
</div>
</details>

<details>
<summary>
HostName
</summary>
The hostname reported by the node's kernel<div>
</div><div>Can be overridden via *--hostname-override*</div>
</details>

<details>
<summary>
ExternalIP
</summary>
The IP address of the node available from outside the cluster
</details>

<details>
<summary>
InternalIP
</summary>
The IP address of the node routable only from inside the cluster
</details>

<details>
<summary>
Node *Info*&nbsp;status field describes general information about a node, such as:
</summary>
OS Name<div>
</div><div>kubelet, kube-proxy, docker versions</div>
</details>

<details>
<summary>
Ready
</summary>
*True*<div>if the node is healthy and ready to accept pods</div><div>*
*</div><div>*False*</div><div>if the node us unhealthy and is not accepting pods</div><div>*
*</div><div>*Unknown*</div><div>If the node controller has not heard from the node in the last 40 seconds</div>
</details>

<details>
<summary>
DiskPressure
</summary>
*True*<div>if the node's disk capacity is low</div>
</details>

<details>
<summary>
MemoryPressure
</summary>
*True*<div>if the node's memory is low</div>
</details>

<details>
<summary>
PIDPressure
</summary>
*True*&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
PIDPressure
</summary>
*True*&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
NetworkUnavailable
</summary>
*True*&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
NetworkUnavailable
</summary>
*True*&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
A node is reachable by the *API server *but its&nbsp;*Ready* condition has remained&nbsp;*False* or *Unknown* for longer than the *kube-controller-manager*'s&nbsp;*pod-eviction-timeout*<div>
</div><div>What happens to the Pods on the node?</div>
</summary>
All Pods on the node are scheduled for deletion by the node controller
</details>

<details>
<summary>
Capacity
</summary>
<div>Capacity fields describe the total amount of resources that a Node has</div>
</details>

<details>
<summary>
Allocatable
</summary>
Describes the amount of the Node's resources that are available to be consumed by Pods
</details>

<details>
<summary>
Node controller
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
Node controller
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
The three roles of the *Node Controller *in a Node's life
</summary>
<div>*CIDR block assignment*
</div><div>Assigns a CIDR block to each node upon registration (if enabled)</div><div><hr></div><div>*List of nodes*</div><div>Synchronizes the Node Controller's internal list of nodes with the *cloud provider*'s list of available machines</div><div><hr></div><div>*Node health monitoring*</div><div>Manages a node's&nbsp;*Ready*&nbsp;condition depending on reachability. Evicts the node's pods if it remains unreachable</div>
</details>

<details>
<summary>
Node heartbeats are sent by...
</summary>
kubelet
</details>

<details>
<summary>
Node heartbeats are sent by...
</summary>
kubelet
</details>

<details>
<summary>
Two types of node Heartbeats
</summary>
1. updates of *NodeStatus*<div>
2. The *Lease Object*</div>
</details>

<details>
<summary>
CAdvisor
</summary>
A daemon in the kubelet that discovers, monitors and exports data on containers
</details>

