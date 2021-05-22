<details>
	<summary>
		Can you perform a rolling update on a DaemonSet? _____
	</summary>
		Yes
</details>

<details>
	<summary>
		A PodDisruptionBudget limits the number of Pods of a workload of that are allowed to be down simultaneously taken down from _____ disruptions.
	</summary>
		voluntary
</details>

<details>
	<summary>
		The possible values for a Pod's status condition field are _____, False or Unknown.
	</summary>
		True
</details>

<details>
	<summary>
		Pods in _____ state await to be scheduled onto the cluster by the Kubernetes Scheduler. An to this are Pods running as part of a DaemonSet, which are scheduled by the DaemonSet controller.
	</summary>
		Pending
</details>

<details>
	<summary>
		A Pod is in its lifecycle's _____ phase if its state could not be obtained, usually due to an error in communicating with its host.
	</summary>
		Unknown
</details>

<details>
	<summary>
		Pods running as part of a _____ have unique network identifiers, persistent storage, ordered deployment and scaling, and ordered rolling updates.
	</summary>
		StatefulSet
</details>

<details>
	<summary>
		The _____ API object is implemented as a control loop, with a sync period controlled by the kube-controller-manager's --horizontal-pod-autoscaler-sync-period flag.
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler API object is implemented as a control loop, with a sync period controlled by the _____'s --horizontal-pod-autoscaler-sync-period flag.
	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		Unlike a Deployment, a StatefulSet maintains a _____ for each of its Pods
	</summary>
		sticky identity
</details>

<details>
	<summary>
		If a Pod's metadata._____ does not link to a workload controller object (i.e. it is an orphanned Pod), it will be acquired by a controller whose selector matches the Pod, or the Pod will be garbage collected.
	</summary>
		OwnerReferences
</details>

<details>
	<summary>
		A Pod's _____ condition field provides a timestamp for when the Pod condition was last probed.
	</summary>
		lastProbeTime
</details>

<details>
	<summary>
		Containers are automatically co-located and co-scheduled on the same node when they are ran as part of a _____.
	</summary>
		Pod
</details>

<details>
	<summary>
		A _____ optimizes a given metric (e.g. CPU utilization) across a set of Pods, increasing or decreasing the number of replicas to achieve it.
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		If a Pod's metadata.OwnerReferences does not link to a workload controller object (i.e. it is an orphanned Pod), it will be acquired by a controller whose selector matches the Pod, or the Pod will be _____.
	</summary>
		garbage collected
</details>

<details>
	<summary>
		A _____ API Object scales the number of Pods in a Deployment, ReplicaSet or StatefulSet based on an observed metric (such as CPU utilization).
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		HorizontalPodAutoscaler API Objects do not apply to objects that can't be scaled, such as _____
	</summary>
		DaemonSets
</details>

<details>
	<summary>
		If non-preempting pods cannot be scheduled at a given time, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them. This is because non-preempting pods are subject to _____
	</summary>
		scheduler back-off
</details>

<details>
	<summary>
		The _____ condition field provides details about the transition from one status to another.
	</summary>
		Message
</details>

<details>
	<summary>
		A _____ injects bits of common configuration into all selected Pods at creation time. For example, you could use it to mount a particular Volume on all matching Pods.
	</summary>
		PodPreset
</details>

<details>
	<summary>
		A _____ load balances traffic across multiple Pods.
	</summary>
		Service
</details>

<details>
	<summary>
		A Pod is in its lifecycle's Failed phase if all its containers have terminated, at least one of which has exited with a _____ exit code, or was terminated by the system.
	</summary>
		non-zero (error)
</details>

<details>
	<summary>
		A _____ can be used to run a log collection daemon on every node.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		When node labels change, the DaemonSet controller will _____ Pods to newly matching nodes and delete Pods from newly not-matching nodes.
	</summary>
		add
</details>

<details>
	<summary>
		_____ is an object which can own ReplicaSets and update their Pods via declarative, server-side rolling updates.
	</summary>
		Deployment
</details>

<details>
	<summary>
		"In _____ cascading deletion, the root object enters a ""deletion in progress"" state. The garbage collector then deletes the object's dependents. Once they are gone, it deletes the owner object."
	</summary>
		foreground
</details>

<details>
	<summary>
		_____, ContainerReady, lastProbeTime, Reason are types of an Object's Conditions.
	</summary>
		Ready
</details>

<details>
	<summary>
		Containers within a single _____ share IP address and port space
	</summary>
		Pod
</details>

<details>
	<summary>
		When node labels change, the DaemonSet controller will add Pods to newly matching nodes and _____ Pods from newly not-matching nodes.
	</summary>
		delete
</details>

<details>
	<summary>
		The values of a Pod's type condition field may equal either PodScheduled, Ready, Initialized or _____
	</summary>
		ContainersReady
</details>

<details>
	<summary>
		A _____ is a global object that maps a priority class name to the integer value of the Priority.
	</summary>
		PriorityClass
</details>

<details>
	<summary>
		A _____ API Object injects additional runtime requirements into label-selected Pods at their creation time.
	</summary>
		PodPreset
</details>

<details>
	<summary>
		_____ cannot prevent involuntary Pod disruptions from occurring, and so they do not count against the budget.
	</summary>
		PodDisruptionBudgets
</details>

<details>
	<summary>
		If a Pod's metadata.OwnerReferences does not link to a workload controller object (i.e. it is an orphanned Pod), it will be acquired by a controller whose _____ matches the Pod, or the Pod will be garbage collected.
	</summary>
		selector
</details>

<details>
	<summary>
		The possible values for a Pod's status condition field are True, False or _____.
	</summary>
		Unknown
</details>

<details>
	<summary>
		The six fields of a PodCondition are reason, status, message, type, _____, lastTransitionTime.
	</summary>
		lastProbeTime
</details>

<details>
	<summary>
		In _____ cascading deletion, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents.
	</summary>
		background
</details>

<details>
	<summary>
		Minimum time in seconds for which a new pod should be ready to be considered available is defined in deployment.spec._____
	</summary>
		minReadySeconds
</details>

<details>
	<summary>
		Identical Pods in a workload are referred to as _____
	</summary>
		Replicas
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler adjusts the number of _____ of an application
	</summary>
		replicas
</details>

<details>
	<summary>
		A _____ runs one or more Containers.
	</summary>
		Pod
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler controller operates on the ratio between current and _____ metric values.
	</summary>
		desired
</details>

<details>
	<summary>
		"In foreground cascading deletion, the root object enters a ""deletion in progress"" state. The garbage collector then deletes the object's _____. Once they are gone, it deletes the owner object."
	</summary>
		dependents
</details>

<details>
	<summary>
		The number of old ReplicaSets retained for rollback purposes is defined in a Deployment's .spec._____ field.
	</summary>
		revisionHistoryLimit
</details>

<details>
	<summary>
		The _____ adjusts the number of replicas of an application
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		When a pod is evicted using the eviction API, is it gracefully terminated? _____
	</summary>
		Yes
</details>

<details>
	<summary>
		The count of hash collisions for a deployment is stored in its deployment.deploymentstatus._____ status field, and is used for collision avoidance.
	</summary>
		collisionCount
</details>

<details>
	<summary>
		Pods in Pending state await to be scheduled onto the cluster by the Kubernetes Scheduler. An to this are Pods running as part of a _____, which are scheduled by the _____ controller.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		The six fields of a PodCondition are reason, status, message, _____, lastProbeTime, lastTransitionTime.
	</summary>
		type
</details>

<details>
	<summary>
		_____ Pods can each be addressed by their uniquely identifiable, predictable DNS names. This is ideal for clustered or quorum-based applications, such as databases.
	</summary>
		StatefulSet
</details>

<details>
	<summary>
		While it's in its termination grace period, you might want an app to process remaining incoming requests by adding a _____ handler.
	</summary>
		preStop
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler API object is implemented as a control loop, with a sync period controlled by the kube-controller-manager's _____ flag.
	</summary>
		--horizontal-pod-autoscaler-sync-period
</details>

<details>
	<summary>
		Pods take an extra amount of a node's resources, additional to the resources taken by the Pod's containers. This is referred to as Pod Overhead and can be configured inside a _____ API object.
	</summary>
		RuntimeClass
</details>

<details>
	<summary>
		_____ within a single Pod share IP address and port space
	</summary>
		Containers
</details>

<details>
	<summary>
		Pod _____ repels Pods from each other. For example, an _____ to replicas of the same Pod on one Node can help spread your replicas evenly across the cluster.
	</summary>
		anti-affinity
</details>

<details>
	<summary>
		The role of the _____ is to delete objects that no longer have an owner.
	</summary>
		garbage collector
</details>

<details>
	<summary>
		_____ cannot be used to override a Pod’s own configuration, only fill in settings the Pod hasn't specified.
	</summary>
		PodPresets
</details>

<details>
	<summary>
		When deleting a DaemonSet with kubectl, you can specify the flag _____, then the Pods will remain on the nodes.
	</summary>
		--cascade=false
</details>

<details>
	<summary>
		A Deployment is set to keep 5 Pod replicas running at any given time, and a matching PodDisruptionBudget defines that there must always be 4 replicas running in any moment in time. Therefore, one Pod may be _____ disrupted by the Eviction API at a time.
	</summary>
		voluntarily
</details>

<details>
	<summary>
		The _____ controller ensures a specific number of pod replicas are running at any one time across nodes
	</summary>
		replication
</details>

<details>
	<summary>
		Each Kubernetes Node has its own _____ range from which it assigns its pods unique IPs.
	</summary>
		CIDR IP block
</details>

<details>
	<summary>
		A HorizontalPodAutoscaler API Object scales the number of Pods in a Deployment, ReplicaSet or StatefulSet based on _____.
	</summary>
		an observed metric (such as CPU utilization)
</details>

<details>
	<summary>
		PodDisruptionBudgets cannot prevent _____ Pod disruptions from occurring, and so they do not count against the budget.
	</summary>
		involuntary
</details>

<details>
	<summary>
		The _____ field indicates that the value of this PriorityClass should be used for Pods without a priorityClassName. Only one such PriorityClass can exist in the system.
	</summary>
		globalDefault
</details>

<details>
	<summary>
		The six fields of a PodCondition are _____, status, message, type, lastProbeTime, lastTransitionTime.
	</summary>
		reason
</details>

<details>
	<summary>
		Pods running as part of a _____ are a set of stateless replicas deployed in random order and given no stable identifiers.
	</summary>
		Deployment
</details>

<details>
	<summary>
		The six fields of a PodCondition are reason, _____, message, type, lastProbeTime, lastTransitionTime.
	</summary>
		status
</details>

<details>
	<summary>
		A Pod is in its lifecycle's _____ phase when the Pod has been bound to a Node, all of its Containers have been created and at least one Container is either running, in the process of starting, or restarting.
	</summary>
		Running
</details>

<details>
	<summary>
		Pods with _____ will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. It will stay in the scheduling queue, until sufficient resources are free.
	</summary>
		PreemptionPolicy: Never
</details>

<details>
	<summary>
		The six fields of a PodCondition are reason, status, _____, type, lastProbeTime, lastTransitionTime.
	</summary>
		message
</details>

<details>
	<summary>
		If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.
	</summary>
		Priority
</details>

<details>
	<summary>
		To control the cascading deletion policy, set the _____ field on the deleteOptions argument when deleting an Object.
	</summary>
		propagationPolicy
</details>

<details>
	<summary>
		A Pod is in its lifecycle's _____ phase if all its containers have terminated, at least one of which has exited with a non-zero (error) exit code, or was terminated by the system.
	</summary>
		Failed
</details>

<details>
	<summary>
		A Pod's _____ condition field provides a unique reason for the condition's last transition.
	</summary>
		reason
</details>

<details>
	<summary>
		A _____ allows templating Pod configuration across many Pods.
	</summary>
		PodPreset
</details>

<details>
	<summary>
		The role of the garbage collector is to delete objects that no longer have an _____.
	</summary>
		owner
</details>

<details>
	<summary>
		The values of a Pod's type condition field may equal either _____, Ready, Initialized or ContainersReady
	</summary>
		PodScheduled
</details>

<details>
	<summary>
		A Kubernetes resource which ensures that all matching Nodes run a copy of a Pod is the _____
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		When Exited Containers are restarted by the kubelet, they are restarted with an _____ delay capped at 5 minutes, reset after ten minutes of successful execution.
	</summary>
		exponential back-off
</details>

<details>
	<summary>
		A logical group of containers with shared network and storage and specifications for how to run each container is called a _____
	</summary>
		Pod
</details>

<details>
	<summary>
		When you delete an object, you can specify whether the object's dependents are also deleted. This is referred to as a _____ deletion.
	</summary>
		cascading
</details>

<details>
	<summary>
		A Deployment is set to keep 5 Pod replicas running at any given time, and a matching _____ defines that there must always be 4 replicas running in any moment in time. Therefore, one Pod may be voluntarily disrupted by the Eviction API at a time.
	</summary>
		PodDisruptionBudget
</details>

<details>
	<summary>
		Workload controllers like deployment or statefulset are not limited by PodDisruptionBudgets when doing rolling updates, because the handling of failures during application updates is configured in the _____.
	</summary>
		controller's spec
</details>

<details>
	<summary>
		"In foreground cascading deletion, the root object enters a ""deletion in progress"" state. The garbage collector then deletes the object's dependents. Once they are gone, it deletes _____."
	</summary>
		the owner object
</details>

<details>
	<summary>
		If you want to use storage volumes to provide persistence for your workload, you can use a _____. The persistent identity of its Pods allows for matching of existing volumes to any new Pods that replace those Pods that fail in the future.
	</summary>
		StatefulSet
</details>

<details>
	<summary>
		A Pod can have an IPv4 and IPv6 address assigned via enabling _____.
	</summary>
		IPv4/IPv6 dual-stack
</details>

<details>
	<summary>
		If a _____'s current metric value per replica is 200m, and the desired metric value per replica is 100m, the number of replicas will be doubled.
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		The values of a Pod's type condition field may equal either PodScheduled, Ready, _____ or ContainersReady
	</summary>
		Initialized
</details>

<details>
	<summary>
		Label _____ specify the Pods to which a given PodPreset applies.
	</summary>
		selectors
</details>

<details>
	<summary>
		A Pod is in its lifecycle's _____ phase when it has been applied to Kubernetes' desired state, but at least one of its Container images has not yet been created, either because the Pod is still being scheduled or is downloading images.
	</summary>
		Pending
</details>

<details>
	<summary>
		A Pod is in its lifecycle's _____ phase when its containers have terminated in success, and will not be restarted.
	</summary>
		Succeeded
</details>

<details>
	<summary>
		Critical Pods can be set to rely on scheduler _____ to be scheduled at the cost of less critical Pods when a cluster is under resource pressure.
	</summary>
		preemption
</details>

<details>
	<summary>
		The possible values for a Pod's status condition field are True, _____ or Unknown.
	</summary>
		False
</details>

<details>
	<summary>
		Containers within a _____ share storage and network resources.
	</summary>
		Pod
</details>

<details>
	<summary>
		Once bound to a node, will a Pod ever rebound to another node? _____
	</summary>
		No
</details>

<details>
	<summary>
		An Object's _____ are latest variable observations of its state, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.
	</summary>
		Conditions
</details>

<details>
	<summary>
		If a deleted Object's dependents were not deleted automatically with their owner, they are considered _____.
	</summary>
		orphaned
</details>

<details>
	<summary>
		The six fields of a PodCondition are reason, status, message, type, lastProbeTime, _____.
	</summary>
		lastTransitionTime
</details>

<details>
	<summary>
		When deleting a _____ with kubectl, you can specify the flag --cascade=false, then the Pods will remain on the nodes.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		A quorum-based application must ensure that the number of running replicas is never brought below the minimum required for a quorum. This can be achieved with a _____
	</summary>
		PodDisruptionBudget
</details>

<details>
	<summary>
		A _____ limits the number of Pods of a workload of that are allowed to be down simultaneously taken down from voluntary disruptions.
	</summary>
		PodDisruptionBudget
</details>

<details>
	<summary>
		_____ indicates the importance of a Pod to be scheduled onto the cluster, relative to other Pods.
	</summary>
		Priority
</details>

<details>
	<summary>
		Pod Priority and Pod Pre-emption are ignored by Pods scheduled by the _____ controller.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		A Deployment is set to keep 5 Pod replicas running at any given time, and a matching PodDisruptionBudget defines that there must always be 4 replicas running in any moment in time. Therefore, _____ Pod may be voluntarily disrupted by the Eviction API at a time.
	</summary>
		one
</details>

<details>
	<summary>
		A ReplicaSet is linked to its Pods via their metadata._____ field, which allow the ReplicaSet to find the state of its Pods.
	</summary>
		ownerReferences
</details>

<details>
	<summary>
		A _____ specifies the minimum number of replicas that an application needs running at any given time to work properly.
	</summary>
		PodDisruptionBudget
</details>

<details>
	<summary>
		StatefulSets do not provide any guarantees on the termination of its pods when a StatefulSet is deleted. To achieve ordered and graceful termination you must _____ before deleting it.
	</summary>
		scale the StatefulSet down to 0
</details>

<details>
	<summary>
		Pods take an extra amount of a node's resources, additional to the resources taken by the Pod's containers. This is referred to as _____ and can be configured inside a RuntimeClass API object.
	</summary>
		Pod Overhead
</details>

<details>
	<summary>
		Normally, Pods are scheduled onto nodes by the Kubernetes scheduler -- except _____ Pods which are created and scheduled by their own workload controller.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		A HorizontalPodAutoscaler optimizes a given metric (e.g. CPU utilization) across a set of Pods, increasing or decreasing the number of _____ to achieve it.
	</summary>
		replicas
</details>

<details>
	<summary>
		Pods running as part of a Deployment are a set of stateless replicas deployed in _____ order and given no stable identifiers.
	</summary>
		random
</details>

<details>
	<summary>
		_____ API Objects do not apply to objects that can't be scaled, such as DaemonSets
	</summary>
		HorizontalPodAutoscaler
</details>

<details>
	<summary>
		A Pod's _____ condition field provides a timestamp for it has last transitioned from one status to another.
	</summary>
		lastTransitionTime
</details>

<details>
	<summary>
		A Pod runs one or more _____.
	</summary>
		Containers
</details>

<details>
	<summary>
		Unlike a Deployment, a _____ maintains a sticky identity for each of its Pods
	</summary>
		StatefulSet
</details>

<details>
	<summary>
		Normally, Pods are scheduled onto nodes by the Kubernetes _____ -- except DaemonSet Pods which are created and scheduled by their own workload controller.
	</summary>
		scheduler
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler API object is implemented as a _____, with a sync period controlled by the kube-controller-manager's --horizontal-pod-autoscaler-sync-period flag.
	</summary>
		control loop
</details>

<details>
	<summary>
		Pods in Pending state await to be scheduled onto the cluster by the Kubernetes Scheduler. An to this are Pods running as part of a _____, which are scheduled by the _____ controller.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		Pod _____ repels Pods from each other. For example, an _____ to replicas of the same Pod on one Node can help spread your replicas evenly across the cluster.
	</summary>
		anti-affinity
</details>

<details>
	<summary>
		The HorizontalPodAutoscaler controller operates on the ratio between _____ and desired metric values.
	</summary>
		current
</details>

<details>
	<summary>
		If a HorizontalPodAutoscaler's current metric value per replica is 200m, and the desired metric value per replica is 100m, the number of replicas will be _____.
	</summary>
		doubled
</details>

<details>
	<summary>
		A _____ can run a monitoring daemon on every node.
	</summary>
		DaemonSet
</details>

<details>
	<summary>
		Pod anti-affinity repels Pods from each other. For example, an anti-affinity to replicas of the same Pod on one _____ can help spread your replicas evenly across the cluster.
	</summary>
		Node
</details>

<details>
	<summary>
		The values of a Pod's type condition field may equal either PodScheduled, _____, Initialized or ContainersReady
	</summary>
		Ready
</details>

<details>
	<summary>
		A PodPreset API Object injects additional runtime requirements into label-selected _____ at their creation time.
	</summary>
		Pods
</details>

<details>
	<summary>
		PreemptionPolicy defaults to _____, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).
	</summary>
		PreemptLowerPriority
</details>

<details>
	<summary>
		The _____ controller provides a time-to-live mechanism which limits the lifetime of workload objects that have finished execution.
	</summary>
		TTL
</details>

<details>
	<summary>
		_____ start and stop Pod replicas in a specific order.
	</summary>
		StatefulSets
</details>

<details>
	<summary>
		A Pod's _____ represents where the Pod is in its lifecycle.
	</summary>
		phase
</details>

