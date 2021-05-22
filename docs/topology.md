<details>
	<summary>
		If two Nodes are labelled with one _____ and have identical values for that label, the scheduler tries to place a balanced number of Pods into each topology domain
	</summary>
		topologyKey
</details>

<details>
	<summary>
		Endpoints in an EndpointSlice can contain labels about the slice's topology information, such as the topological Node, Zone or _____.
	</summary>
		Region
</details>

<details>
	<summary>
		You can control Service traffic routing by specifying the .spec._____ field.
	</summary>
		topologyKeys
</details>

<details>
	<summary>
		A Service's .spec.topologyKeys field is a preference-order list of _____ labels by which the Service's Endpoints are sorted when accessing it. Traffic is directed to a _____ whose first label matches the originating Node's label value. If no backend for the Service exists on a matching _____, then the second label is evaluated, and so forth.
	</summary>
		Node
</details>

<details>
	<summary>
		Topology spread constraints rely on node _____ to identify the topology domains each Node belongs to.
	</summary>
		labels
</details>

<details>
	<summary>
		A Service's .spec.topologyKeys field is a preference-order list of Node labels by which the Service's Endpoints are sorted when accessing it. Traffic is directed to a Node whose first label matches the originating _____ label value. If no backend for the Service exists on a matching Node, then the second label is evaluated, and so forth.
	</summary>
		Node's
</details>

<details>
	<summary>
		Endpoints in an EndpointSlice can contain labels about the slice's topology information, such as the topological _____, Zone or Region.
	</summary>
		Node
</details>

<details>
	<summary>
		If a Pod doesn't satisfy its topologySpreadConstraints, the spec.topologySpreadConstraints._____ field defines how to deal with it. The possible values are: DoNotSchedule (the Pod should not be scheduled by the Kubernetes scheduler) or ScheduleAnyway (the Pod is allowed to be scheduled, prioritizing nodes in a way that minimizes skew)
	</summary>
		whenUnsatisfiable
</details>

<details>
	<summary>
		A Service's .spec.topologyKeys field is a preference-order list of _____ labels by which the Service's Endpoints are sorted when accessing it. Traffic is directed to a _____ whose first label matches the originating Node's label value. If no backend for the Service exists on a matching _____, then the second label is evaluated, and so forth.
	</summary>
		Node
</details>

<details>
	<summary>
		_____ defines the degree to which Pods may be unevenly distributed across topology domains. It represents the maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type.
	</summary>
		maxSkew
</details>

<details>
	<summary>
		_____ enables a service to route traffic based on the Node topology of the cluster.
	</summary>
		Service Topology
</details>

<details>
	<summary>
		You can use _____ to control how Pods are spread across your cluster among failure-domains (regions, zones, nodes or user-defined domains).
	</summary>
		topology spread constraints
</details>

<details>
	<summary>
		A Service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone by using _____
	</summary>
		Service Topology
</details>

<details>
	<summary>
		If a Pod doesn't satisfy its topologySpreadConstraints, the spec._____.whenUnsatisfiable field defines how to deal with it. The possible values are: DoNotSchedule (the Pod should not be scheduled by the Kubernetes scheduler) or ScheduleAnyway (the Pod is allowed to be scheduled, prioritizing nodes in a way that minimizes skew)
	</summary>
		topologySpreadConstraints
</details>

<details>
	<summary>
		If a Pod doesn't satisfy its topologySpreadConstraints, the spec.topologySpreadConstraints.whenUnsatisfiable field defines how to deal with it. The possible values are: _____ or ScheduleAnyway (the Pod is allowed to be scheduled, prioritizing nodes in a way that minimizes skew)
	</summary>
		DoNotSchedule (the Pod should not be scheduled by the Kubernetes scheduler)
</details>

<details>
	<summary>
		Two Nodes labelled with an identical topologyKey and value, are treated by the _____ as belonging to the same topology.
	</summary>
		scheduler
</details>

<details>
	<summary>
		A Service's .spec.topologyKeys field is a preference-order list of _____ labels by which the Service's Endpoints are sorted when accessing it. Traffic is directed to a _____ whose first label matches the originating Node's label value. If no backend for the Service exists on a matching _____, then the second label is evaluated, and so forth.
	</summary>
		Node
</details>

<details>
	<summary>
		If two Nodes are labelled with one topologyKey and have identical values for that label, the scheduler tries to place a balanced number of Pods into each _____
	</summary>
		topology domain
</details>

<details>
	<summary>
		Two Nodes labelled with an identical _____ and value, are treated by the scheduler as belonging to the same topology.
	</summary>
		topologyKey
</details>

<details>
	<summary>
		Endpoints in an EndpointSlice can contain labels about the slice's topology information, such as the topological Node, _____ or Region.
	</summary>
		Zone
</details>

<details>
	<summary>
		A Service's .spec._____ field is a preference-order list of Node labels by which the Service's Endpoints are sorted when accessing it. Traffic is directed to a Node whose first label matches the originating Node's label value. If no backend for the Service exists on a matching Node, then the second label is evaluated, and so forth.
	</summary>
		topologyKeys
</details>

<details>
	<summary>
		Two Nodes labelled with an identical topologyKey and value, are treated by the scheduler as belonging to the same _____.
	</summary>
		topology
</details>

<details>
	<summary>
		If a Pod doesn't satisfy its topologySpreadConstraints, the spec.topologySpreadConstraints.whenUnsatisfiable field defines how to deal with it. The possible values are: DoNotSchedule (the Pod should not be scheduled by the Kubernetes scheduler) or _____
	</summary>
		ScheduleAnyway (the Pod is allowed to be scheduled, prioritizing nodes in a way that minimizes skew)
</details>

