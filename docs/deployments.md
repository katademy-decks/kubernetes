<details>
<summary>Jobs on a repeating schedule are called _____</summary>
CronJobs
<br></details>

<details>
<summary>One CronJob object is like one line of a _____ file. It runs a job periodically on a given schedule, written in Cron format.</summary>
crontab
<br></details>

<details>
<summary>Can CronJobs be used for running backups?</summary>
Yes
<br></details>

<details>
<summary>Because it is not guaranteed only one job will launch per execution time of its schedule, Jobs should be&nbsp;<i>_____&nbsp;</i></summary>
idempotent
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A CronJob is counted as _____ if it&nbsp;</span><span style="color: rgb(34, 34, 34);">has failed to be created at its scheduled time.</span></summary>
missed
<br></details>

<details>
<summary>A job's default parallelism value is 1.<span style="color: rgb(34, 34, 34);">&nbsp;If it is set to _____ instead, then the Job&nbsp;</span><span style="color: rgb(34, 34, 34);">is paused until it is increased.</span></summary>
0
<br></details>

<details>
<summary>A job's _____ is&nbsp;<span style="color: rgb(34, 34, 34);">the number of Job pods running at any instant.</span></summary>
parallelism
<br></details>

<details>
<summary>A Kubernetes&nbsp;resource which ensures that all (or some)&nbsp;Nodes run a copy of a Pod is the _____</summary>
DaemonSet
<br></details>

<details>
<summary>What will happen to ReplicaSet pods inside a node when that node gets deleted?</summary>
These pods will be replaced on another node, or nodes.
<br></details>

<details>
<summary>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</summary>
sticky identity
<br></details>

<details>
<summary>An application requires several of the following:<ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>Which workload object could work best?</summary>
StatefulSet
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Will deleting or scaling a StatefulSet down also delete&nbsp;</span><span style="color: rgb(34, 34, 34);">the volumes associated with it?</span></summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet is linked to its Pods via their _____ field.</span><span style="color: rgb(34, 34, 34);">&nbsp;It's through this link that the ReplicaSet knows of the state of the Pods it is maintaining and plans accordingly.</span></summary>
metadata.ownerReferences
<br></details>

<details>
<summary>_____&nbsp;<span style="color: rgb(34, 34, 34);">is an object which can own ReplicaSets and update them and their Pods via declarative, server-side rolling updates.</span></summary>
Deployment
<br></details>

<details>
<summary>Is running a logs collection daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary>Can you perform a rolling update on a DaemonSet?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ provides a TTL (time to live) mechanism to limit the lifetime of resource objects that have finished execution.</span></summary>
<span style="color: rgb(34, 34, 34);">TTL controller</span>
<br></details>

<details>
<summary>All CronJob schedules are based on the timezone of _____</summary>
the <b>kube-controller-manager</b>.
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a CronJob's&nbsp;</span><code>concurrencyPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;is set to&nbsp;</span><code>Forbid,</code><span style="color: rgb(34, 34, 34);">&nbsp;and it attempted to be scheduled when there was a previous schedule still running, then it would count as _____.</span></summary>
missed
<br></details>

<details>
<summary>The number of old ReplicaSets to retain for rollback is defined in a deployment's .spec._____</summary>
revisionHistoryLimit
<br></details>

<details>
<summary>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about the _____ and _____of these Pods</summary>
ordering and uniqueness
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, you should deploy your application using a _____ - a&nbsp;</span><span style="color: rgb(34, 34, 34);">workload object that provides a set of stateless replicas.</span></summary>
Deployment
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet identifies new Pods to acquire by using its _____.&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;If there is a Pod that has no OwnerReference or the Ow</span>nerReference is not a&nbsp;<a href="https://kubernetes.io/docs/concepts/architecture/controller/">Controller</a>&nbsp;an<span style="color: rgb(34, 34, 34);">d the _____ matches, it will be immediately acquired by said ReplicaSet.</span></summary>
selector
<br></details>

<details>
<summary>Is running a cluster storage daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary>Pods waiting to be scheduled are usually created in <b>Pending </b>state. Are DaemonSet pods created in <b>Pending </b>state?</summary>
No - it is an inconsistency due to being scheduled by the DaemonSet controller.
<br></details>

<details>
<summary>When <b>Pod preemption</b> is enabled, does the DaemonSet controller consider <b>pod priority</b> and <b>preemption </b>when making scheduling decisions?</summary>
No - <b>Pod preemption</b> is handled by the <b>default scheduler</b>, DaemonSet pods are scheduled by the <b>DaemonSet controller</b>.
<br></details>

<details>
<summary>If node labels are changed, the DaemonSet will _____ Pods to newly matching nodes.</summary>
Add
<br></details>

<details>
<summary>If node labels are changed, the DaemonSet will _____ Pods from newly not-matching nodes.</summary>
Delete
<br></details>

<details>
<summary>Can CronJobs be used for sending e-mails?</summary>
Yes
<br></details>

<details>
<summary>The Job Controller counts how many jobs had missed in the last X seconds, but only if a CronJob's _____ field<b>&nbsp;</b>is set.</summary>
startingDeadlineSeconds&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ creates one or more Pods and ensures that a specified number of them successfully terminate.&nbsp;</span><span style="color: rgb(34, 34, 34);">As pods successfully complete, it tracks the successful completions until a certain number of successful completions is reached.</span></summary>
<span style="color: rgb(34, 34, 34);">Job</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">For </span>a&nbsp;fixed completion count<span style="color: rgb(34, 34, 34);">&nbsp;Job, you should set its .spec._____ field</span></summary>
completions
<br></details>

<details>
<summary>A _____&nbsp;ensures that all (or some) Nodes run a copy of a Pod.</summary>
DaemonSet
<br></details>

<details>
<summary>What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</summary>
These pods will be garbage collected
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____. Although its Pods are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
<br></details>

<details>
<summary>Is running a node monitoring daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Normally, the node that a Pod runs on is selected by the Kubernetes scheduler. However, DaemonSet pods are created and scheduled by _____ instead.</span></summary>
<span style="color: rgb(34, 34, 34);">the DaemonSet controller</span>
<br></details>

<details>
<summary>DaemonSets are similar to Deployments in that they both...</summary>
<span style="color: rgb(34, 34, 34);">create Pods, with processes which are not expected to terminate (web servers, storage servers etc).</span>
<br></details>

<details>
<summary>Every dependent (i.e. owned) object has a metadata._____&nbsp;field that points to the owning object. The owning object is usually a&nbsp;Job, CronJob,&nbsp;Deployment, DaemonSet,&nbsp;StatefulSet,&nbsp;ReplicationController, ReplicaSet.</summary>
ownerReferences
<br></details>

<details>
<summary>Identical Pods in a deployment are referred to as _____</summary>
Replicas
<br></details>

<details>
<summary>_____ run a Pod a specified number of times before completing. _____ run a Pod periodically at specified times.</summary>
Jobs
CronJobs
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Deployment&nbsp;</span><span style="color: rgb(34, 34, 34);">is supposed to have 5 pods at any given time, with</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">If a PodDisruptionBudget allows for there to be 4 at a time, then how many pods at a time are allowed to be voluntarily disrupted by the Eviction API?</span></summary>
<span style="color: rgb(34, 34, 34);">One</span>
<br></details>

<details>
<summary>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</summary>
<b>No!&nbsp;</b><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec.</span>
<br></details>

<details>
<summary>When deleting a DaemonSet with kubectl, you can specify the flag _____, then the Pods will remain on the nodes.&nbsp;</summary>
--cascade=false
<br></details>

<details>
<summary>Given that you can start daemon processes on a node directly via systemd, why use a DaemonSet?</summary>
<ul><li>Ability to monitor and manage logs for daemons in the same way as applications.</li><li>Same config language and tools (e.g. Pod templates,&nbsp;<code>kubectl</code>) for daemons and applications.</li><li>Running daemons in containers with resource limits increases isolation between daemons from app containers. However, this can also be accomplished by running the daemons in a container but not in a Pod (e.g. start directly via Docker).</li></ul>
<br></details>

<details>
<summary>_____ allow you to schedule one copy of a Pod on every node (for example, a logging agent).</summary>
DaemonSets
<br></details>

<details>
<summary>_____ start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.</summary>
StatefulSets&nbsp;
<br></details>

<details>
<summary>Does deleting deployments or pods bypass PodDisruptionBudgets?</summary>
Yes
<br></details>

<details>
<summary>Minimum time in seconds for which a new pod should be ready to be considered available is defined in deployment.spec._____</summary>
minReadySeconds
<br></details>

<details>
<summary>The count of hash collisions for a deployment is stored in its deployment.deploymentstatus._____ status field. It is used for collision avoidance.</summary>
collisionCount
<br></details>

<details>
<summary>_____ differ from Deployments in that Pods are created sequentially, each given an incrementing index number.&nbsp;</summary>
StatefulSets
<br></details>