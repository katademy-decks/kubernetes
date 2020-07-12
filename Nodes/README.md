# Nodes 

<details>
<summary>
<b>Kubernetes Master controls...</b>
</summary>
Kubernetes nodes
</details>

<details>
<summary>
<b>List 3 components that every Kubernetes Node has</b>
</summary>
1. <b>kubelet</b>, a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
2. <b>kube-proxy</b>, a proxy that maintains network rules on nodes.3.&nbsp;<div style="display: inline !important;"><b>container runtime </b>(like Docker) responsible for pulling the container image from a registry, unpacking the container, and running the application.

<img src="paste-0d78f3f9993df127ff9365555478608a03a8904f.jpg">
</details>

<details>
<summary>
<b>What's the name of a Kubernetes entity that executes workloads?</b>
</summary>
Node

<img src="paste-2dd3a0d3b489fe0cc29ee86ddb9283470450af35.jpg">
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
<b>Image Pull Policy by kubernetes to node</b>
</summary>
* Always pull* Never pull* IfNotPresent pull (default)
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
<b>Kubernetes runs your workload by placing containers into Pods to run on...</b>
</summary>
Nodes
</details>

<details>
<summary>
<b>Are nodes virtual machines?</b>
</summary>
Not always
They can be physical machines
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
Pass this flag to the kubelet:<b>--register-node=false</b>
</details>

<details>
<summary>
<b>A node's status containts four domains of information.These are...</b>
</summary>
Addresses
Conditions
Capacity and Allocatable
Info
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
ExternalIP

InternalIP
HostName
</details>

<details>
<summary>
<b>HostName</b>
</summary>
The hostname reported by the node's kernel
Can be overridden via <b>--hostname-override</b>
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
<b>Ready</b>
</summary>
<b>True</b>if the node is healthy and ready to accept pods<b>
</b><b>False</b>if the node us unhealthy and is not accepting pods<b>
</b><b>Unknown</b>If the node controller has not heard from the node in the last 40 seconds
</details>

<details>
<summary>
<b>DiskPressure</b>
</summary>
<b>True</b>if the node's disk capacity is low
</details>

<details>
<summary>
<b>MemoryPressure</b>
</summary>
<b>True</b>if the node's memory is low
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
<b>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b>
What happens to the Pods on the node?</b>
</summary>
All Pods on the node are scheduled for deletion by the node controller
</details>

<details>
<summary>
<b>Capacity</b>
</summary>
Capacity fields describe the total amount of resources that a Node has
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
<b>CIDR block assignment</b>
Assigns a CIDR block to each node upon registration (if enabled)<hr><b>List of nodes</b>Synchronizes the Node Controller's internal list of nodes with the <b>cloud provider</b>'s list of available machines<hr><b>Node health monitoring</b>Manages a node's&nbsp;<b>Ready</b>&nbsp;condition depending on reachability. Evicts the node's pods if it remains unreachable
</details>

<details>
<summary>
<b>Two types of node Heartbeats</b>
</summary>
1. updates of <b>NodeStatus</b>
2. The <b>Lease Object</b>
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
<b>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</b>
</summary>
OS Name
kubelet, kube-proxy, docker versions
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">This namespace for the lease objects associated with each node which improves the performance of the node heartbeats as the cluster scales is...</span></b>
</summary>
kube-node-lease
</details>

<details>
<summary>
<b>todo</b>
</summary>
Sent by kubelets, help determine the availability of a node.&nbsp;
1) updates of&nbsp;<code>NodeStatus</code>&nbsp;2)&nbsp;<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#lease-v1-coordination-k8s-io">Lease object</a>.&nbsp;
Each Node has an associated Lease object in the&nbsp;<code>kube-node-lease</code>&nbsp;<a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces">namespace</a>&nbsp;which improves the performance of the node heartbeats as the cluster scales.
</details>

<details>
<summary>
<b>CAdvisor</b>
</summary>
A daemon in the kubelet that discovers, monitors and exports data on containers
</details>

<details>
<summary>
<b>What is Node Affinities?&nbsp;</b>
</summary>
Schedule pods on selector'd nodes preferentially or not
<b>requiredDuringSchedulingIgnoredDuringExecution</b><b>preferredDuringSchedulingIgnoredDuringExecution</b>&nbsp;
<b>spec:
 &nbsp;affinity:
 &nbsp;&nbsp;&nbsp;nodeAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nodeSelectorTerms:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: "failure-domain.beta.kubernetes.io/zone"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["us-central1-a"]</b>
</details>

<details>
<summary>
<b>Worker node components</b>
</summary>
<b>kubelet</b>Controls node, provides api for control plane
<b>kube-proxy</b>Configs iptables and virtual network
<b>Container runtime</b>Downloads and runs containers
</details>

<details>
<summary>
<b>What are taints and&nbsp;<strong>tolerations</strong>?</b>
</summary>
<em>Taints</em>&nbsp;allow a node to repel a set of Pods, based on certain properties of the node.
</details>

