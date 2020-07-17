# Nodes 

<details>
<summary>
<b>Available ImagePullPolicies</b>
</summary>
Always, Never, IfNotPresent (default)
</details>

<details>
<summary>
<b>_____ allow a node to repel a set of Pods, based on certain properties of the node.</b>
</summary>
Taints
</details>

<details>
<summary>
<b>A Kubernetes cluster consists of two types of resources...</b>
</summary>
Master and Nodes
</details>

<details>
<summary>
<b>A _____ is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster.&nbsp;</b>
</summary>
Node
</details>

<details>
<summary>
<b>Is it possible to run DaemonSet pods on only some nodes?</b>
</summary>
Yes - with taints and affinities
</details>

<details>
<summary>
<b>To prevent a kubelet from self-registering the node in the control-plane, you could pass the _____ flag.</b>
</summary>
--register-node=false
</details>

<details>
<summary>
<b>A node's <b>DiskPressure </b>is True when...</b>
</summary>
The node's disk capacity is low
</details>

<details>
<summary>
<b>A Node's <b>MemoryPressure </b>is True when...</b>
</summary>
The node's memory is low
</details>

<details>
<summary>
<b>A Node's <b>PIDPressure</b>&nbsp;is True when...</b>
</summary>
There are too many processes running
</details>

<details>
<summary>
<b>A Node's <b>NetworkUnavailable</b>&nbsp;is True when...</b>
</summary>
The Node's network is not correctly configured
</details>

<details>
<summary>
<b>Node heartbeats are sent by...</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>A Node's "Ready" status is False when...</b>
</summary>
It's unhealthy and not accepting pods
</details>

<details>
<summary>
<b>A _____ is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster.</b>
</summary>
Node
</details>

<details>
<summary>
<b>A node's status contains four domains of information.These are...</b>
</summary>
Addresses
Conditions
Capacity and Allocatable
Info
</details>

<details>
<summary>
<b>Addresses in a node's status include...</b>
</summary>
HostName, InternalIP, ExternalIP
</details>

<details>
<summary>
<b>Capacity fields describe the total amount of _____ that a Node has</b>
</summary>
resources
</details>

<details>
<summary>
<b>The Kubernetes control plane component that manages various aspects of nodes is the...</b>
</summary>
Node controller
</details>

<details>
<summary>
<b>The three roles of the <b>Node Controller </b>in a Node's life</b>
</summary>
CIDR block assignment

Synchronize internal list of nodes
Node health monitoring
</details>

<details>
<summary>
<b>Two types of node Heartbeats</b>
</summary>
NodeStatus updates
Lease Object
</details>

<details>
<summary>
<b>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</b>
</summary>
operating system
node component versions
</details>

<details>
<summary>
<b>A Node's "Ready" status is Unknown when...</b>
</summary>
40 seconds have passed since the Node Controller has heard from the node
</details>

<details>
<summary>
<b>In terms of network, the Node Controller assigns a _____ to a Node upon its registration.</b>
</summary>
CIDR block
</details>

<details>
<summary>
<b>A Pod always runs on a...</b>
</summary>
Node
</details>

<details>
<summary>
<b>Each Kubernetes Node is managed by the....</b>
</summary>
Master
</details>

<details>
<summary>
<b>When a node self-registers to the control plane, which component is responsible?</b>
</summary>
kubelet
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
<b>Allocatable describes the amount of the Node's resources that are _____</b>
</summary>
available to be consumed by Pods
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></b>
</summary>
node labels
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></b>
</summary>
bypassed
</details>

<details>
<summary>
<b>A Node's "Ready" status is True when...</b>
</summary>
It's healthy and accepts pods
</details>

<details>
<summary>
<b>_____ are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won’t be scheduled on nodes with them.</b>
</summary>
Taints
</details>

<details>
<summary>
<b>The kubernetes components inside a worker node are...</b>
</summary>
kubelet, kube-proxy, container runtime
</details>

<details>
<summary>
<b>_____ allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.</b>
</summary>
Tolerations
</details>

<details>
<summary>
<b>Pod _____ express a preference for Pods to be scheduled on the same node as other Pods, when they benefit from it.</b>
</summary>
affinities
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler&nbsp;</span><span style="color: rgb(34, 34, 34);">tries to place a _____ number of Pods into each topology domain</span></b>
</summary>
balanced
</details>

<details>
<summary>
<b><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler treats both Nodes as being in the same _____&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">topology&nbsp;</span>
</details>

<details>
<summary>
<b>_____ attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.</b>
</summary>
Node affinities
</details>

<details>
<summary>
<b>While _____ can block a Pod from running on a node, _____ are more like suggestions to the scheduler. You can combine multiple, with different weights.</b>
</summary>
hard node affinities
soft node affinities
</details>

