# Nodes 

<details>
<summary>_____ allow a node to repel a set of Pods, based on certain properties of the node.</summary>
Taints
<br></details><details>
<summary>A Kubernetes cluster consists of two types of resources...</summary>
Master and Nodes
<br></details><details>
<summary>A _____ is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster.&nbsp;</summary>
Node
<br></details><details>
<summary>Is it possible to run DaemonSet pods on only some nodes?</summary>
Yes - with taints and affinities
<br></details><details>
<summary>To prevent a kubelet from self-registering the node in the control-plane, you could pass the _____ flag.</summary>
--register-node=false
<br></details><details>
<summary>A node's <b>DiskPressure </b>is True when...</summary>
The node's disk capacity is low
<br></details><details>
<summary>A Node's <b>MemoryPressure </b>is True when...</summary>
The node's memory is low
<br></details><details>
<summary>A Node's <b>PIDPressure</b>&nbsp;is True when...</summary>
There are too many processes running
<br></details><details>
<summary>A Node's <b>NetworkUnavailable</b>&nbsp;is True when...</summary>
The Node's network is not correctly configured
<br></details><details>
<summary>Node heartbeats are sent by...</summary>
kubelet
<br></details><details>
<summary>A Node's "Ready" status is False when...</summary>
It's unhealthy and not accepting pods
<br></details><details>
<summary>A _____ is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster.</summary>
Node
<br></details><details>
<summary>A node's status contains four domains of information.These are...</summary>
Addresses
Conditions
Capacity and Allocatable
Info
<br></details><details>
<summary>Addresses in a node's status include...</summary>
HostName, InternalIP, ExternalIP
<br></details><details>
<summary>Capacity fields describe the total amount of _____ that a Node has</summary>
resources
<br></details><details>
<summary>The Kubernetes control plane component that manages various aspects of nodes is the...</summary>
Node controller
<br></details><details>
<summary>The three roles of the <b>Node Controller </b>in a Node's life</summary>
CIDR block assignment

Synchronize internal list of nodes
Node health monitoring
<br></details><details>
<summary>Two types of node Heartbeats</summary>
NodeStatus updates
Lease Object
<br></details><details>
<summary>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</summary>
operating system
node component versions
<br></details><details>
<summary>A Node's "Ready" status is Unknown when...</summary>
40 seconds have passed since the Node Controller has heard from the node
<br></details><details>
<summary>In terms of network, the Node Controller assigns a _____ to a Node upon its registration.</summary>
CIDR block
<br></details><details>
<summary>A Pod always runs on a...</summary>
Node
<br></details><details>
<summary>Each Kubernetes Node is managed by the....</summary>
Master
<br></details><details>
<summary>When a node self-registers to the control plane, which component is responsible?</summary>
kubelet
<br></details><details>
<summary>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b>
What happens to the Pods on the node?</summary>
All Pods on the node are scheduled for deletion by the node controller
<br></details><details>
<summary>Allocatable describes the amount of the Node's resources that are _____</summary>
available to be consumed by Pods
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></summary>
node labels
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If an incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></summary>
bypassed
<br></details><details>
<summary>A Node's "Ready" status is True when...</summary>
It's healthy and accepts pods
<br></details><details>
<summary>_____ are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won’t be scheduled on nodes with them.</summary>
Taints
<br></details><details>
<summary>The kubernetes components inside a worker node are...</summary>
kubelet, kube-proxy, container runtime
<br></details><details>
<summary>_____ allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.</summary>
Tolerations
<br></details><details>
<summary>Pod _____ express a preference for Pods to be scheduled on the same node as other Pods, when they benefit from it.</summary>
affinities
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler&nbsp;</span><span style="color: rgb(34, 34, 34);">tries to place a _____ number of Pods into each topology domain</span></summary>
balanced
<br></details><details>
<summary><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler treats both Nodes as being in the same _____&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">topology&nbsp;</span>
<br></details><details>
<summary>_____ attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.</summary>
Node affinities
<br></details><details>
<summary>While _____ can block a Pod from running on a node, _____ are more like suggestions to the scheduler. You can combine multiple, with different weights.</summary>
hard node affinities
soft node affinities
<br></details>