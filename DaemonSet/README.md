# DaemonSet 

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">ensures that all (or some) Nodes run a copy of a Pod.</span></b>
</summary>
DaemonSet
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

