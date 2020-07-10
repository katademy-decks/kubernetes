# Status 

<details>
<summary>
<b>A node's status containts four domains of information.>These are...</b>
</summary>
Addresses>
>Conditions>
>Capacity and Allocatable>
>Info
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
>ExternalIP
>
>InternalIP>
>HostName
</details>

<details>
<summary>
<b>HostName</b>
</summary>
The hostname reported by the node's kernel>
>Can be overridden via <b>--hostname-override</b>
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
OS Name>
>kubelet, kube-proxy, docker versions
</details>

<details>
<summary>
<b>Ready</b>
</summary>
<b>True</b>>if the node is healthy and ready to accept pods><b>
</b>><b>False</b>>if the node us unhealthy and is not accepting pods><b>
</b>><b>Unknown</b>>If the node controller has not heard from the node in the last 40 seconds
</details>

<details>
<summary>
<b>DiskPressure</b>
</summary>
<b>True</b>>if the node's disk capacity is low
</details>

<details>
<summary>
<b>MemoryPressure</b>
</summary>
<b>True</b>>if the node's memory is low
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
<b>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b>>
>What happens to the Pods on the node?</b>
</summary>
All Pods on the node are scheduled for deletion by the node controller
</details>

<details>
<summary>
<b>Capacity</b>
</summary>
>Capacity fields describe the total amount of resources that a Node has
</details>

<details>
<summary>
<b>Allocatable</b>
</summary>
Describes the amount of the Node's resources that are available to be consumed by Pods
</details>

<details>
<summary>
<b>Two types of node Heartbeats</b>
</summary>
1. updates of <b>NodeStatus</b>>
2. The <b>Lease Object</b>
</details>

