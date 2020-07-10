# Status 

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
Two types of node Heartbeats
</summary>
1. updates of *NodeStatus*<div>
2. The *Lease Object*</div>
</details>

