<details>
<summary>When you run a Pod on a Node, the Pod itself takes an amount of system resources. These resources are additional to the resources needed to run the container(s) inside the Pod.&nbsp;<i>_____&nbsp;</i>is a feature for accounting for the resources consumed by the Pod infrastructure on top of the container requests &amp; limits.</summary>
Pod Overhead
<br></details>

<details>
<summary>Can a Pod have a single IPv4 and IPv6 address assigned?</summary>
Yes - via enabling IPv4/IPv6 dual-stack.
<br></details>

<details>
<summary>Pod Overhead is set at _____&nbsp;time according to the overhead associated with the Pod's _____. When enabled, it is considered in addition to the sum of container resource requests when scheduling a Pod. Similarly, Kubelet will include the Pod overhead when sizing the Pod cgroup, and when carrying out Pod eviction ranking.</summary>
admission
RuntimeClass
<br></details>

<details>
<summary>The _____ ensures a specific number of pod replicas are running at any one time across nodes</summary>
replication controller
<br></details>

<details>
<summary>A Pod can opt out of being modified by PodPresets altogether via the metadata _____ podpreset.admission.kubernetes.io/exclude: "true"</summary>
annotation
<br></details>

<details>
<summary>Containers within a single pod share ____ and _____ resources.</summary>
storage and network
<br></details>

<details>
<summary>Ready, ContainerReady, lastProbeTime, reason. These are the types of latest variable observations of an object's state called _____, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.</summary>
Conditions
<br></details>

<details>
<summary>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</summary>
an owner
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called a&nbsp;<i>_____ </i>deletion.</span></summary>
cascading
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When configuring a container, the _____ field allows you t</span><span style="color: rgb(34, 34, 34);">o pass a secret that contains a Docker (or other) image registry password.</span></summary>
imagePullSecrets&nbsp;
<br></details>

<details>
<summary>Does a Service load balance traffic across multiple Pods?</summary>
Yes
<br></details>

<details>
<summary>Containers within a single pod share network resources - _____ and _____</summary>
IP address and port space
<br></details>

<details>
<summary>A _____ is an API resource for injecting additional runtime requirements into a label-selected Pod at creation time.</summary>
Pod Preset
<br></details>

<details>
<summary>A logical group of containers with shared network and storage and specifications for how to run each is called a _____</summary>
Pod
<br></details>

<details>
<summary>Are containers in a Pod automatically co-located and co-scheduled on the same node?</summary>
Yes
<br></details>

<details>
<summary>Can a pod's containers share resources, dependencies, communicate with each other and coordinate their lifecycle?</summary>
Yes
<br></details>

<details>
<summary>A pod's _____ is the high-level summary of where the pod is in its lifecycle.</summary>
phase
<br></details>

<details>
<summary><table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting. This is the _____ phase of a Pod's lifecycle.</td></tr></tbody></table></summary>
Running
<br></details>

<details>
<summary>List all 5 Pod <b>phases</b></summary>
Pending
Running
Succeeded
Failed
Unknown
<br></details>

<details>
<summary>The six fields of a _____ are&nbsp;reason, status, message, type, lastProbeTime, lastTransitionTime.</summary>
PodCondition&nbsp;
<br></details>

<details>
<summary>A Pod's <b>_____&nbsp;</b>condition field provides a unique, one-word reason for the condition's last transition.</summary>
reason&nbsp;
<br></details>

<details>
<summary>The four possible values of a Pod's <b>_____</b>&nbsp;condition field are&nbsp;PodScheduled,&nbsp;Ready,&nbsp;Initialized,&nbsp;ContainersReady</summary>
type
<br></details>

<details>
<summary>If the _____ probe fails, the Pod's IP address&nbsp;is removed from the endpoints of all&nbsp;<b>Services&nbsp;</b>that match the Pod.</summary>
readiness
<br></details>

<details>
<summary>If the _____ probe fails, the container is killed by the kubelet, then subjected to the container's&nbsp;<b>restart policy</b>.</summary>
startup
<br></details>

<details>
<summary>To find out why a container is in&nbsp;<b>Waiting </b>state, you can check its state's <b>_____&nbsp;</b>field</summary>
Reason
<br></details>

<details>
<summary>The _____ hook is executed prior to a container entering its <b>Running </b>state.</summary>
postStart
<br></details>

<details>
<summary>Once bound to a node, will a Pod ever rebound to another node?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></summary>
label selectors
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
<br></details>

<details>
<summary>The annotation to&nbsp;disable PodPreset for a Specific Pod is...</summary>
podpreset.admission.kubernetes.io/exclude: "true"
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></summary>
node labels
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>Do ephemeral containers guarantee execution?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can specify relationships between an owner and dependents by manually setting their .metadata._____ field</span></summary>
ownerReference
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In _____</span><span style="color: rgb(34, 34, 34);">, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents in the background.</span></summary>
background cascading deletion
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In </span><i>_____</i><span style="color: rgb(34, 34, 34);">, the root object first enters a "deletion in progress" state.&nbsp;</span>Once the "deletion in progress" state is set, the garbage collector deletes the object's dependents. Once the garbage collector has deleted all dependents,&nbsp;it deletes the owner object.</summary>
foreground cascading deletion
<br></details>

<details>
<summary>To control the cascading deletion policy, set the _____&nbsp;field on the _____&nbsp;argument when deleting an Object.&nbsp;</summary>
propagationPolicy&nbsp;
deleteOptions
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.</span></summary>
<span style="color: rgb(34, 34, 34);">priority</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ is a non-namespaced object that defines a mapping from a priority class name to the integer value of the priority.</span></summary>
<span style="color: rgb(34, 34, 34);">PriorityClass</span>
<br></details>

<details>
<summary>Is there currently an API standard for whether a Pod is considered sandboxed?</summary>
No -&nbsp;<span style="color: rgb(34, 34, 34);">Sandbox Pods may be identified by the use of a sandboxed runtime (such as gVisor or Kata Containers), but there is no standard definition of what a sandboxed runtime is.</span>
<br></details>

<details>
<summary>_____ optimize a given metric (e.g. CPU utilization) across a set of Pods. They increase or decrease the number of replicas to achieve it.</summary>
Horizontal Pod Autoscalers (HPA)
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">PodPreset</span>
<br></details>

<details>
<summary>_____ restrict the scheduler�s freedom, trading off one application against another.&nbsp;</summary>
Pod affinities
<br></details>

<details>
<summary>Do pods run a single container each?</summary>
Not necessarily. They can run multiple containers.
<br></details>

<details>
<summary>Do Pods each have a unique IP address?</summary>
Yes, for each address family
<br></details>

<details>
<summary><b>Failed </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
<br></details>

<details>
<summary><b>Unknown </b>phase</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
<br></details>

<details>
<summary>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</summary>
a timestamp for when the Pod last transitioned from one status to another.
<br></details>

<details>
<summary>The three possible values for the&nbsp;<b>status</b>&nbsp;Pod condition field are...</summary>
<b>"True"</b>
<b>
</b><b>"False"</b><b>
</b>"<b>Unknown"</b>
<br></details>

<details>
<summary>A probe can have one of three results:</summary>
<b>Success</b>The Container passed the diagnostic
<b>
</b><b>Failure</b>The Container failed the diagnostic<b>
</b><b>Unknown</b>The diagnostic failed, so no action should be taken
<br></details>

<details>
<summary>If a container's _____ probe fails, the container is killed by the kubelet, then subjected to the container's&nbsp;restart policy.</summary>
liveness&nbsp;
<br></details>

<details>
<summary>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe
What will be the state of each probe of the container?</summary>
<b>Success </b>on all of them
<br></details>

<details>
<summary>A _____ probe indicates whether a container is ready to service requests.</summary>
readiness&nbsp;
<br></details>

<details>
<summary>A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;
Do you still need a livenessProbe?</summary>
Not necessarily.&nbsp;
The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;restartPolicy.
<br></details>

<details>
<summary>A container is in the <b>_____&nbsp;</b>state when it has successfully or unsuccessfully completed execution.</summary>
Terminated
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at 5 minutes, and is reset after ten minutes of successful execution.</span></summary>
exponential back-off
<br></details>

<details>
<summary>The degree to which Pods may be unevenly distributed (i.e. t<span style="color: rgb(34, 34, 34);">he maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type) is called the _____</span></summary>
maxSkew
<br></details>

<details>
<summary><b>whenUnsatisfiable </b>possible values:</summary>
<b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span>
<br></details>

<details>
<summary>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring. Do involuntary disruptions count against the budget?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A temporary "_____" container may be ran in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish user-initiated actions such as, t</span>roubleshooting and inspecting services.</summary>
<span style="color: rgb(34, 34, 34);">ephemeral&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">To troubleshoot a hard-to-reproduce bug, you might need to inspect the state of an existing Pod and its containers, or run some arbitrary commands. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">inside an existing Pod.</span></summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container</span>
<br></details>

<details>
<summary>Do ephemeral containers have guaranteed resources?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</summary>
process namespace sharing
<br></details>

<details>
<summary>If you delete an object without deleting its dependents automatically, the dependents are said to become&nbsp;<i>_____</i></summary>
orphaned
<br></details>

<details>
<summary>PodPresets cannot be used to override a Pod�s own configuration, only to fill in settings which the Pod itself _____</summary>
&nbsp;hasn't specified.
<br></details>

<details>
<summary>_____ can inject bits of common configuration into all selected Pods at creation time. For example, you could use it to mount a particular Volume on all matching Pods.</summary>
PodPresets&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A quorum-based application must ensure that the number of running replicas is never brought below the minimum required for a quorum. This can be achieved with a _____</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>A pod represents _____ running in your cluster.</summary>
Processes
<br></details>

<details>
<summary>In terms of Docker constructs, a Pod is modelled as a group of Docker containers with shared _____ and shared _____</summary>
namespaces
filesystem volumes
<br></details>

<details>
<summary><table><tbody><tr><td>A Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created, either still being scheduled or download images. This describes a Pod's _____ phase.</td></tr></tbody></table></summary>
Pending
<br></details>

<details>
<summary><b>Succeeded </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
<br></details>

<details>
<summary>A Pod's _____&nbsp;condition field provides a timestamp for when the Pod condition was last probed.</summary>
lastProbeTime&nbsp;
<br></details>

<details>
<summary>The <b>message&nbsp;</b>condition field provides...</summary>
a human-readable message indicating details about the transition from one status to another.
<br></details>

<details>
<summary>A container's _____ probe indicates whether the application in the container has started.</summary>
startup
<br></details>

<details>
<summary>All other probes are disabled until _____ succeeds.</summary>
startupProbe
<br></details>

<details>
<summary>A Pod should only be sent traffic when a probe succeeds. Which probe can achieve this?</summary>
readinessProbe
<br></details>

<details>
<summary>A container is <b>_____&nbsp;</b>when it is neither&nbsp;<b>Running&nbsp;</b>or&nbsp;<b>Terminated</b>. It is likely pulling images, applying secrets etc.</summary>
Waiting
<br></details>

<details>
<summary>A container is in the <b>_____&nbsp;</b>state when it is executing without issues.</summary>
Running
<br></details>

<details>
<summary>To tell why a container is in <b>Terminated </b>state, check its state's&nbsp;<b>_____&nbsp;</b>and&nbsp;<b>_____&nbsp;</b>fields.</summary>
Reason and Exit Code
<br></details>

<details>
<summary>The _____ hook is executed before a container enters Terminated state.</summary>
preStop
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of the .status._____ fields for the Pod.&nbsp;</span>If such a field isn't found, the status of the condition defaults to&nbsp;<b>"False"</b></summary>
conditions
<br></details>

<details>
<summary>Does a Pod's <b>restartPolicy </b>apply to all its containers?</summary>
Yes
<br></details>

<details>
<summary>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></summary>
creation time
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies their _____</span></summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the topology spread constraint is indicated in the _____ field.</span></summary>
<strong>whenUnsatisfiable</strong>
<br></details>

<details>
<summary>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></summary>
replicas
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></summary>
Yes
<br></details>

<details>
<summary>Will an ephemeral container ever be automatically restarted?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____ indicates the importance of a Pod relative to other Pods.</span></summary>
<span style="color: rgb(34, 34, 34);">Priority</span>
<br></details>

<details>
<summary>Critical pods rely on scheduler _____ to be scheduled when a cluster is under resource pressure.</summary>
preemption
<br></details>

<details>
<summary>The _____&nbsp;field indicates that the value of this PriorityClass should be used for Pods without a&nbsp;priorityClassName.&nbsp;Only one such PriorityClass can exist in the system.</summary>
globalDefault
<br></details>

<details>
<summary>Pods with PreemptionPolicy:_____&nbsp;will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. It will stay in the scheduling queue, until sufficient resources are free.&nbsp;</summary>
Never
<br></details>

<details>
<summary>PreemptionPolicy&nbsp;defaults to&nbsp;_____, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).&nbsp;</summary>
PreemptLowerPriority
<br></details>

<details>
<summary>_____ repel other Pods instead of attracting. Ex.: One to replicas of the same Pod can help spread your replicas evenly across the cluster.</summary>
anti-affinity
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total. This can be achieved via a _____</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>If non-preempting pods cannot be scheduled at a given time, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them. This is because non-preempting pods are subject to scheduler...</summary>
back-off
<br></details>

<details>
<summary>The kubelet manages the _____ file for each container of a Pod to prevent Docker from modifying it.</summary>
hosts
<br></details>

<details>
<summary>The three available ImagePullPolicies of a container are Always, Never and _____ (default)</summary>
IfNotPresent
<br></details>

<details>
<summary><code>kubectl exec</code>&nbsp;was insufficient to interactively troubleshoot a container, because it has crashed, and didn't have any debugging utilities.

To troubleshoot, you can use _____ containers.</summary>
Ephemeral containers / busybox
<br></details>

<details>
<summary>.spec._____&nbsp;adds entries to a Pod's /etc/hosts&nbsp;file, overriding its hostname resolution when DNS and other options are not applicable.&nbsp;</summary>
HostAliases
<br></details>

<details>
<summary>A container without a readinessProbe is assumed to be ready for traffic once it starts. What are some potential problems with this?&nbsp;</summary>
The containerised application might need time to start after its enclosing container has. All requests to the app will fail throughout this process, because the container was "Ready" before the app started.
<br></details>

<details>
<summary>If a container crashes inside a pod due to an unrecoverable error (such as a typo in the code), should you signal the liveness probe?</summary>
No. Let it crash by exiting the process, allowing kubelet to restart it.&nbsp;<a href="https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-revisited-how-to-avoid-shooting-yourself-in-the-other-foot/#letitcrash">https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-revisited-how-to-avoid-shooting-yourself-in-the-other-foot/#letitcrash</a>
<br></details>

<details>
<summary>Liveness probes are designed to _____ your containers when stuck, such as in an infinite loop, where there is no way for the process to seek help externally, or even exit.</summary>
restart
<br></details>

<details>
<summary>A stuck process consuming 100% CPU won't reply to _____ probes. If you don't have a _____ probe, it will stay uselessly&nbsp;<em>Running,</em>&nbsp;serving no requests and consuming resources.</summary>
Readiness
Liveness
<br></details>

<details>
<summary>_____ probes are used for recovery when a process is not responsive.</summary>
Liveness&nbsp;
<br></details>

<details>
<summary>Liveness and Readiness probes pointing to the same endpoint inside a container will cause the container to be detached from the Service and deleted at the same time. Is this okay?</summary>
No - it will cause connection drops due to the unready container running out of time to drain its current connections due to being deleted.
<br></details>

<details>
<summary>Should readiness probes be allowed to depend on other services (databases, APIs...) to succeed?</summary>
No&nbsp;<a href="https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-how-to-avoid-shooting-yourself-in-the-foot/#shootingyourselfinthefootwithreadinessprobes">https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-how-to-avoid-shooting-yourself-in-the-foot/#shootingyourselfinthefootwithreadinessprobes</a>
<br></details>

<details>
<summary>While it's in its termination grace period, you might want an app to process remaining incoming requests by adding a _____ handler.</summary>
preStop
<br></details>

<details>
<summary>Most applications should log to _____ and send errors to _____, which are then aggregated by another service.</summary>
stdout
stderr
<br></details>

<details>
<summary>Does each Pod have a unique IP?</summary>
Yes
<br></details>

<details>
<summary>A _____ is like a machine with its own IP address and ports, running containers inside which can map their ports to it.</summary>
Pod
<br></details>

<details>
<summary>Does a Pod have its own network namespace inside?</summary>
Yes
<br></details>

<details>
<summary>Does a Pod have its own virtual ethernet connection?</summary>
Yes
<br></details>

<details>
<summary>Is running backups a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>Is running database synchronisation a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>Is running authentication proxies a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>The "pause" container (also called sandbox container) inside each Pod reserves and holds the network _____, enabling containers to communicate with each other and retaining the IP address of the pod.</summary>
namespace (netns)
<br></details>

<details>
<summary>A _____ is an abstract way to expose on the network an application running on a set of Pods.</summary>
service
<br></details>

<details>
<summary>Each Kubernetes Node has its own _____ range from which it assigns its pods unique IPs.</summary>
CIDR IP block
<br></details>