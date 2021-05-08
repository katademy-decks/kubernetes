<details>
<summary>The 3 possible values for volume.spec.accessMode are:
_____ - Can be used by 1 node_____ - Can be used by many nodes_____ - Can be read from many nodes</summary>
<b>ReadWriteOnce</b>
<b>ReadWriteMany</b>
<b>ReadOnlyMany</b>
<br></details>

<details>
<summary>_____ allow a node to repel a set of Pods, based on certain properties of the node.</summary>
Taints
<br></details>

<details>
<summary>A _____ is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster.&nbsp;</summary>
Node
<br></details>

<details>
<summary>To prevent a kubelet from self-registering the node in the control-plane, you could pass the _____ flag.</summary>
--register-node=false
<br></details>

<details>
<summary>A node's _____ condition<b>&nbsp;</b>is True when its disk capacity is low</summary>
DiskPressure
<br></details>

<details>
<summary>A Node's <b>_____ </b>condition&nbsp;is True when the node's memory is low</summary>
MemoryPressure&nbsp;&nbsp;
<br></details>

<details>
<summary>A Node's <b>_____ </b>condition is&nbsp;True when there are too many processes running.</summary>
PIDPressure
<br></details>

<details>
<summary>A Node's <b>_____&nbsp;</b>condition is True when its network is not correctly configured</summary>
<b>NetworkUnavailable</b>
<br></details>

<details>
<summary>Node heartbeats are sent by...</summary>
kubelet
<br></details>

<details>
<summary>The .spec.____ field is a preference-order list of Node labels, which will be used to sort endpoints when accessing this Service. Traffic will be directed to a Node whose value for the first label matches the originating Node's value for that label. If there is no backend for the Service on a matching Node, then the second label will be considered, and so forth, until no labels remain.</summary>
topologyKeys
<br></details>

<details>
<summary>A Node's "Ready" status is False when...</summary>
It's unhealthy and not accepting pods
<br></details>

<details>
<summary>A _____ is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster.</summary>
Node
<br></details>

<details>
<summary>A node's _____ contains four domains of information - its Addresses, Conditions, Capacity/Allocatable and Info.</summary>
status
<br></details>

<details>
<summary>Addresses in a node's status include...</summary>
HostName, InternalIP, ExternalIP
<br></details>

<details>
<summary>Capacity fields describe the total amount of _____ that a Node has</summary>
resources
<br></details>

<details>
<summary>The Kubernetes control plane component that manages various aspects of nodes is the...</summary>
Node controller
<br></details>

<details>
<summary>The three roles of the <b>Node Controller </b>in a Node's life</summary>
CIDR block assignment

Synchronize internal list of nodes
Node health monitoring
<br></details>

<details>
<summary>Two types of node Heartbeats</summary>
NodeStatus updates
Lease Object
<br></details>

<details>
<summary>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</summary>
operating system
node component versions
<br></details>

<details>
<summary>_____ enables a service to route traffic based upon the Node topology of the cluster.&nbsp;</summary>
Service Topology
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone by using _____</span></summary>
Service Topology
<br></details>

<details>
<summary>A Node's "Ready" status is Unknown when...</summary>
40 seconds have passed since the Node Controller has heard from the node
<br></details>

<details>
<summary>In terms of network, the Node Controller assigns a _____ to a Node upon its registration.</summary>
CIDR block
<br></details>

<details>
<summary>Which Kubernetes component is responsible for a node's self-registration into the control plane?</summary>
kubelet
<br></details>

<details>
<summary>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b>
What happens to the Pods on the node?</summary>
All Pods on the node are scheduled for deletion by the node controller
<br></details>

<details>
<summary>Allocatable describes the amount of the Node's resources that are _____</summary>
available to be consumed by Pods
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If an incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></summary>
bypassed
<br></details>

<details>
<summary>You can control Service traffic routing by specifying the .spec._____&nbsp;field.&nbsp;</summary>
topologyKeys&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice's Endpoints can contain labels about its topology information, such as...</span></summary>
Node - kubernetes.io/hostnameZone - topology.kubernetes.io/zoneRegion - topology.kubernetes.io/region
<br></details>

<details>
<summary>A Node's "Ready" status is True when...</summary>
It's healthy and accepts pods
<br></details>

<details>
<summary>_____ are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won�t be scheduled on nodes with them.</summary>
Taints
<br></details>

<details>
<summary>The kubernetes components inside a worker node are...</summary>
kubelet, kube-proxy, container runtime
<br></details>

<details>
<summary>_____ allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.</summary>
Tolerations
<br></details>

<details>
<summary>Pod _____ express a preference for Pods to be scheduled on the same node as other Pods, when they benefit from it.</summary>
affinities
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler&nbsp;</span><span style="color: rgb(34, 34, 34);">tries to place a _____ number of Pods into each topology domain</span></summary>
balanced
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can use </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;to control&nbsp;</span><span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains&nbsp;</span><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains).</span></summary>
topology spread constraints
<br></details>

<details>
<summary><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler treats both Nodes as being in the same _____&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">topology&nbsp;</span>
<br></details>

<details>
<summary>_____ attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.</summary>
Node affinities
<br></details>

<details>
<summary>While _____ can block a Pod from running on a node, _____ are more like suggestions to the scheduler. You can combine multiple, with different weights.</summary>
hard node affinities
soft node affinities
<br></details>

<details>
<summary>The controller that creates services, endpoints and updates iptables on each node is _____</summary>
kube-proxy
<br></details>

<details>
<summary>The LoadBalancer Service creates an external IP address, but itself does not know any Pod IP's. Instead,&nbsp;it chooses a _____ to send packets to.</summary>
Node
<br></details>

<details>
<summary>A node's _____ tell an incoming packet where in the node to go.</summary>
iptables
<br></details>

<details>
<summary>When running several copies of your Pod for the sake of fault tolerance, the _____ they are running on may still fail. It's important to place your Pods across several of them.</summary>
nodes
<br></details>

<details>
<summary>Restricting access to your cluster _____ can prevent privilege escalation to your cloud provider.</summary>
nodes / VMs (especially master)
<br></details>

<details>
<summary>Node heartbeats are inside the _____ namespace.</summary>
kube-node-lease
<br></details>

<details>
<summary>Are nodes namespaced?</summary>
No
<br></details>

<details>
<summary>Which taints are tolerated by default by Pods?</summary>
None
<br></details>

<details>
<summary>Taints are set on _____</summary>
nodes
<br></details>

<details>
<summary>Tolerations are set on _____</summary>
Pods
<br></details>

<details>
<summary>Do taints and tolerations guarantee which node a Pod will be scheduled to?</summary>
No - you need Node Affinity
<br></details>

<details>
<summary>Every node in a Kubernetes cluster runs a _____, responsible for implementing a form of virtual IP for Services of type other than ExternalName.</summary>
kube-proxy
<br></details>