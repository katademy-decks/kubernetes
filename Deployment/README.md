# Deployment 

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
<b><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></b>
</summary>
<b>Deployments&nbsp;</b>or<b> Replicasets </b>-<span style="color: rgb(34, 34, 34);">&nbsp;workload objects that provide a set of stateless replicas.</span>
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

