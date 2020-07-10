# Node_Controller 

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

