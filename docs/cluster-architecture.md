<details>
	<summary>
		An object's metadata._____ status field denotes its parent object. If empty, the child object will be garbage collected and removed.
	</summary>
		ownerReference
</details>

<details>
	<summary>
		A _____ API object stores confidential key-value pairs. Pods can consume them as environment variables, command-line arguments, or mount them as volumes.
	</summary>
		Secret
</details>

<details>
	<summary>
		_____ are key-value pairs that identify resources, and can be matched by the Selectors of other resources.
	</summary>
		Labels
</details>

<details>
	<summary>
		In clusters that mount tens of thousands unique Secrets/ConfigMaps to Pods or more, Secrets and Configmaps can be configured as _____ to significantly increase performance, as kube-apiserver will no longer watch for secrets or config maps.
	</summary>
		immutable
</details>

<details>
	<summary>
		An API Object's _____.finalizers field holds a list of strings, all of which must be explicitly removed before the object can be deleted from the cluster.
	</summary>
		metadata
</details>

<details>
	<summary>
		_____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.
	</summary>
		cloud-controller-manager
</details>

<details>
	<summary>
		In Kubernetes request/limit terms, 1 CPU equals _____ on bare-metal Intel processors.
	</summary>
		1 hyperthread
</details>

<details>
	<summary>
		A custom resource  is _____.
	</summary>
		an extension of the Kubernetes API
</details>

<details>
	<summary>
		If the data you want to store are confidential, use a _____ rather than a ConfigMap.
	</summary>
		Secret
</details>

<details>
	<summary>
		An object's _____.ownerReference status field denotes its parent object. If empty, the child object will be garbage collected and removed.
	</summary>
		metadata
</details>

<details>
	<summary>
		A ResourceQuota may constraint aspects of a _____ such as maximum resource consumption or maximum allowed number of Objects of a specific Kind.
	</summary>
		namespace
</details>

<details>
	<summary>
		A ConfigMap API object stores non-confidential key-value pairs. Pods can consume them as environment variables, command-line arguments, or as _____.
	</summary>
		volumes
</details>

<details>
	<summary>
		_____ allow you to create your own custom Kubernetes objects, to store any data you wish.
	</summary>
		CustomResourceDefinitions (CRDs)
</details>

<details>
	<summary>
		A Secret API object stores confidential key-value pairs. Pods can consume them as _____, command-line arguments, or mount them as volumes.
	</summary>
		environment variables
</details>

<details>
	<summary>
		An API Object's metadata.finalizers field holds a list of strings, all of which must be explicitly removed before the object can be _____ from the cluster.
	</summary>
		deleted
</details>

<details>
	<summary>
		A ConfigMap API object stores non-confidential key-value pairs. Pods can consume them as environment variables, _____, or as volumes.
	</summary>
		command-line arguments
</details>

<details>
	<summary>
		A Secret API object stores confidential key-value pairs. Pods can consume them as environment variables, command-line arguments, or mount them as _____.
	</summary>
		volumes
</details>

<details>
	<summary>
		A Secret API object stores confidential key-value pairs. Pods can consume them as environment variables, _____, or mount them as volumes.
	</summary>
		command-line arguments
</details>

<details>
	<summary>
		An object's metadata.ownerReference status field denotes its parent object. If empty, the child object will be _____.
	</summary>
		garbage collected and removed
</details>

<details>
	<summary>
		A _____ API object is set per namespace
	</summary>
		LimitRange
</details>

<details>
	<summary>
		_____ are key/value pairs you may write in the metadata of objects.
	</summary>
		Labels
</details>

<details>
	<summary>
		The _____ namespace holds the public data of a Kubernetes cluster.
	</summary>
		kube-public
</details>

<details>
	<summary>
		A LimitRange API object is set per _____
	</summary>
		namespace
</details>

<details>
	<summary>
		A _____ is an extension of the Kubernetes API.
	</summary>
		custom resource
</details>

<details>
	<summary>
		ConfigMaps are mounted to a Pod via its .spec._____ field
	</summary>
		volumes
</details>

<details>
	<summary>
		A LimitRange API Object can enforce a ratio between requests and limits for _____ in a namespace.
	</summary>
		containers
</details>

<details>
	<summary>
		A _____ can enforce minimum and maximum resource usage per Pod or Container in a namespace.
	</summary>
		LimitRange
</details>

<details>
	<summary>
		A LimitRange API Object can enforce a ratio between requests and _____ for containers in a namespace.
	</summary>
		limits
</details>

<details>
	<summary>
		metrics-server provides metrics via the resource metrics API, used by _____s to collect metrics.
	</summary>
		Horizontal Pod Autoscaler
</details>

<details>
	<summary>
		A _____ API object stores non-confidential key-value pairs. Pods can consume them as environment variables, command-line arguments, or as volumes.
	</summary>
		ConfigMap
</details>

<details>
	<summary>
		You can enforce minimum and maximum storage request per PersistentVolumeClaim in a namespace using a _____
	</summary>
		LimitRange
</details>

<details>
	<summary>
		A _____ API Object can enforce a ratio between requests and limits for containers in a namespace.
	</summary>
		LimitRange
</details>

<details>
	<summary>
		A _____ may constraint aspects of a namespace such as maximum resource consumption or maximum allowed number of Objects of a specific Kind.
	</summary>
		ResourceQuota
</details>

<details>
	<summary>
		When a ConfigMap is updated, the projected keys inside the Pod which mount the ConfigMap are _____. The kubelet periodically checks that every mounted ConfigMap is fresh, though it also uses its own local configurable cache for getting the current value of the ConfigMap.
	</summary>
		eventually updated
</details>

<details>
	<summary>
		When teams share a cluster with limited resources, one team could use more than its fair share. _____ objects address this concern.
	</summary>
		ResorceQuota
</details>

<details>
	<summary>
		metrics-server provides metrics via the _____ API, used by Horizontal Pod Autoscalers to collect metrics.
	</summary>
		resource metrics
</details>

<details>
	<summary>
		A ConfigMap API object stores non-confidential key-value pairs. Pods can consume them as _____, command-line arguments, or as volumes.
	</summary>
		environment variables
</details>

<details>
	<summary>
		Labels are key-value pairs that identify resources, and can be matched by the _____ of other resources.
	</summary>
		Selectors
</details>

<details>
	<summary>
		_____ provides metrics via the resource metrics API, used by Horizontal Pod Autoscalers to collect metrics.
	</summary>
		metrics-server
</details>

<details>
	<summary>
		If too many Pods run with high priority, lower priority Pods may start being _____.
	</summary>
		evicted or unschedulable
</details>

<details>
	<summary>
		The _____ namespace holds Kubernetes system processes.
	</summary>
		kube-system
</details>

<details>
	<summary>
		Labels are key/value pairs you may write in the _____ of objects.
	</summary>
		metadata
</details>

<details>
	<summary>
		The _____ daemon embeds the core control loops of Kubernetes.
	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		When a ConfigMap is updated, the projected keys inside the Pod which mount the ConfigMap are eventually updated. The _____ periodically checks that every mounted ConfigMap is fresh, though it also uses its own local configurable cache for getting the current value of the ConfigMap.
	</summary>
		kubelet
</details>

<details>
	<summary>
		A LimitRange API Object can enforce a ratio between requests and limits for containers in a _____.
	</summary>
		namespace
</details>

<details>
	<summary>
		An API Object's metadata._____ field holds a list of strings, all of which must be explicitly removed before the object can be deleted from the cluster.
	</summary>
		finalizers
</details>

<details>
	<summary>
		In Kubernetes request/limit terms, _____ equals 1 hyperthread on bare-metal Intel processors.
	</summary>
		1 CPU
</details>

<details>
	<summary>
		A LimitRange API Object can enforce a ratio between _____ and limits for containers in a namespace.
	</summary>
		requests
</details>

