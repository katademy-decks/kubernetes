# Node_Controller 

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

