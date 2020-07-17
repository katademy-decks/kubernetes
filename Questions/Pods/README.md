# Pods 

<details>
<summary>The three available ImagePullPolicies of a container, are...</summary>
Always, Never, IfNotPresent (default)
<br></details><details>
<summary>What is DaemonSet?</summary>
A Kubernetes&nbsp;<b>Controller&nbsp;</b>which ensures that all (or some)&nbsp;<b>Nodes run a copy of a Pod.
</b>
<br></details><details>
<summary>What will happen to ReplicaSet pods inside a node when that node gets deleted?</summary>
These pods will be replaced on another node, or nodes.
<br></details><details>
<summary>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</summary>
sticky identity
<br></details><details>
<summary>An application requires several of the following:<ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>Which workload object could work best?</summary>
StatefulSet
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Will deleting or scaling a StatefulSet down also delete&nbsp;</span><span style="color: rgb(34, 34, 34);">the volumes associated with it?</span></summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet is linked to its Pods via their _____ field.</span><span style="color: rgb(34, 34, 34);">&nbsp;It's through this link that the ReplicaSet knows of the state of the Pods it is maintaining and plans accordingly.</span></summary>
metadata.ownerReferences
<br></details><details>
<summary>_____&nbsp;<span style="color: rgb(34, 34, 34);">is an object which can own ReplicaSets and update them and their Pods via declarative, server-side rolling updates.</span></summary>
Deployment
<br></details><details>
<summary>Is running a logs collection daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details><details>
<summary>Can you perform a rolling update on a DaemonSet?</summary>
Yes
<br></details><details>
<summary>The _____ ensures a specific number of pod replicas are running at any one time across nodes</summary>
replication controller
<br></details><details>
<summary>A Kubernetes concept that represents the smallest unit of deployment.</summary>
Pod
<br></details><details>
<summary>Can a Pod can opt out of being modified by PodPresets altogether?</summary>
Yes - via the exclude annotation <b>podpreset.admission.kubernetes.io/exclude: "true"</b>
<br></details><details>
<summary>Containers within a single pod share ____ and _____ resources.</summary>
storage and network
<br></details><details>
<summary>The number of old ReplicaSets to retain for rollback is defined in a deployment's .spec._____</summary>
revisionHistoryLimit
<br></details><details>
<summary>Ready, ContainerReady, lastProbeTime, reason. These are the types of latest variable observations of an object's state called _____, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.</summary>
Conditions
<br></details><details>
<summary>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about the _____ and _____of these Pods</summary>
ordering and uniqueness
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></summary>
<b>Deployments&nbsp;</b>or<b> Replicasets </b>-<span style="color: rgb(34, 34, 34);">&nbsp;workload objects that provide a set of stateless replicas.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet identifies new Pods to acquire by using its _____.&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;If there is a Pod that has no OwnerReference or the Ow</span>nerReference is not a&nbsp;<a href="https://kubernetes.io/docs/concepts/architecture/controller/">Controller</a>&nbsp;an<span style="color: rgb(34, 34, 34);">d the _____ matches, it will be immediately acquired by said ReplicaSet.</span></summary>
selector
<br></details><details>
<summary>Is running a cluster storage daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details><details>
<summary>Pods waiting to be scheduled are usually created in <b>Pending </b>state. Are DaemonSet pods created in <b>Pending </b>state?</summary>
No - it is an inconsistency due to being scheduled by the DaemonSet controller.
<br></details><details>
<summary>When <b>Pod preemption</b> is enabled, does the DaemonSet controller consider <b>pod priority</b> and <b>preemption </b>when making scheduling decisions?</summary>
No - <b>Pod preemption</b> is handled by the <b>default scheduler</b>, DaemonSet pods are scheduled by the <b>DaemonSet controller</b>.
<br></details><details>
<summary>If node labels are changed, the DaemonSet will _____ Pods to newly matching nodes.</summary>
Add
<br></details><details>
<summary>If node labels are changed, the DaemonSet will _____ Pods from newly not-matching nodes.</summary>
Delete
<br></details><details>
<summary>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</summary>
an owner
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called a&nbsp;<i>_____ </i>deletion.</span></summary>
cascading
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If you create a DaemonSet with the same selector as Pods that belonged to a matching DaemonSet, what will the new DaemonSet do with the Pods?</span></summary>
adopt them
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">ensures that all (or some) Nodes run a copy of a Pod.</span></summary>
DaemonSet
<br></details><details>
<summary>A _____ is an API resource for injecting additional runtime requirements into a label-selected Pod at creation time.</summary>
Pod Preset
<br></details><details>
<summary>What’s a <b>Pod</b></summary>
A logical group of containers with shared network and storage, and a specification for how to run.
<br></details><details>
<summary>What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</summary>
These pods will be garbage collected
<br></details><details>
<summary>Are containers in a Pod automatically co-located and co-scheduled on the same node?</summary>
Yes
<br></details><details>
<summary>Can a pod's containers share resources, dependencies, communicate with each other and coordinate their lifecycle?</summary>
Yes
<br></details><details>
<summary>The <b>phase </b>of a pod is...</summary>
A high-level summary of where the pod is in its lifecycle
<br></details><details>
<summary><table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting. This is the _____ phase of a Pod's lifecycle.</td></tr></tbody></table></summary>
Running
<br></details><details>
<summary>List all 5 Pod <b>phases</b></summary>
Pending
Running
Succeeded
Failed
Unknown
<br></details><details>
<summary>List all six fields in a <b>PodCondition</b></summary>
reason
status
message
type
lastProbeTime
lastTransitionTime
<br></details><details>
<summary>The <b>reason&nbsp;</b>condition field provides...</summary>
a unique, one-word reason for the condition's last transition.
<br></details><details>
<summary>The four possible values of the&nbsp;<b>type</b>&nbsp;condition field are...</summary>
<b>PodScheduled</b>
<b>Ready</b>
<b>Initialized</b>
<b>ContainersReady</b>
<br></details><details>
<summary>If the readinessProbe fails, what happens?</summary>
The Pod's IP address&nbsp;is removed from the endpoints of all <b>Services </b>that match the Pod.
<br></details><details>
<summary>If the startupProbe fails, the container...</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
<br></details><details>
<summary>A container should be killed or restarted if a probe fails. What can be done to achieve this?</summary>
1. Specify a <b>livenessProbe&nbsp;</b>
2. Add a <b>restartPolicy </b>of <b>Always </b>or <b>OnFailure</b>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A Container should be able to take itself down for maintenance. What can achieve this?</span></summary>
A <b>readinessProbe </b>that checks an endpoints specific to readiness that is different from the liveness probe.
<br></details><details>
<summary>The three possible states of containers are...</summary>
Waiting
Running
Terminated
<br></details><details>
<summary>To find out why a container is in&nbsp;<b>Waiting </b>state, you can check its state's <b>_____&nbsp;</b>field</summary>
Reason
<br></details><details>
<summary>The _____ hook is executed prior to a container entering its <b>Running </b>state.</summary>
postStart
<br></details><details>
<summary>Once bound to a node, will a Pod ever rebound to another node?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></summary>
label selectors
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
<br></details><details>
<summary>The annotation to&nbsp;disable PodPreset for a Specific Pod is...</summary>
podpreset.admission.kubernetes.io/exclude: "true"
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If set, a cluster's default topology spread constraints are applied to a Pod if, and only if:</span></summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span></summary>
PodDisruptionBudget
<br></details><details>
<summary>Do ephemeral containers guarantee execution?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____. Although its Pods are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets currently require manually creating a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods.</span></summary>
headless service
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
<br></details><details>
<summary>Is running a node monitoring daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Normally, the node that a Pod runs on is selected by the Kubernetes scheduler. However, DaemonSet pods are created and scheduled by _____ instead.</span></summary>
<span style="color: rgb(34, 34, 34);">the DaemonSet controller</span>
<br></details><details>
<summary>DaemonSets are similar to Deployments in that they both...</summary>
<span style="color: rgb(34, 34, 34);">create Pods, with processes which are not expected to terminate (web servers, storage servers etc).</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Every dependent (i.e. owned) object has a metadata.</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;field that points to the owning object. The owning object is usually a&nbsp;</span><span style="color: rgb(34, 34, 34);">Job, CronJob,&nbsp;</span><span style="color: rgb(34, 34, 34);">Deployment, DaemonSet,&nbsp;</span><span style="color: rgb(34, 34, 34);">StatefulSet,</span><span style="color: rgb(34, 34, 34);">&nbsp;ReplicationController, ReplicaSet.</span></summary>
ownerReferences
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can specify relationships between an owner and dependents by manually setting their .metadata._____ field</span></summary>
ownerReference
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In _____</span><span style="color: rgb(34, 34, 34);">, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents in the background.</span></summary>
background cascading deletion
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In </span><i>_____</i><span style="color: rgb(34, 34, 34);">, the root object first enters a "deletion in progress" state.&nbsp;</span>Once the "deletion in progress" state is set, the garbage collector deletes the object's dependents. Once the garbage collector has deleted all dependents,&nbsp;it deletes the owner object.</summary>
foreground cascading deletion
<br></details><details>
<summary>To control the cascading deletion policy, set the <font face="monospace">_____&nbsp;</font>field on the <font face="monospace">_____&nbsp;</font>argument when deleting an Object.&nbsp;</summary>
<code>propagationPolicy</code>&nbsp;
<code>deleteOptions</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.</span></summary>
<span style="color: rgb(34, 34, 34);">priority</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A _____ is a non-namespaced object that defines a mapping from a priority class name to the integer value of the priority.</span></summary>
<span style="color: rgb(34, 34, 34);">PriorityClass</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A</span><span style="color: rgb(34, 34, 34);">&nbsp;data science workload</span><span style="color: rgb(34, 34, 34);">&nbsp;may need to be prioritized above others, though without discarding existing work via pre-emption. To ensure this job begins once cluster resources become free, you could set...</span></summary>
PreemptionPolicy: Never
<br></details><details>
<summary>Identical Pods in a deployment are referred to as...</summary>
Replicas
<br></details><details>
<summary>_____ optimize a given metric (e.g. CPU utilization) across a set of Pods. They increase or decrease the number of replicas to achieve it.</summary>
Horizontal Pod Autoscalers (HPA)
<br></details><details>
<summary>A pod's only container exits with&nbsp;<b>success</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>Always?</b></summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays <b>Running</b>.
<br></details><details>
<summary>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>Always</b>?</summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A _____ allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">PodPreset</span>
<br></details><details>
<summary>From one container, how could you view processes in other containers?</summary>
Enable process namespace sharing
<br></details><details>
<summary>_____ restrict the scheduler’s freedom, trading off one application against another.&nbsp;</summary>
Pod affinities
<br></details><details>
<summary>Do pods run a single container each?</summary>
Not necessarily. They can run multiple containers.
<br></details><details>
<summary>Do Pods each have a unique IP address?</summary>
Yes, for each address family
<br></details><details>
<summary><b>Failed </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
<br></details><details>
<summary><b>Unknown </b>phase</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
<br></details><details>
<summary>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</summary>
a timestamp for when the Pod last transitioned from one status to another.
<br></details><details>
<summary>The three possible values for the&nbsp;<b>status</b>&nbsp;Pod condition field are...</summary>
<b>"True"</b>
<b>
</b><b>"False"</b><b>
</b>"<b>Unknown"</b>
<br></details><details>
<summary>A probe can have one of three results:</summary>
<b>Success</b>The Container passed the diagnostic
<b>
</b><b>Failure</b>The Container failed the diagnostic<b>
</b><b>Unknown</b>The diagnostic failed, so no action should be taken
<br></details><details>
<summary>If a livenessProbe fails, the container...</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
<br></details><details>
<summary>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe
What will be the state of each probe of the container?</summary>
<b>Success </b>on all of them
<br></details><details>
<summary>readinessProbe indicates whether...</summary>
a container is ready to service requests.
<br></details><details>
<summary>A container's default readiness state before the initial delay is...</summary>
Failure
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Do you still need a livenessProbe?</span></summary>
Not necessarily.&nbsp;
<span style="color: rgb(34, 34, 34);">The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;</span><code>restartPolicy</code><span style="color: rgb(34, 34, 34);">.</span>
<br></details><details>
<summary>A container is in the <b>_____&nbsp;</b>state when it has successfully or unsuccessfully completed execution.</summary>
Terminated
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Inject extra feedback or signals into PodStatus via...</span></summary>
<b>Pod readiness</b>
<br></details><details>
<summary>Default restartPolicy is...</summary>
Always
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at 5 minutes, and is reset after ten minutes of successful execution.</span></summary>
exponential back-off
<br></details><details>
<summary>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy </b>is <b>Never</b>?</summary>
Pod phase becomes Failed.
<br></details><details>
<summary>What applies Pod Presets to incoming pod creation requests?</summary>
PodPreset admission controller
<br></details><details>
<summary>The degree to which Pods may be unevenly distributed, i.e. t<span style="color: rgb(34, 34, 34);">he maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type is called...</span></summary>
<strong>maxSkew</strong>
<br></details><details>
<summary><b>whenUnsatisfiable </b>possible values:</summary>
<b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A Deployment&nbsp;</span><span style="color: rgb(34, 34, 34);">is supposed to have 5 pods at any given time, with</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">If a PodDisruptionBudget allows for there to be 4 at a time, then how many pods at a time are allowed to be voluntarily disrupted by the Eviction API?</span></summary>
<span style="color: rgb(34, 34, 34);">One</span>
<br></details><details>
<summary>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring. Do involuntary disruptions count against the budget?</summary>
No
<br></details><details>
<summary>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</summary>
<b>No!&nbsp;</b><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></summary>
Yes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A temporary ephemeral container is ran in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish user-initiated actions such as..</span></summary>
Troubleshooting and inspecting services
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">To troubleshoot a hard-to-reproduce bug, you might need to inspect the state of an existing Pod and its containers, or run some arbitrary commands. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">inside an existing Pod.</span></summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container</span>
<br></details><details>
<summary>Do ephemeral containers have guaranteed resources?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</summary>
process namespace sharing
<br></details><details>
<summary>When deleting a DaemonSet with kubectl, you can specify the flag _____, then the Pods will remain on the nodes.&nbsp;</summary>
--cascade=false
<br></details><details>
<summary>Given that you can start daemon processes on a node directly via systemd, why use a DaemonSet?</summary>
<ul><li>Ability to monitor and manage logs for daemons in the same way as applications.</li><li>Same config language and tools (e.g. Pod templates,&nbsp;<code>kubectl</code>) for daemons and applications.</li><li>Running daemons in containers with resource limits increases isolation between daemons from app containers. However, this can also be accomplished by running the daemons in a container but not in a Pod (e.g. start directly via Docker).</li></ul>
<br></details><details>
<summary>If you delete an object without deleting its dependents automatically, the dependents are said to become&nbsp;<i>_____</i></summary>
orphaned
<br></details><details>
<summary>Cascading deletion types</summary>
"Orphan", "Foreground", or "Background"
<br></details><details>
<summary>PodPresets cannot be used to override a Pod’s own configuration, only to fill in settings which the Pod itself _____</summary>
&nbsp;hasn't specified.
<br></details><details>
<summary>_____ allow you to schedule one copy of a Pod on every node (for example, a logging agent).</summary>
DaemonSets
<br></details><details>
<summary>_____ can inject bits of common configuration into all selected Pods at creation time. For example, you could use it to mount a particular Volume on all matching Pods.</summary>
PodPresets&nbsp;
<br></details><details>
<summary>_____ start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.</summary>
StatefulSets&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A quorum-based application must ensure that the number of running replicas is never brought below the minimum required for a quorum. This can be achieved with a _____</span></summary>
PodDisruptionBudget
<br></details><details>
<summary>A pod represents _____ running in your cluster.</summary>
Processes
<br></details><details>
<summary>In terms of Docker constructs, a Pod is modelled as a group of Docker containers with shared _____ and shared _____</summary>
namespaces
filesystem volumes
<br></details><details>
<summary>A container can be set to run in privileged mode to allow Linux capabilities inside the container, such as...</summary>
device accessvolume plugin developmentnetwork plugin development and stack manipulation
<br></details><details>
<summary><table><tbody><tr><td>A Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created, either still being scheduled or download images. This describes a Pod's _____ phase.</td></tr></tbody></table></summary>
Pending
<br></details><details>
<summary><b>Succeeded </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
<br></details><details>
<summary>The <b>lastProbeTime</b>&nbsp;condition field provides...</summary>
A timestamp for when the Pod condition was last probed.
<br></details><details>
<summary>The <b>message&nbsp;</b>condition field provides...</summary>
a human-readable message indicating details about the transition from one status to another.
<br></details><details>
<summary>A livenessProbe indicates whether a container is...</summary>
running
<br></details><details>
<summary>startupProbe indicates whether...</summary>
the application in the container has started.
<br></details><details>
<summary>All other probes are disabled until _____ succeeds.</summary>
startupProbe
<br></details><details>
<summary>A Pod should only be sent traffic when a probe succeeds. What can achieve this?</summary>
readinessProbe
<br></details><details>
<summary>A container is <b>_____&nbsp;</b>when it is neither&nbsp;<b>Running&nbsp;</b>or&nbsp;<b>Terminated</b>. It is likely pulling images, applying secrets etc.</summary>
Waiting
<br></details><details>
<summary>A container is in the <b>_____&nbsp;</b>state when it is executing without issues.</summary>
Running
<br></details><details>
<summary>To tell why a container is in <b>Terminated </b>state, check its state's&nbsp;<b>_____&nbsp;</b>and&nbsp;<b>_____&nbsp;</b>fields.</summary>
Reason and Exit Code
<br></details><details>
<summary>The _____ hook is executed before a container enters Terminated state.</summary>
preStop
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of the .status._____ fields for the Pod.&nbsp;</span>If such a field isn't found, the status of the condition defaults to&nbsp;<b>"False"</b></summary>
conditions
<br></details><details>
<summary><b>restartPolicy </b>possible values are...</summary>
Always
Never
OnFailure
<br></details><details>
<summary>Does a Pod's <b>restartPolicy </b>apply to all its containers?</summary>
Yes
<br></details><details>
<summary>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></summary>
Yes
<br></details><details>
<summary>A pod's only container exits with <b>success</b>. What happens if the&nbsp;<b>restartPolicy </b>is <b>Never?</b></summary>
Pod&nbsp;<code>phase</code>&nbsp;becomes&nbsp;<b>Succeeded</b>.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></summary>
creation time
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies their _____</span></summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can use </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;to control&nbsp;</span><span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains&nbsp;</span><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains).</span></summary>
topology spread constraints
<br></details><details>
<summary>You have a 4-node cluster with the following labels:<pre><code>NAME    STATUS   ROLES    AGE     VERSION   LABELS
node1   Ready    &lt;none&gt;   4m26s   v1.16.0   node=node1,zone=zoneA
node2   Ready    &lt;none&gt;   3m58s   v1.16.0   node=node2,zone=zoneA
node3   Ready    &lt;none&gt;   3m17s   v1.16.0   node=node3,zone=zoneB
node4   Ready    &lt;none&gt;   2m43s   v1.16.0   node=node4,zone=zoneB</code></pre>What would the cluster logically look like?</summary>
<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+</code></pre>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the topology spread constraint is indicated in the _____ field.</span></summary>
<strong>whenUnsatisfiable</strong>
<br></details><details>
<summary>Does deleting deployments or pods bypass PodDisruptionBudgets?</summary>
Yes
<br></details><details>
<summary>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></summary>
replicas
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></summary>
Yes
<br></details><details>
<summary>Will an ephemeral container ever be automatically restarted?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">_____ indicates the importance of a Pod relative to other Pods.</span></summary>
<span style="color: rgb(34, 34, 34);">Priority</span>
<br></details><details>
<summary>A malicious user could create Pods at the highest possible priorities, causing other Pods to be evicted/not get scheduled. An administrator can use _____ to prevent users from creating pods at high priorities.</summary>
ResourceQuota
<br></details><details>
<summary>Critical pods rely on scheduler _____ to be scheduled when a cluster is under resource pressure.</summary>
preemption
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field indicates that the value of this PriorityClass should be used for Pods without a&nbsp;</span><code>priorityClassName</code><span style="color: rgb(34, 34, 34);">.&nbsp;</span><span style="color: rgb(34, 34, 34);">Only one such PriorityClass </span><span style="color: rgb(34, 34, 34);">can exist in the system.</span></summary>
<code>globalDefault</code>
<br></details><details>
<summary>Pods with PreemptionPolicy:<font face="monospace">_____</font>&nbsp;will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. It will stay in the scheduling queue, until sufficient resources are free.&nbsp;</summary>
Never
<br></details><details>
<summary><code>PreemptionPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;defaults to&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).&nbsp;</span></summary>
PreemptLowerPriority
<br></details><details>
<summary>_____ repel other Pods instead of attracting. Ex.: One to replicas of the same Pod can help spread your replicas evenly across the cluster.</summary>
anti-affinity
<br></details><details>
<summary>A pod's only container exits with&nbsp;<b>success</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>OnFailure?</b></summary>
Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.
<br></details><details>
<summary>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>OnFailure</b>?</summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total. This can be achieved via a _____</span></summary>
PodDisruptionBudget
<br></details><details>
<summary>If non-preempting pods cannot be scheduled at a given time, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them. This is because non-preempting pods are subject to scheduler...</summary>
back-off
<br></details>