<details>
	<summary>
		A Node's _____ condition is True when its network is not correctly configured
	</summary>
		NetworkUnavailable
</details>

<details>
	<summary>
		Addresses in a node's status include _____, InternalIP, ExternalIP
	</summary>
		HostName
</details>

<details>
	<summary>
		Addresses in a node's status include HostName, _____, ExternalIP
	</summary>
		InternalIP
</details>

<details>
	<summary>
		A node's DiskPressure condition is _____ when its disk capacity is low
	</summary>
		True
</details>

<details>
	<summary>
		A Node's heartbeats are sent by its _____.
	</summary>
		kubelet
</details>

<details>
	<summary>
		The _____ master components manages Node Health, assigns CIDR and updates a node's internal list of nodes.
	</summary>
		Node Controller
</details>

<details>
	<summary>
		When a node is reachable by kube-apiserver, but its Ready condition has remained False or Unknown for longer than the kube-controller-manager's pod-eviction-timeout, all Pods on the node are scheduled for deletion by the _____ controller
	</summary>
		node
</details>

<details>
	<summary>
		The _____ assigns a Node's a CIDR block, synchronizes its internal list of other Nodes, and monitors its health.
	</summary>
		Node Controller
</details>

<details>
	<summary>
		Worker node Kubernetes components (_____ and kube-proxy) communicate with Master node components, specifically kube-apiserver.
	</summary>
		kubelet
</details>

<details>
	<summary>
		A Node's _____ condition is True when the node's memory is low
	</summary>
		MemoryPressure
</details>

<details>
	<summary>
		A Node's PIDPressure condition is _____ when there are too many processes running.
	</summary>
		True
</details>

<details>
	<summary>
		_____ node affinities can block a Pod from running on a node. Soft node affinities are suggestions to the scheduler. Both can be combined, and have multiple weights.
	</summary>
		Hard
</details>

<details>
	<summary>
		A taint's possible effects are PreferNoSchedule, NoSchedule, _____
	</summary>
		NoExecute
</details>

<details>
	<summary>
		The Kubernetes Master node runs kube-apiserver, _____, kube-controller-manager.
	</summary>
		scheduler
</details>

<details>
	<summary>
		The two types of Node Heartbeats are _____ and the Lease Object
	</summary>
		NodeStatus updates
</details>

<details>
	<summary>
		_____ allow a node to repel a set of Pods, based on certain properties of the node.
	</summary>
		Taints
</details>

<details>
	<summary>
		When a node is reachable by kube-apiserver, but its Ready condition has remained False or Unknown for longer than the _____'s pod-eviction-timeout, all Pods on the node are scheduled for deletion by the node controller
	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		"A node is in ""_____"" status when it is healthy and accepts pods."
	</summary>
		Ready
</details>

<details>
	<summary>
		Node heartbeats are stored inside the _____ namespace.
	</summary>
		kube-node-lease
</details>

<details>
	<summary>
		Taints are set on _____. Tolerations are set on Pods.
	</summary>
		Nodes
</details>

<details>
	<summary>
		A taint's possible effects are _____, NoSchedule, NoExecute
	</summary>
		PreferNoSchedule
</details>

<details>
	<summary>
		A node's status contains information about its Addresses, Conditions, _____ and Info.
	</summary>
		Capacity/Allocatable
</details>

<details>
	<summary>
		A Node's self-registration into the control plane is done by its _____.
	</summary>
		kubelet
</details>

<details>
	<summary>
		A _____ is a physical or virtual machine running Kubernetes workloads.
	</summary>
		Node
</details>

<details>
	<summary>
		Worker node Kubernetes components (kubelet and kube-proxy) communicate with Master node components, specifically _____.
	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		A Node's MemoryPressure condition is _____ when the node's memory is low
	</summary>
		True
</details>

<details>
	<summary>
		A node's _____ condition is True when its disk capacity is low
	</summary>
		DiskPressure
</details>

<details>
	<summary>
		A node's status contains information about its _____, Conditions, Capacity/Allocatable and Info.
	</summary>
		Addresses
</details>

<details>
	<summary>
		"A Node's ""Ready"" status is Unknown when 40 seconds have passed since _____ has heard from the node."
	</summary>
		the Node Controller
</details>

<details>
	<summary>
		Pod _____ express a preference for Pods to be scheduled on the same node as a specific group of other Pods.
	</summary>
		affinities
</details>

<details>
	<summary>
		"A Node's ""Ready"" status is _____ when it's unhealthy and not accepting pods."
	</summary>
		False
</details>

<details>
	<summary>
		Node _____ attract Pods to nodes or repel Pods from nodes using specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.
	</summary>
		affinities
</details>

<details>
	<summary>
		The _____ watches for unschedulable pods and tries to consolidate currently deployed pods on a smaller number of nodes.
	</summary>
		cluster autoscaler
</details>

<details>
	<summary>
		A Node's _____ inform an incoming packet where in the node it should go to.
	</summary>
		iptables
</details>

<details>
	<summary>
		A node's status contains information about its Addresses, Conditions, Capacity/Allocatable and _____.
	</summary>
		Info
</details>

<details>
	<summary>
		The two types of Node Heartbeats are NodeStatus updates and _____
	</summary>
		the Lease Object
</details>

<details>
	<summary>
		A node's _____ describes the amount of resources available to be consumed by Pods.
	</summary>
		Allocatable
</details>

<details>
	<summary>
		A Pod won’t be scheduled on a Node that has a Taint defined, unless the Pod has a matching _____ defined.
	</summary>
		Toleration
</details>

<details>
	<summary>
		When a node is reachable by kube-apiserver, but its Ready condition has remained False or Unknown for longer than the kube-controller-manager's _____-timeout, all Pods on the node are scheduled for deletion by the node controller
	</summary>
		pod-eviction
</details>

<details>
	<summary>
		_____ allow a Pod to be scheduled on nodes with a specific taint. You can use them to run certain Pods only on dedicated nodes.
	</summary>
		Tolerations
</details>

<details>
	<summary>
		A node's status contains information about its Addresses, _____, Capacity/Allocatable and Info.
	</summary>
		Conditions
</details>

<details>
	<summary>
		Taints are set on Nodes. Tolerations are set on _____.
	</summary>
		Pods
</details>

<details>
	<summary>
		A Node's NetworkUnavailable condition is _____ when its network is not correctly configured
	</summary>
		True
</details>

<details>
	<summary>
		A Node's _____ status field describes general information about it, such as operating system and node component versions
	</summary>
		Info
</details>

<details>
	<summary>
		Addresses in a node's status include HostName, InternalIP, _____
	</summary>
		ExternalIP
</details>

<details>
	<summary>
		It's important to place your Pods across several _____ to ensure fault tolerance, as one of them may fail.
	</summary>
		nodes
</details>

<details>
	<summary>
		A Node's _____ condition is True when there are too many processes running.
	</summary>
		PIDPressure
</details>

<details>
	<summary>
		The Kubernetes Master node runs _____, scheduler, kube-controller-manager.
	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		The _____ node runs kube-apiserver, scheduler, kube-controller-manager.
	</summary>
		Kubernetes Master
</details>

<details>
	<summary>
		A Pod won’t be scheduled on a Node that has a _____ defined, unless the Pod has a matching Toleration defined.
	</summary>
		Taint
</details>

<details>
	<summary>
		Hard node affinities can block a Pod from running on a node. _____ node affinities are suggestions to the scheduler. Both can be combined, and have multiple weights.
	</summary>
		Soft
</details>

<details>
	<summary>
		Worker node Kubernetes components (kubelet and _____) communicate with Master node components, specifically kube-apiserver.
	</summary>
		kube-proxy
</details>

<details>
	<summary>
		The cluster autoscaler watches for unschedulable pods and tries to consolidate currently deployed pods on a smaller number of _____.
	</summary>
		nodes
</details>

<details>
	<summary>
		The Kubernetes Master node runs kube-apiserver, scheduler, _____.
	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		A taint's possible effects are PreferNoSchedule, _____, NoExecute
	</summary>
		NoSchedule
</details>

<details>
	<summary>
		"A Node's ""Ready"" status is _____ when 40 seconds have passed since the Node Controller has heard from the node."
	</summary>
		Unknown
</details>

<details>
	<summary>
		The Cluster Autoscaler adjusts the number of _____ of a cluster.
	</summary>
		nodes
</details>

<details>
	<summary>
		You can prevent a kubelet from self-registering the node in the control-plane with the _____ flag.
	</summary>
		--register-node=false
</details>

<details>
	<summary>
		The cluster autoscaler watches for _____ pods and tries to consolidate currently deployed pods on a smaller number of nodes.
	</summary>
		unschedulable
</details>

