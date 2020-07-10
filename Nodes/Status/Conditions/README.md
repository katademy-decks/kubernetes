# Conditions 

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

