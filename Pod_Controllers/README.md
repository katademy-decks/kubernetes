# Pod_Controllers 

<details>
<summary>
<b>Kubernetes replication controller ensures</b>
</summary>
a specific number of pod replicas are running at any one time across nodes
</details>

<details>
<summary>
<b>what is rolling deployment?</b>
</summary>
approach when you deploy your containers to production hosts one at a time, so your app keeps running.Centurion can do this
</details>

<details>
<summary>
<b>The name of the Kubernetes Controller that provides declarative updates for pods.</b>
</summary>
Deployments
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">ensures that all (or some) Nodes run a copy of a Pod.</span></b>
</summary>
DaemonSet
</details>

<details>
<summary>
<b>Kubernetes deployments can be in what states?&nbsp;</b>
</summary>
1.&nbsp;<b>Progressing</b>, which means the deployment is in the process of performing a task&nbsp;
2.&nbsp;<b>Completed</b>, which means the rollout of containers is complete and all pods are running the latest version of containers&nbsp;
3.&nbsp;<b>Failed</b>, which indicates the deployment process encountered a problem it could not recover from&nbsp;&nbsp;

<img src="paste-b161711b323beee4f9321701871a89dbe94c759c.jpg">
<img src="paste-eb67b2c5aa380b7fa66366a34219cd767c81a081.jpg">
<img src="paste-3b99c3b118c2e59529bf12a6a554aa2c5c5bab73.jpg">
</details>

<details>
<summary>
<b>To which entity is this description reffering to?

A Kubernetes&nbsp;<b>Controller&nbsp;</b>which ensures that all (or some)&nbsp;<b>Nodes run a copy of a Pod&nbsp;</b>- thus allowing for node management.</b>
</summary>
DaemonSet

<img src="paste-71933616ad20fe752807b7c64a8363b0d177838e.jpg">
</details>

<details>
<summary>
<b>Explain what DaemonSet and ReplicaSet have in common (and what are the differences)</b>
</summary>
They are both Kubernetes Controllers and they are both related to count of pods inside the cluster.
<b>
ReplicaSet </b>makes sure that given amount of pods is always running in the cluster (<b>doesn't</b> matter in which worker node they are running!)<img src="paste-3dfda59e415fbe71f6a599a82a877ec60953f322.jpg">

<div style="display: inline !important;"><b>DaemonSet </b>makes sure that all (or selected) nodes have a replica of given pod.
In most use cases, the number of nodes will be equal with number of pods<img src="paste-41a44af9a7651900a5b65dbf3ba95a1f3fa4eb3e.jpg">
</details>

<details>
<summary>
<b>Is it possible to run DaemonSet pods on only some nodes?</b>
</summary>
Yes - with taints and affinities
</details>

<details>
<summary>
<b>What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</b>
</summary>
These pods will be garbage collected (deleted) as well<b><img src="lFn2VhS56EQ5e5HzPHY0ouWasNdxi6-R2XEOtnqIpKDTocCA4l-Sg6AfbKXHH9WIS1a8EMnYYEOiGyGJFioK-9qIZIH3sduMAborO6gXiCHw1Umz7OniapkRpRZdEZfQbEXv.png"></b>
</details>

<details>
<summary>
<b>What will happen to ReplicaSet pods inside a node when that node gets deleted?</b>
</summary>
These pods will be replaced on another node(s)

<img src="paste-69330a78781544cb8771f0f33692134d36fa2003.jpg">
</details>

<details>
<summary>
<b>cloudnatived/demo:hello deployment spec</b>
</summary>
spec:
 &nbsp;containers:
 &nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello
 &nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;- containerPort: 8888
</details>

<details>
<summary>
<b>What is DaemonSet?</b>
</summary>
A Kubernetes&nbsp;<b>Controller&nbsp;</b>which ensures that all (or some)&nbsp;<b>Nodes run a copy of a Pod.</b>

<img src="paste-b232887ca039d4beaf429a411e14fa6b3a83a025.jpg">
<img src="paste-29aacf46a4806c2486da42a774bf5401c35eea64.jpg"><img src="paste-1542ce24313150291f3adf83860cdf110447b2b4.jpg">


* It runs one instance on *NODE*
* Kubernetes DaemonSets run a&nbsp;<em>daemon</em>&nbsp;container on each node in the cluster.
* The term&nbsp;<em>daemon</em>&nbsp;traditionally refers to long-running background processes on a server that handle things like logging, so by analogy,&nbsp;
</details>

<details>
<summary>
<b>What is&nbsp;Deployments?</b>
</summary>
* Supervisor program, which continually checks that the container is running, and if it ever stops, starts it again immediately.* On traditional servers, you can use a tool like&nbsp;systemd,&nbsp;runit, or&nbsp;supervisord&nbsp;to do this; On Kubernetes, it is Deployment
* Kubernetes&nbsp;creates a corresponding Deployment object for each pods&nbsp; * Deployment records some information about the program:&nbsp;&nbsp; * Name of the container image&nbsp; *&nbsp;The number of replicas you want to run&nbsp; * Whatever else it needs to know to start the container.
</details>

<details>
<summary>
<b>Deployment, Controller with replicaset</b>
</summary>
* Deployment doesn’t manage replicas directly: instead, it automatically creates an associated object called a ReplicaSet, which handles that. We’ll talk more about ReplicaSets in a moment in&nbsp;“ReplicaSets”
* Working together with the&nbsp;Deployment resource is a kind of&nbsp;Kubernetes object called a&nbsp;<em>controller</em>. Controllers watch the resources they’re responsible for, making sure they’re present and working. If a given Deployment isn’t running enough replicas, for whatever reason, the controller will create some new ones.
</details>

<details>
<summary>
<b>StatefulSets</b>
</summary>
*&nbsp;Ability to start and stop Pods in a specific sequence.
* Manages disk storage for their Pods, using a VolumeClaimTemplate object that automatically creates a PersistentVolumeClaim* Each&nbsp;replica in a StatefulSet must be running and ready before Kubernetes starts the&nbsp;next one, and similarly when the StatefulSet is terminated, the replicas will be shut down in reverse order, waiting for each Pod to finish before moving on to the next.
</details>

<details>
<summary>
<b>deployment.spec.replicas</b>
</summary>
Numer of desired pods
</details>

<details>
<summary>
<b>deployment.spec.revisionHistoryLimit</b>
</summary>
Number of old ReplicaSets to retain for rollback
</details>

<details>
<summary>
<b>deployment.spec.selector</b>
</summary>
Label selector for pods
Must match pod template labels
</details>

<details>
<summary>
<b>deployment.spec.strategy</b>
</summary>
<b>Recreate</b><b>
</b><b>RollingUpdate</b>maxSurge: max number / percentage of pods that can be scheduled above the desired number of pods
maxUnavailable: max number of pods that can be unavailable during the update
</details>

<details>
<summary>
<b>StatefulSet is the workload API object used to manage _____</b>
</summary>
stateful applications
</details>

<details>
<summary>
<b>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about _____&nbsp;of these Pods</b>
</summary>
the ordering and uniqueness
</details>

<details>
<summary>
<b>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</b>
</summary>
sticky identity
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSet pods are created from the same spec, but are _____</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Each has a persistent identifier that it maintains across any rescheduling.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">interchangeable</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____ as part of the solution. Although individual Pods in a _____ are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
</details>

<details>
<summary>
<b>An application requires several of the following:<ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>Which workload object could work best?</b>
</summary>
StatefulSet
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></b>
</summary>
<b>Deployments&nbsp;</b>or<b> Replicasets </b>-<span style="color: rgb(34, 34, 34);">&nbsp;workload objects that provide a set of stateless replicas.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Deleting and/or scaling a StatefulSet down will </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;the volumes associated with the StatefulSet.</span></b>
</summary>
<em>not</em><span style="color: rgb(34, 34, 34);">&nbsp;delete</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSets currently require a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods. You are responsible for creating it.</span></b>
</summary>
<a href="https://kubernetes.io/docs/concepts/services-networking/service/#headless-services">Headless Service</a>
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
<b><span style="color: rgb(34, 34, 34);">When using&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#rolling-updates">Rolling Updates</a><span style="color: rgb(34, 34, 34);">&nbsp;with the default&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#pod-management-policies">Pod Management Policy</a><span style="color: rgb(34, 34, 34);">&nbsp;(</span><code>OrderedReady</code><span style="color: rgb(34, 34, 34);">), it's possible to get into a broken state that requires _____&nbsp;to repair</span></b>
</summary>
<a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#forced-rollback">manual intervention</a>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A ReplicaSet is linked to its Pods via their _____ field.</span><span style="color: rgb(34, 34, 34);">&nbsp;It's through this link that the ReplicaSet knows of the state of the Pods it is maintaining and plans accordingly.</span></b>
</summary>
metadata.ownerReferences
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A ReplicaSet identifies new Pods to acquire by using its _____.&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;If there is a Pod that has no OwnerReference or the Ow</span>nerReference is not a&nbsp;<a href="https://kubernetes.io/docs/concepts/architecture/controller/">Controller</a>&nbsp;an<span style="color: rgb(34, 34, 34);">d the _____ matches, it will be immediately acquired by said ReplicaSet.</span></b>
</summary>
selector
</details>

<details>
<summary>
<b>_____&nbsp;<span style="color: rgb(34, 34, 34);">is an object which can own ReplicaSets and update them and their Pods via declarative, server-side rolling updates.</span></b>
</summary>
Deployment
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. This workload behaviour might be the work of a _____</span></b>
</summary>
DaemonSet
</details>

<details>
<summary>
<b>Is running a cluster storage daemon on every node a valid DaemonSet use case?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Is running a logs collection daemon on every node a valid DaemonSet use case?</b>
</summary>
Yes
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
<b>Some possible patterns for communicating with Pods in a DaemonSet are:<ul><li><strong>Push</strong>: Pods in the DaemonSet are configured to send updates to another service, such as a stats database. They do not have clients.</li><li><strong>NodeIP and Known Port</strong>: Pods in the DaemonSet can use a&nbsp;<code>hostPort</code>, so that the pods are reachable via the node IPs. Clients know the list of node IPs somehow, and know the port by convention.</li><li><strong>DNS</strong>: Create a&nbsp;<a href="https://kubernetes.io/docs/concepts/services-networking/service/#headless-services">headless service</a>&nbsp;with the same pod selector, and then discover DaemonSets using the&nbsp;<code>endpoints</code>&nbsp;resource or retrieve multiple A records from DNS.</li><li><strong>Service</strong>: Create a service with the same Pod selector, and use the service to reach a daemon on a random node. (No way to reach specific node.)</li></ul></b>
</summary>
todo
</details>

<details>
<summary>
<b>Can you perform a rolling update on a DaemonSet?</b>
</summary>
Yes
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
<b>When deleting a DaemonSet, you can specify the flag _____ with kubectl, then the Pods will be left on the nodes.&nbsp;<span style="color: rgb(34, 34, 34);">If you subsequently create a new DaemonSet with the same selector, the new DaemonSet adopts the existing Pods.</span></b>
</summary>
--cascade=false
</details>

<details>
<summary>
<b>You can run daemon processes by directly starting them on a node via systemd. Why use a DaemonSet then?</b>
</summary>
<ul><li>Ability to monitor and manage logs for daemons in the same way as applications.</li><li>Same config language and tools (e.g. Pod templates,&nbsp;<code>kubectl</code>) for daemons and applications.</li><li>Running daemons in containers with resource limits increases isolation between daemons from app containers. However, this can also be accomplished by running the daemons in a container but not in a Pod (e.g. start directly via Docker).</li></ul>
</details>

<details>
<summary>
<b>DaemonSets are similar to Deployments in that they both...</b>
</summary>
<span style="color: rgb(34, 34, 34);">create Pods, and those Pods have processes which are not expected to terminate (e.g. web servers, storage servers).</span>
</details>

<details>
<summary>
<b>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</b>
</summary>
an owner
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Owned objects are called&nbsp;</span><em>dependents</em><span style="color: rgb(34, 34, 34);">&nbsp;of the owner object. Every dependent object has a&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;field that points to the owning object. The field is&nbsp;</span><span style="color: rgb(34, 34, 34);">automatically set </span><span style="color: rgb(34, 34, 34);">for objects created or adopted by ReplicationController, ReplicaSet, StatefulSet, DaemonSet, Deployment, Job and CronJob.</span></b>
</summary>
metadata.ownerReferences
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Can you specify relationships between owners and dependents manually?</span></b>
</summary>
Yes - by&nbsp;setting the&nbsp;ownerReference&nbsp;field.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called <i>_____</i></span></b>
</summary>
cascading deletion
</details>

<details>
<summary>
<b>If you delete an object without deleting its dependents automatically, the dependents are said to be <i>_____</i></b>
</summary>
orphaned
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
<b>To control the cascading deletion policy, set the&nbsp;<code>propagationPolicy</code>&nbsp;field on the&nbsp;<code>deleteOptions</code>&nbsp;argument when deleting an Object. Possible values include "Orphan", "Foreground", or "Background".</b>
</summary>
TODO
</details>

