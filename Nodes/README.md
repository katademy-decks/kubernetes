# Nodes 

<details>
<summary>
<b>Convert the "nginx" ClusterIP service to NodePort and find the NodePort port. Hit it using Node's IP.</b>
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
<b><div style="">List 3 components that every Kubernetes Node has</div></b>
</summary>
<div style="">1. <b>kubelet</b>, a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
2. <b>kube-proxy</b>, a proxy that maintains network rules on nodes.</div>3.&nbsp;<div style="display: inline !important;"><b>container runtime </b>(like Docker) responsible for pulling the container image from a registry, unpacking the container, and running the application.
</div>
<img src="paste-0d78f3f9993df127ff9365555478608a03a8904f.jpg">
</details>

<details>
<summary>
<b>What is a node pool?</b>
</summary>
<b>A group of nodes within a cluster that all have the same configuration</b>

<img src="paste-3d68d8e58746cbf4aed5beb32f7857fc7601156f.jpg">
<img src="paste-75313fe7c14867e5f60723d98b3f6c0f00afb66a.jpg">
</details>

<details>
<summary>
<b>How many master nodes does a Kubernetes cluster contain (assuming no high availability features)?</b>
</summary>
1

<img src="paste-331274bc09622c2e5c6b92c3e36981ae6931f602.jpg">
</details>

<details>
<summary>
<b>To list your busiest nodes, by the number of Pods running on each:</b>
</summary>
kubectl get pods -o json --all-namespaces | 
jq '.items | group_by(.spec.nodeName) | 
map({"nodeName": .[0].spec.nodeName, "count": length}) | 
sort_by(.count) | 
reverse'
</details>

<details>
<summary>
<b>Add AntiAffinity such that Pod will&nbsp;<em>not</em>&nbsp;be scheduled on any node matching this rule.</b>
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
<b>How to add/remove taint to a node?</b>
</summary>
<strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule</strong><div><strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule-
</strong><b>
</b>apiVersion: v1
kind: Pod
...
spec:
 &nbsp;tolerations:
 &nbsp;- key: "dedicated"
 &nbsp;&nbsp;&nbsp;operator: "Equal"
 &nbsp;&nbsp;&nbsp;value: "true"
 &nbsp;&nbsp;&nbsp;effect: "NoSchedule"<b>
</b><div><strong>
</strong></div></div>
</details>

<details>
<summary>
<b>Kubernetes runs your workload by placing containers into Pods to run on...</b>
</summary>
Nodes
</details>

<details>
<summary>
<b>Are nodes virtual machines?</b>
</summary>
Not always<div>
</div><div>They can be physical machines</div>
</details>

<details>
<summary>
<b>When a node self-registers to the control plane, which component is responsible?</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>To prevent a node from self-registering on the control-plane, you could...</b>
</summary>
<div>Pass this flag to the kubelet:</div><div><b>--register-node=false</b>
</div>
</details>

<details>
<summary>
<b>kubectl cordon NODE</b>
</summary>
Mark a node unschedulable
</details>

<details>
<summary>
<b>kubectl drain NODE</b>
</summary>
Cordons the node then evicts/deletes all pods.<div>
</div><div>Does not deleted mirror pods or DaemonSet pods (DS controller ignores unschedulable markings)</div><div>
</div><div><b>--ignore-daemonsets</b></div><div>Ignore DS managed pods</div><div>
</div><div><b>--force</b></div><div>Continue even if there are dangling pods</div><div>
</div><div><b>--delete-local-data</b></div><div>Continue even if there are pods with <b>EmptyDir</b>&nbsp;(local data that is removed upon draining)</div>
</details>

<details>
<summary>
<b>kubectl taint (?)</b>
</summary>
<div>kubectl taint NODE KEY=VAL:EFFECT</div><div>
</div><div><b>--overwrite</b></div>
</details>

<details>
<summary>
<b>todo</b>
</summary>
<div>Sent by kubelets, help determine the availability of a node.&nbsp;</div><div>
</div><div>1) updates of&nbsp;<code>NodeStatus</code>&nbsp;</div><div>2)&nbsp;<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#lease-v1-coordination-k8s-io">Lease object</a>.&nbsp;</div><div>
</div><div>Each Node has an associated Lease object in the&nbsp;<code>kube-node-lease</code>&nbsp;<a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces">namespace</a>&nbsp;which improves the performance of the node heartbeats as the cluster scales.</div>
</details>

<details>
<summary>
<b>What is Node Affinities?&nbsp;</b>
</summary>
<div>Schedule pods on selector'd nodes preferentially or not</div><div>
</div><div><b>requiredDuringSchedulingIgnoredDuringExecution</b></div><div><b>preferredDuringSchedulingIgnoredDuringExecution</b>&nbsp;</div><div>
<b>spec:
 &nbsp;affinity:
 &nbsp;&nbsp;&nbsp;nodeAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nodeSelectorTerms:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: "failure-domain.beta.kubernetes.io/zone"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["us-central1-a"]</b>
</div>
</details>

<details>
<summary>
<b>Worker node components</b>
</summary>
<b>kubelet</b><div>Controls node, provides api for control plane</div><div>
</div><div><b>kube-proxy</b></div><div>Configs iptables and virtual network</div><div>
</div><div><b>Container runtime</b></div><div>Downloads and runs containers
</div>
</details>

<details>
<summary>
<b>kubectl uncordon</b>
</summary>
Mark a node schedulable
</details>

<details>
<summary>
<b>kubectl top node NODE_NAME</b>
</summary>
Display resource usage of nodes
</details>

<details>
<summary>
<b>A node's status containts four domains of information.<div>These are...</div></b>
</summary>
Addresses<div>
</div><div>Conditions</div><div>
</div><div>Capacity and Allocatable</div><div>
</div><div>Info</div>
</details>

<details>
<summary>
<b>kubectl command to view a Node's status and other details</b>
</summary>
<b>kubectl describe node &lt;node-name&gt;</b>
</details>

<details>
<summary>
<b>The usage of the "Addresses" status fields depends on...</b>
</summary>
your cloud provider or bare metal configuration
</details>

<details>
<summary>
<b>Addresses in a node's status include...</b>
</summary>
<div>ExternalIP
</div><div>
</div><div>InternalIP</div><div>
</div><div>HostName
</div>
</details>

<details>
<summary>
<b>HostName</b>
</summary>
The hostname reported by the node's kernel<div>
</div><div>Can be overridden via <b>--hostname-override</b></div>
</details>

<details>
<summary>
<b>ExternalIP</b>
</summary>
The IP address of the node available from outside the cluster
</details>

<details>
<summary>
<b>InternalIP</b>
</summary>
The IP address of the node routable only from inside the cluster
</details>

<details>
<summary>
<b>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</b>
</summary>
OS Name<div>
</div><div>kubelet, kube-proxy, docker versions</div>
</details>

<details>
<summary>
<b>Ready</b>
</summary>
<b>True</b><div>if the node is healthy and ready to accept pods</div><div><b>
</b></div><div><b>False</b></div><div>if the node us unhealthy and is not accepting pods</div><div><b>
</b></div><div><b>Unknown</b></div><div>If the node controller has not heard from the node in the last 40 seconds</div>
</details>

<details>
<summary>
<b>DiskPressure</b>
</summary>
<b>True</b><div>if the node's disk capacity is low</div>
</details>

<details>
<summary>
<b>MemoryPressure</b>
</summary>
<b>True</b><div>if the node's memory is low</div>
</details>

<details>
<summary>
<b>PIDPressure</b>
</summary>
<b>True</b>&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
<b>PIDPressure</b>
</summary>
<b>True</b>&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
<b>NetworkUnavailable</b>
</summary>
<b>True</b>&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
<b>NetworkUnavailable</b>
</summary>
<b>True</b>&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
<b>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b><div>
</div><div>What happens to the Pods on the node?</div></b>
</summary>
All Pods on the node are scheduled for deletion by the node controller
</details>

<details>
<summary>
<b>Capacity</b>
</summary>
<div>Capacity fields describe the total amount of resources that a Node has</div>
</details>

<details>
<summary>
<b>Allocatable</b>
</summary>
Describes the amount of the Node's resources that are available to be consumed by Pods
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
<b>The three roles of the <b>Node Controller </b>in a Node's life</b>
</summary>
<div><b>CIDR block assignment</b>
</div><div>Assigns a CIDR block to each node upon registration (if enabled)</div><div><hr></div><div><b>List of nodes</b></div><div>Synchronizes the Node Controller's internal list of nodes with the <b>cloud provider</b>'s list of available machines</div><div><hr></div><div><b>Node health monitoring</b></div><div>Manages a node's&nbsp;<b>Ready</b>&nbsp;condition depending on reachability. Evicts the node's pods if it remains unreachable</div>
</details>

<details>
<summary>
<b>Node heartbeats are sent by...</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>Node heartbeats are sent by...</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>Two types of node Heartbeats</b>
</summary>
1. updates of <b>NodeStatus</b><div>
2. The <b>Lease Object</b></div>
</details>

<details>
<summary>
<b>CAdvisor</b>
</summary>
A daemon in the kubelet that discovers, monitors and exports data on containers
</details>

