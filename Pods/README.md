# Pods 

<details>
<summary>
<b>What is DaemonSet?</b>
</summary>
A Kubernetes&nbsp;<b>Controller&nbsp;</b>which ensures that all (or some)&nbsp;<b>Nodes run a copy of a Pod.
</b>
</details>

<details>
<summary>
<b>What will happen to ReplicaSet pods inside a node when that node gets deleted?</b>
</summary>
These pods will be replaced on another node, or nodes.
</details>

<details>
<summary>
<b>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</b>
</summary>
sticky identity
</details>

<details>
<summary>
<b>An application requires several of the following:<ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>Which workload object could work best?</b>
</summary>
StatefulSet
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Will deleting or scaling a StatefulSet down also delete&nbsp;</span><span style="color: rgb(34, 34, 34);">the volumes associated with it?</span></b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A ReplicaSet is linked to its Pods via their _____ field.</span><span style="color: rgb(34, 34, 34);">&nbsp;It's through this link that the ReplicaSet knows of the state of the Pods it is maintaining and plans accordingly.</span></b>
</summary>
metadata.ownerReferences
</details>

<details>
<summary>
<b>_____&nbsp;<span style="color: rgb(34, 34, 34);">is an object which can own ReplicaSets and update them and their Pods via declarative, server-side rolling updates.</span></b>
</summary>
Deployment
</details>

<details>
<summary>
<b>Is running a logs collection daemon on every node a valid DaemonSet use case?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Can you perform a rolling update on a DaemonSet?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>The _____ ensures a specific number of pod replicas are running at any one time across nodes</b>
</summary>
replication controller
</details>

<details>
<summary>
<b>A Kubernetes concept that represents the smallest unit of deployment.</b>
</summary>
Pod
</details>

<details>
<summary>
<b>Can a Pod can opt out of being modified by PodPresets altogether?</b>
</summary>
Yes - via the exclude annotation <b>podpreset.admission.kubernetes.io/exclude: "true"</b>
</details>

<details>
<summary>
<b>Containers within a single pod share ____ and _____ resources.</b>
</summary>
storage and network
</details>

<details>
<summary>
<b>The number of old ReplicaSets to retain for rollback is defined in a deployment's .spec._____</b>
</summary>
revisionHistoryLimit
</details>

<details>
<summary>
<b>Ready, ContainerReady, lastProbeTime, reason. These are the types of latest variable observations of an object's state called _____, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.</b>
</summary>
Conditions
</details>

<details>
<summary>
<b>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about the _____ and _____of these Pods</b>
</summary>
ordering and uniqueness
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></b>
</summary>
<b>Deployments&nbsp;</b>or<b> Replicasets </b>-<span style="color: rgb(34, 34, 34);">&nbsp;workload objects that provide a set of stateless replicas.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A ReplicaSet identifies new Pods to acquire by using its _____.&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;If there is a Pod that has no OwnerReference or the Ow</span>nerReference is not a&nbsp;<a href="https://kubernetes.io/docs/concepts/architecture/controller/">Controller</a>&nbsp;an<span style="color: rgb(34, 34, 34);">d the _____ matches, it will be immediately acquired by said ReplicaSet.</span></b>
</summary>
selector
</details>

<details>
<summary>
<b>Is running a cluster storage daemon on every node a valid DaemonSet use case?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Pods waiting to be scheduled are usually created in <b>Pending </b>state. Are DaemonSet pods created in <b>Pending </b>state?</b>
</summary>
No - it is an inconsistency due to being scheduled by the DaemonSet controller.
</details>

<details>
<summary>
<b>When <b>Pod preemption</b> is enabled, does the DaemonSet controller consider <b>pod priority</b> and <b>preemption </b>when making scheduling decisions?</b>
</summary>
No - <b>Pod preemption</b> is handled by the <b>default scheduler</b>, DaemonSet pods are scheduled by the <b>DaemonSet controller</b>.
</details>

<details>
<summary>
<b>If node labels are changed, the DaemonSet will _____ Pods to newly matching nodes.</b>
</summary>
Add
</details>

<details>
<summary>
<b>If node labels are changed, the DaemonSet will _____ Pods from newly not-matching nodes.</b>
</summary>
Delete
</details>

<details>
<summary>
<b>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</b>
</summary>
an owner
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called a&nbsp;<i>_____ </i>deletion.</span></b>
</summary>
cascading
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If you create a DaemonSet with the same selector as Pods that belonged to a matching DaemonSet, what will the new DaemonSet do with the Pods?</span></b>
</summary>
adopt them
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">ensures that all (or some) Nodes run a copy of a Pod.</span></b>
</summary>
DaemonSet
</details>

<details>
<summary>
<b>A _____ is an API resource for injecting additional runtime requirements into a label-selected Pod at creation time.</b>
</summary>
Pod Preset
</details>

<details>
<summary>
<b>What’s a <b>Pod</b></b>
</summary>
A logical group of containers with shared network and storage, and a specification for how to run.
</details>

<details>
<summary>
<b>What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</b>
</summary>
These pods will be garbage collected
</details>

<details>
<summary>
<b>Are containers in a Pod automatically co-located and co-scheduled on the same node?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Can a pod's containers share resources, dependencies, communicate with each other and coordinate their lifecycle?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>The <b>phase </b>of a pod is...</b>
</summary>
A high-level summary of where the pod is in its lifecycle
</details>

<details>
<summary>
<b><table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting. This is the _____ phase of a Pod's lifecycle.</td></tr></tbody></table></b>
</summary>
Running
</details>

<details>
<summary>
<b>List all 5 Pod <b>phases</b></b>
</summary>
Pending
Running
Succeeded
Failed
Unknown
</details>

<details>
<summary>
<b>List all six fields in a <b>PodCondition</b></b>
</summary>
reason
status
message
type
lastProbeTime
lastTransitionTime
</details>

<details>
<summary>
<b>The <b>reason&nbsp;</b>condition field provides...</b>
</summary>
a unique, one-word reason for the condition's last transition.
</details>

<details>
<summary>
<b>The four possible values of the&nbsp;<b>type</b>&nbsp;condition field are...</b>
</summary>
<b>PodScheduled</b>
<b>Ready</b>
<b>Initialized</b>
<b>ContainersReady</b>
</details>

<details>
<summary>
<b>If the readinessProbe fails, what happens?</b>
</summary>
The Pod's IP address&nbsp;is removed from the endpoints of all <b>Services </b>that match the Pod.
</details>

<details>
<summary>
<b>If the startupProbe fails, the container...</b>
</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
</details>

<details>
<summary>
<b>A container should be killed or restarted if a probe fails. What can be done to achieve this?</b>
</summary>
1. Specify a <b>livenessProbe&nbsp;</b>
2. Add a <b>restartPolicy </b>of <b>Always </b>or <b>OnFailure</b>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A Container should be able to take itself down for maintenance. What can achieve this?</span></b>
</summary>
A <b>readinessProbe </b>that checks an endpoints specific to readiness that is different from the liveness probe.
</details>

<details>
<summary>
<b>The three possible states of containers are...</b>
</summary>
Waiting
Running
Terminated
</details>

<details>
<summary>
<b>To find out why a container is in&nbsp;<b>Waiting </b>state, you can check its state's <b>_____&nbsp;</b>field</b>
</summary>
Reason
</details>

<details>
<summary>
<b>The _____ hook is executed prior to a container entering its <b>Running </b>state.</b>
</summary>
postStart
</details>

<details>
<summary>
<b>Once bound to a node, will a Pod ever rebound to another node?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></b>
</summary>
label selectors
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></b>
</summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
</details>

<details>
<summary>
<b>The annotation to&nbsp;disable PodPreset for a Specific Pod is...</b>
</summary>
podpreset.admission.kubernetes.io/exclude: "true"
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If set, a cluster's default topology spread constraints are applied to a Pod if, and only if:</span></b>
</summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b>Do ephemeral containers guarantee execution?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____. Although its Pods are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSets currently require manually creating a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods.</span></b>
</summary>
headless service
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
</details>

<details>
<summary>
<b>Is running a node monitoring daemon on every node a valid DaemonSet use case?</b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Normally, the node that a Pod runs on is selected by the Kubernetes scheduler. However, DaemonSet pods are created and scheduled by _____ instead.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the DaemonSet controller</span>
</details>

<details>
<summary>
<b>DaemonSets are similar to Deployments in that they both...</b>
</summary>
<span style="color: rgb(34, 34, 34);">create Pods, with processes which are not expected to terminate (web servers, storage servers etc).</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Every dependent (i.e. owned) object has a metadata.</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;field that points to the owning object. The owning object is usually a&nbsp;</span><span style="color: rgb(34, 34, 34);">Job, CronJob,&nbsp;</span><span style="color: rgb(34, 34, 34);">Deployment, DaemonSet,&nbsp;</span><span style="color: rgb(34, 34, 34);">StatefulSet,</span><span style="color: rgb(34, 34, 34);">&nbsp;ReplicationController, ReplicaSet.</span></b>
</summary>
ownerReferences
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can specify relationships between an owner and dependents by manually setting their .metadata._____ field</span></b>
</summary>
ownerReference
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In _____</span><span style="color: rgb(34, 34, 34);">, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents in the background.</span></b>
</summary>
background cascading deletion
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In </span><i>_____</i><span style="color: rgb(34, 34, 34);">, the root object first enters a "deletion in progress" state.&nbsp;</span>Once the "deletion in progress" state is set, the garbage collector deletes the object's dependents. Once the garbage collector has deleted all dependents,&nbsp;it deletes the owner object.</b>
</summary>
foreground cascading deletion
</details>

<details>
<summary>
<b>To control the cascading deletion policy, set the <font face="monospace">_____&nbsp;</font>field on the <font face="monospace">_____&nbsp;</font>argument when deleting an Object.&nbsp;</b>
</summary>
<code>propagationPolicy</code>&nbsp;
<code>deleteOptions</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">priority</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ is a non-namespaced object that defines a mapping from a priority class name to the integer value of the priority.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PriorityClass</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A</span><span style="color: rgb(34, 34, 34);">&nbsp;data science workload</span><span style="color: rgb(34, 34, 34);">&nbsp;may need to be prioritized above others, though without discarding existing work via pre-emption. To ensure this job begins once cluster resources become free, you could set...</span></b>
</summary>
PreemptionPolicy: Never
</details>

<details>
<summary>
<b>Identical Pods in a deployment are referred to as...</b>
</summary>
Replicas
</details>

<details>
<summary>
<b>_____ optimize a given metric (e.g. CPU utilization) across a set of Pods. They increase or decrease the number of replicas to achieve it.</b>
</summary>
Horizontal Pod Autoscalers (HPA)
</details>

<details>
<summary>
<b>A pod's only container exits with&nbsp;<b>success</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>Always?</b></b>
</summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays <b>Running</b>.
</details>

<details>
<summary>
<b>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>Always</b>?</b>
</summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PodPreset</span>
</details>

<details>
<summary>
<b>From one container, how could you view processes in other containers?</b>
</summary>
Enable process namespace sharing
</details>

<details>
<summary>
<b>_____ restrict the scheduler’s freedom, trading off one application against another.&nbsp;</b>
</summary>
Pod affinities
</details>

<details>
<summary>
<b>Do pods run a single container each?</b>
</summary>
Not necessarily. They can run multiple containers.
</details>

<details>
<summary>
<b>Do Pods each have a unique IP address?</b>
</summary>
Yes, for each address family
</details>

<details>
<summary>
<b><b>Failed </b>phase</b>
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Unknown </b>phase</b>
</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
</details>

<details>
<summary>
<b>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</b>
</summary>
a timestamp for when the Pod last transitioned from one status to another.
</details>

<details>
<summary>
<b>The three possible values for the&nbsp;<b>status</b>&nbsp;Pod condition field are...</b>
</summary>
<b>"True"</b>
<b>
</b><b>"False"</b><b>
</b>"<b>Unknown"</b>
</details>

<details>
<summary>
<b>A probe can have one of three results:</b>
</summary>
<b>Success</b>The Container passed the diagnostic
<b>
</b><b>Failure</b>The Container failed the diagnostic<b>
</b><b>Unknown</b>The diagnostic failed, so no action should be taken
</details>

<details>
<summary>
<b>If a livenessProbe fails, the container...</b>
</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
</details>

<details>
<summary>
<b>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe
What will be the state of each probe of the container?</b>
</summary>
<b>Success </b>on all of them
</details>

<details>
<summary>
<b>readinessProbe indicates whether...</b>
</summary>
a container is ready to service requests.
</details>

<details>
<summary>
<b>A container's default readiness state before the initial delay is...</b>
</summary>
Failure
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Do you still need a livenessProbe?</span></b>
</summary>
Not necessarily.&nbsp;
<span style="color: rgb(34, 34, 34);">The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;</span><code>restartPolicy</code><span style="color: rgb(34, 34, 34);">.</span>
</details>

<details>
<summary>
<b>A container is in the <b>_____&nbsp;</b>state when it has successfully or unsuccessfully completed execution.</b>
</summary>
Terminated
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Inject extra feedback or signals into PodStatus via...</span></b>
</summary>
<b>Pod readiness</b>
</details>

<details>
<summary>
<b>Default restartPolicy is...</b>
</summary>
Always
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at 5 minutes, and is reset after ten minutes of successful execution.</span></b>
</summary>
exponential back-off
</details>

<details>
<summary>
<b>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy </b>is <b>Never</b>?</b>
</summary>
Pod phase becomes Failed.
</details>

<details>
<summary>
<b>What applies Pod Presets to incoming pod creation requests?</b>
</summary>
PodPreset admission controller
</details>

<details>
<summary>
<b>The degree to which Pods may be unevenly distributed, i.e. t<span style="color: rgb(34, 34, 34);">he maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type is called...</span></b>
</summary>
<strong>maxSkew</strong>
</details>

<details>
<summary>
<b><b>whenUnsatisfiable </b>possible values:</b>
</summary>
<b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A Deployment&nbsp;</span><span style="color: rgb(34, 34, 34);">is supposed to have 5 pods at any given time, with</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">If a PodDisruptionBudget allows for there to be 4 at a time, then how many pods at a time are allowed to be voluntarily disrupted by the Eviction API?</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">One</span>
</details>

<details>
<summary>
<b>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring. Do involuntary disruptions count against the budget?</b>
</summary>
No
</details>

<details>
<summary>
<b>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</b>
</summary>
<b>No!&nbsp;</b><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A temporary ephemeral container is ran in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish user-initiated actions such as..</span></b>
</summary>
Troubleshooting and inspecting services
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">To troubleshoot a hard-to-reproduce bug, you might need to inspect the state of an existing Pod and its containers, or run some arbitrary commands. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">inside an existing Pod.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container</span>
</details>

<details>
<summary>
<b>Do ephemeral containers have guaranteed resources?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</b>
</summary>
process namespace sharing
</details>

<details>
<summary>
<b>When deleting a DaemonSet with kubectl, you can specify the flag _____, then the Pods will remain on the nodes.&nbsp;</b>
</summary>
--cascade=false
</details>

<details>
<summary>
<b>Given that you can start daemon processes on a node directly via systemd, why use a DaemonSet?</b>
</summary>
<ul><li>Ability to monitor and manage logs for daemons in the same way as applications.</li><li>Same config language and tools (e.g. Pod templates,&nbsp;<code>kubectl</code>) for daemons and applications.</li><li>Running daemons in containers with resource limits increases isolation between daemons from app containers. However, this can also be accomplished by running the daemons in a container but not in a Pod (e.g. start directly via Docker).</li></ul>
</details>

<details>
<summary>
<b>If you delete an object without deleting its dependents automatically, the dependents are said to become&nbsp;<i>_____</i></b>
</summary>
orphaned
</details>

<details>
<summary>
<b>Cascading deletion types</b>
</summary>
"Orphan", "Foreground", or "Background"
</details>

<details>
<summary>
<b>PodPresets cannot be used to override a Pod’s own configuration, only to fill in settings which the Pod itself _____</b>
</summary>
&nbsp;hasn't specified.
</details>

<details>
<summary>
<b>_____ allow you to schedule one copy of a Pod on every node (for example, a logging agent).</b>
</summary>
DaemonSets
</details>

<details>
<summary>
<b>_____ can inject bits of common configuration into all selected Pods at creation time. For example, you could use it to mount a particular Volume on all matching Pods.</b>
</summary>
PodPresets&nbsp;
</details>

<details>
<summary>
<b>_____ start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.</b>
</summary>
StatefulSets&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A quorum-based application must ensure that the number of running replicas is never brought below the minimum required for a quorum. This can be achieved with a _____</span></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b>A pod represents _____ running in your cluster.</b>
</summary>
Processes
</details>

<details>
<summary>
<b>In terms of Docker constructs, a Pod is modelled as a group of Docker containers with shared _____ and shared _____</b>
</summary>
namespaces
filesystem volumes
</details>

<details>
<summary>
<b>A container can be set to run in privileged mode to allow Linux capabilities inside the container, such as...</b>
</summary>
device accessvolume plugin developmentnetwork plugin development and stack manipulation
</details>

<details>
<summary>
<b><table><tbody><tr><td>A Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created, either still being scheduled or download images. This describes a Pod's _____ phase.</td></tr></tbody></table></b>
</summary>
Pending
</details>

<details>
<summary>
<b><b>Succeeded </b>phase</b>
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b>The <b>lastProbeTime</b>&nbsp;condition field provides...</b>
</summary>
A timestamp for when the Pod condition was last probed.
</details>

<details>
<summary>
<b>The <b>message&nbsp;</b>condition field provides...</b>
</summary>
a human-readable message indicating details about the transition from one status to another.
</details>

<details>
<summary>
<b>A livenessProbe indicates whether a container is...</b>
</summary>
running
</details>

<details>
<summary>
<b>startupProbe indicates whether...</b>
</summary>
the application in the container has started.
</details>

<details>
<summary>
<b>All other probes are disabled until _____ succeeds.</b>
</summary>
startupProbe
</details>

<details>
<summary>
<b>A Pod should only be sent traffic when a probe succeeds. What can achieve this?</b>
</summary>
readinessProbe
</details>

<details>
<summary>
<b>A container is <b>_____&nbsp;</b>when it is neither&nbsp;<b>Running&nbsp;</b>or&nbsp;<b>Terminated</b>. It is likely pulling images, applying secrets etc.</b>
</summary>
Waiting
</details>

<details>
<summary>
<b>A container is in the <b>_____&nbsp;</b>state when it is executing without issues.</b>
</summary>
Running
</details>

<details>
<summary>
<b>To tell why a container is in <b>Terminated </b>state, check its state's&nbsp;<b>_____&nbsp;</b>and&nbsp;<b>_____&nbsp;</b>fields.</b>
</summary>
Reason and Exit Code
</details>

<details>
<summary>
<b>The _____ hook is executed before a container enters Terminated state.</b>
</summary>
preStop
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of the .status._____ fields for the Pod.&nbsp;</span>If such a field isn't found, the status of the condition defaults to&nbsp;<b>"False"</b></b>
</summary>
conditions
</details>

<details>
<summary>
<b><b>restartPolicy </b>possible values are...</b>
</summary>
Always
Never
OnFailure
</details>

<details>
<summary>
<b>Does a Pod's <b>restartPolicy </b>apply to all its containers?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b>A pod's only container exits with <b>success</b>. What happens if the&nbsp;<b>restartPolicy </b>is <b>Never?</b></b>
</summary>
Pod&nbsp;<code>phase</code>&nbsp;becomes&nbsp;<b>Succeeded</b>.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></b>
</summary>
creation time
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies their _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can use </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;to control&nbsp;</span><span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains&nbsp;</span><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains).</span></b>
</summary>
topology spread constraints
</details>

<details>
<summary>
<b>You have a 4-node cluster with the following labels:<pre><code>NAME    STATUS   ROLES    AGE     VERSION   LABELS
node1   Ready    &lt;none&gt;   4m26s   v1.16.0   node=node1,zone=zoneA
node2   Ready    &lt;none&gt;   3m58s   v1.16.0   node=node2,zone=zoneA
node3   Ready    &lt;none&gt;   3m17s   v1.16.0   node=node3,zone=zoneB
node4   Ready    &lt;none&gt;   2m43s   v1.16.0   node=node4,zone=zoneB</code></pre>What would the cluster logically look like?</b>
</summary>
<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the topology spread constraint is indicated in the _____ field.</span></b>
</summary>
<strong>whenUnsatisfiable</strong>
</details>

<details>
<summary>
<b>Does deleting deployments or pods bypass PodDisruptionBudgets?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></b>
</summary>
replicas
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b>Will an ephemeral container ever be automatically restarted?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____ indicates the importance of a Pod relative to other Pods.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Priority</span>
</details>

<details>
<summary>
<b>A malicious user could create Pods at the highest possible priorities, causing other Pods to be evicted/not get scheduled. An administrator can use _____ to prevent users from creating pods at high priorities.</b>
</summary>
ResourceQuota
</details>

<details>
<summary>
<b>Critical pods rely on scheduler _____ to be scheduled when a cluster is under resource pressure.</b>
</summary>
preemption
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field indicates that the value of this PriorityClass should be used for Pods without a&nbsp;</span><code>priorityClassName</code><span style="color: rgb(34, 34, 34);">.&nbsp;</span><span style="color: rgb(34, 34, 34);">Only one such PriorityClass </span><span style="color: rgb(34, 34, 34);">can exist in the system.</span></b>
</summary>
<code>globalDefault</code>
</details>

<details>
<summary>
<b>Pods with PreemptionPolicy:<font face="monospace">_____</font>&nbsp;will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. It will stay in the scheduling queue, until sufficient resources are free.&nbsp;</b>
</summary>
Never
</details>

<details>
<summary>
<b><code>PreemptionPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;defaults to&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).&nbsp;</span></b>
</summary>
PreemptLowerPriority
</details>

<details>
<summary>
<b>_____ repel other Pods instead of attracting. Ex.: One to replicas of the same Pod can help spread your replicas evenly across the cluster.</b>
</summary>
anti-affinity
</details>

<details>
<summary>
<b>A pod's only container exits with&nbsp;<b>success</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>OnFailure?</b></b>
</summary>
Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.
</details>

<details>
<summary>
<b>A pod's only container exits with&nbsp;<b>failure</b>. What happens if the&nbsp;<b>restartPolicy&nbsp;</b>is&nbsp;<b>OnFailure</b>?</b>
</summary>
Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total. This can be achieved via a _____</span></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b>If non-preempting pods cannot be scheduled at a given time, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them. This is because non-preempting pods are subject to scheduler...</b>
</summary>
back-off
</details>

