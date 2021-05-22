<details>
	<summary>
		A container's available _____ options are Always, Never and IfNotPresent (default)

	</summary>
		ImagePullPolicy
</details>

<details>
	<summary>
		Containers run with unbounded compute resources on a Kubernetes cluster by default. To alleviate this, using Limits, LimitRanges and _____ is recommended.

	</summary>
		ResourceQuotas
</details>

<details>
	<summary>
		The _____ hook is executed before a container enters Terminated state.

	</summary>
		preStop
</details>

<details>
	<summary>
		When a process in a container tries to consume more than the allowed amount of memory, the system kernel terminates the process that attempted the allocation, with an _____ error

	</summary>
		OOM (Out of Memory)
</details>

<details>
	<summary>
		When a container's livenessProbe fails, the container is killed by the kubelet, then subjected to the container's _____ policy.

	</summary>
		restart
</details>

<details>
	<summary>
		If a Pod's _____Probe fails, the Pod's IP address is removed all Services that match the Pod.

	</summary>
		readiness
</details>

<details>
	<summary>
		To define default CPU/memory limit and requests for containers started with no CPU/memory settings in their specs, you could use _____.

	</summary>
		LimitRange
</details>

<details>
	<summary>
		The postStart hook is executed immediately after a Container is _____.

	</summary>
		Created
</details>

<details>
	<summary>
		A pod or container could monopolize all available resources in a cluster. A _____ API object constrains resource allocations to pods or containers in a namespace.

	</summary>
		LimitRange
</details>

<details>
	<summary>
		A _____Probe restarts your container when it's stuck, for example when it's running an infinite loop, where there is no way for the process to seek help externally, or even exit by itself.

	</summary>
		liveness
</details>

<details>
	<summary>
		Do ephemeral containers guarantee execution? _____

	</summary>
		No
</details>

<details>
	<summary>
		A container is in _____ state when it is pulling images, applying secrets, etc.

	</summary>
		Waiting
</details>

<details>
	<summary>
		If a container should only be sent traffic when a probe succeeds, the _____Probe can be used achieve this behaviour.

	</summary>
		readiness
</details>

<details>
	<summary>
		"A temporary ""_____"" container may be ran in an existing Pod to accomplish user-initiated actions such as troubleshooting and inspecting services."

	</summary>
		ephemeral
</details>

<details>
	<summary>
		A container's process is stuck, consuming 100% of its CPU and it won't reply to Readiness probes. If it doesn't have a _____, it will keep infinitely consuming resources, while serving no requests.

	</summary>
		livenessProbe
</details>

<details>
	<summary>
		To find why a container is in Terminated state, check its state's _____ and Exit Code fields.

	</summary>
		Reason
</details>

<details>
	<summary>
		A container's probes will not run until its _____Probe succeeds.

	</summary>
		startup
</details>

<details>
	<summary>
		Container probes result in Success if the container passed the diagnostic, Failure if it hasn't. If the diagnostic failed altogether, the probe's result is _____.

	</summary>
		Unknown
</details>

<details>
	<summary>
		Container probes result in Success if the container passed the diagnostic, _____ if it hasn't. If the diagnostic failed altogether, the probe's result is Unknown.

	</summary>
		Failure
</details>

<details>
	<summary>
		Is running database synchronisation a valid use case for a sidecar container inside a Pod? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Default requests/limits for containers can be set on a namespace via a _____

	</summary>
		LimitRange
</details>

<details>
	<summary>
		The preStop hook is executed before a container enters _____ state.

	</summary>
		Terminated
</details>

<details>
	<summary>
		A container's available ImagePullPolicy options are Always, Never and _____

	</summary>
		IfNotPresent (default)
</details>

<details>
	<summary>
		"Readiness gates are determined by the current state of a Pod's .status.conditions fields. If the field isn't found, the status of the condition defaults to ""_____"""

	</summary>
		False
</details>

<details>
	<summary>
		"The ""_____"" container inside each Pod reserves and holds the network namespace (netns), enabling containers to communicate with each other and retaining the Pod's IP address."

	</summary>
		pause
</details>

<details>
	<summary>
		The VerticalPodAutoscaler API Object adjusts the _____ of a container.

	</summary>
		resource requests and limits
</details>

<details>
	<summary>
		Does a Pod's restartPolicy apply to all its containers? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A container is in the Terminated state when it has _____.

	</summary>
		completed execution, with or without success
</details>

<details>
	<summary>
		Containers run with unbounded compute resources on a Kubernetes cluster by default. To alleviate this, using Limits, _____ and ResourceQuotas is recommended.

	</summary>
		LimitRanges
</details>

<details>
	<summary>
		A _____ is used for recovery when a Container's process is not responsive.

	</summary>
		livenessProbe
</details>

<details>
	<summary>
		When a container's _____Probe fails, the container is killed by the kubelet, then subjected to the container's restart policy.

	</summary>
		liveness
</details>

<details>
	<summary>
		If you don't set limits for a container, they may be inferred from the namespace's _____, if set.

	</summary>
		LimitRange
</details>

<details>
	<summary>
		"A container without a readinessProbe is considered ready for traffic once it starts. The problem with this is that _____"

	</summary>
		the application inside the container might need more time to start than its enclosing container. Requests sent to the container will fail, because the container was deemed ""Ready"" before the application actually started.
</details>

<details>
	<summary>
		A container's available ImagePullPolicy options are _____, Never and IfNotPresent (default)

	</summary>
		Always
</details>

<details>
	<summary>
		A process with one thread cannot consume more than _____ per second. The more threads, the less time it takes to consume it.

	</summary>
		1 CPU second
</details>

<details>
	<summary>
		To troubleshoot a Container's bug, inspect its state or run some arbitrary commands, you may execute an _____ Container inside the enclosing Pod, from which further commands can be ran.

	</summary>
		ephemeral
</details>

<details>
	<summary>
		When a process in a container tries to consume more than the allowed amount of memory, the system kernel _____ the process that attempted the allocation, with an OOM (Out of Memory) error

	</summary>
		terminates
</details>

<details>
	<summary>
		To find out why a container is in Waiting state, you can check its state's _____ field

	</summary>
		Reason
</details>

<details>
	<summary>
		If the node where a Pod is running has enough of a resource available, a container is allowed to use more resources than its resource _____.

	</summary>
		requests
</details>

<details>
	<summary>
		Containers run with unbounded compute resources on a Kubernetes cluster by default. To alleviate this, using _____, LimitRanges and ResourceQuotas is recommended.

	</summary>
		Limits
</details>

<details>
	<summary>
		A _____Probe indicates whether a container is ready to service requests.

	</summary>
		readiness
</details>

<details>
	<summary>
		If the startupProbe fails, the container is killed by the kubelet, then subjected to the container's _____ policy.

	</summary>
		restart
</details>

<details>
	<summary>
		The _____ hook is executed immediately after a Container is Created.

	</summary>
		postStart
</details>

<details>
	<summary>
		A container's available ImagePullPolicy options are Always, _____ and IfNotPresent (default)

	</summary>
		Never
</details>

<details>
	<summary>
		The _____ API Object adjusts the resource requests and limits of a container.

	</summary>
		VerticalPodAutoscaler
</details>

<details>
	<summary>
		Will an ephemeral container ever automatically restart? _____

	</summary>
		No
</details>

<details>
	<summary>
		A container's _____ field allows you to store credentials for a container image registry.

	</summary>
		imagePullSecrets
</details>

<details>
	<summary>
		Is running backups a valid use case for a sidecar container inside a Pod? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		When a container's livenessProbe fails, the container is _____ by the kubelet, then subjected to the container's restart policy.

	</summary>
		killed
</details>

<details>
	<summary>
		Container probes result in _____ if the container passed the diagnostic, Failure if it hasn't. If the diagnostic failed altogether, the probe's result is Unknown.

	</summary>
		Success
</details>

<details>
	<summary>
		A container has no livenessProbe, readinessProbe nor startupProbe. With this configuration, the result on each of these probes will be _____.

	</summary>
		Success!
</details>

<details>
	<summary>
		Do ephemeral containers have guaranteed resources? _____

	</summary>
		No
</details>

<details>
	<summary>
		A container is in the _____ state when it is executing without issues.

	</summary>
		Running
</details>

<details>
	<summary>
		When a container's livenessProbe and readinessProbe point to the same endpoint, the container will be detached from its Service and deleted at the same time. Is this fine? _____

	</summary>
		No - it will cause connection drops because the container is given no time to drain its current connections before being deleted.
</details>

<details>
	<summary>
		"Readiness gates are determined by the current state of a Pod's .status._____ fields. If the field isn't found, the status of the condition defaults to ""False"""

	</summary>
		conditions
</details>

<details>
	<summary>
		If the _____Probe fails, the container is killed by the kubelet, then subjected to the container's restart policy.

	</summary>
		startup
</details>

<details>
	<summary>
		Is running authentication proxies a valid use case for a sidecar container inside a Pod? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A container's _____Probe indicates whether the application in the container has started.

	</summary>
		startup
</details>

<details>
	<summary>
		To find why a container is in Terminated state, check its state's Reason and _____ fields.

	</summary>
		Exit Code
</details>

<details>
	<summary>
		Default _____ for containers can be set on a namespace via a LimitRange

	</summary>
		requests/limits
</details>

<details>
	<summary>
		Containers run with _____ compute resources on a Kubernetes cluster by default. To alleviate this, using Limits, LimitRanges and ResourceQuotas is recommended.

	</summary>
		unbounded
</details>

<details>
	<summary>
		A container is in the _____ state when it has completed execution, with or without success.

	</summary>
		Terminated
</details>

<details>
	<summary>
		A container is not allowed to use more than its resource _____.
	</summary>
		limits
</details>

