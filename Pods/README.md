# Pods 

<details>
<summary>
<b>What’s a <b>Pod</b></b>
</summary>
A&nbsp;<b>Pod </b>is a group of one or more&nbsp;containers with shared storage/network, and a specification for how to run the containers.

<b><img src="m6OgY8HdeAOI59RmeT0Ue6ortvnFbTmq9hg2duJnAKD0WYGQpN1xDCWQ9_fNi3fbYYd4c0FESi-jtoTt2B4W7gsYqaYD2mrHIqt9T8OEItsIIJfKB_5cHdhvG5ULq_TOqCI1.png"></b>
</details>

<details>
<summary>
<b>A Kubernetes concept that represents the smallest unit of deployment.</b>
</summary>
Pod
</details>

<details>
<summary>
<b>Containers within a single {{c2::pod}} share {{c1::storage and network resources (IP address and port space)}}
<img src="paste-4a2866ebe8cac19809f8cc3915104dd1f2423b01.jpg"></b>
</summary>

</details>

<details>
<summary>
<b>How to set environment variablein k8s?</b>
</summary>
containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
 &nbsp;env:
 &nbsp;- name: GREETING
 &nbsp;&nbsp;&nbsp;value: "Hello from the environment"
</details>

<details>
<summary>
<b>Why not use pod affinities?</b>
</summary>
* Pod affinities restrict the scheduler’s freedom
*&nbsp;Trading off one application against another.&nbsp;
</details>

<details>
<summary>
<b>Why do you need&nbsp;Pod Controllers?</b>
</summary>
If the container exits for some reason, you have to manually restart it.
There’s only one replica of your container and no way to load-balance traffic across multiple replicas if you ran them manually.
If you want highly available replicas, you have to decide which nodes to run them on, and take care of keeping the cluster balanced.
When you update the container, you have to take care of stopping each running image in turn, pulling the new image and restarting it.
</details>

<details>
<summary>
<b>What are PodPresets? Example of PodPresets</b>
</summary>
PodPresets:<strong>
</strong>A&nbsp;Pod Preset&nbsp;is an API resource for injecting additional runtime requirements into a Pod at creation time. You use&nbsp;label selectors&nbsp;to specify the Pods to which a given Pod Preset applies.
<strong>
</strong><strong>
</strong><strong>Specific Example:</strong>
Specific Example:

1. Database Administrator provisions a MySQL service for their cluster.
2. Database Administrator creates secrets for the cluster containing the database name, username, and password.
3. Database Administrator creates a PodPreset defining the database &nbsp;&nbsp;port as an environment variable, as well as the secrets. See Examples below for various examples.
4. Developer of an application can now label their pod with the specified Selector the Database Administrator tells them, and consume the MySQL database without needing to know any of the details from step 2 and 3.
</details>

<details>
<summary>
<b>Can PodPresets override POD settings.</b>
</summary>
PodPresets can’t be used to override a Pod’s own configuration, only to fill in settings which the Pod itself doesn’t specify. A Pod can opt out of being modified by PodPresets altogether, by setting the annotation:podpreset.admission.kubernetes.io/exclude: "true"
</details>

<details>
<summary>
<b>Building Your Own Kubernetes Tools, How to list all the pods in your cluster using go?</b>
</summary>
Operators and Custom Resource Definitions (CRDs)

...
podList, err := clientset.CoreV1().Pods("").List(metav1.ListOptions{})
if err != nil {
 &nbsp;&nbsp;&nbsp;log.Fatal(err)
}
fmt.Println("There are", len(podList.Items), "pods in the cluster:")
for _, i := range podList.Items {
 &nbsp;&nbsp;&nbsp;fmt.Println(i.ObjectMeta.Name)
}
...
</details>

<details>
<summary>
<b>Everything about running Pod</b>
</summary>
Labels are key-value pairs that identify resources, and can be used with selectors to match a specified group of resources.

Node affinities attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.

While hard node affinities can block a Pod from running, soft node affinities are more like suggestions to the scheduler. You can combine multiple soft affinities with different weights.

Pod affinities express a preference for Pods to be scheduled on the same node as other Pods. For example, Pods that benefit from running on the same node can express that using a Pod affinity for each other.

Pod anti-affinities repel other Pods instead of attracting. For example, an anti-affinity to replicas of the same Pod can help spread your replicas evenly across the cluster.

Taints are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won’t be scheduled on tainted nodes.

Tolerations allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.

DaemonSets allow you to schedule one copy of a Pod on every node (for example, a logging agent).

StatefulSets start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.

Jobs run a Pod once (or a specified number of times) before completing. Similarly, Cronjobs run a Pod periodically at specified times.

Horizontal Pod Autoscalers watch a set of Pods, trying to optimize a given metric (such as CPU utilization). They increase or decrease the desired number of replicas to achieve the specified goal.

PodPresets can inject bits of common configuration into all selected Pods at creation time. For example, you could use a PodPreset to mount a particular Volume on all matching Pods.

Custom Resource Definitions (CRDs) allow you to create your own custom Kubernetes objects, to store any data you wish. Operators are Kubernetes client programs that can implement orchestration behavior for your specific application (for example, MySQL).

Ingress resources route requests to different services, depending on a set of rules, for example, matching parts of the request URL. They can also terminate TLS connections for your application.

Istio is a tool that provides advanced networking features for microservice applications and can be installed, like any Kubernetes application, using Helm.

Envoy provides more sophisticated load balancing features than standard cloud load balancers, as well as a service mesh facility.
</details>

<details>
<summary>
<b>containers.imagePullPolicy</b>
</summary>
Always
Never
IfNotPresent
</details>

<details>
<summary>
<b>containers.args</b>
</summary>
Arguments to the entrypoint
Default: the image's CMD line
<font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.command</b>
</summary>
Entrypoint array
Not executed in a shell
Default: the image's ENTRYPOINT
<font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.env</b>
</summary>
List of env vars
<font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.envFrom</b>
</summary>
List of sources to populate env vars
<font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.image</b>
</summary>
container image url
</details>

<details>
<summary>
<b>containers.lifecycle</b>
</summary>
Actions to take in response to lifecycle events<b>
</b><b>postStart</b>Called after a container is created
If it fails, container restarts according to restart policy<b>
</b><b>preStop</b>
Called before a container is terminated (not if it crashes/exits)
<font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.livenessProbe</b>
</summary>
Periodic probe of container liveness
Restart container if fails
httpGet: request to perform
failureThreshold: failures needed to mark probe failed
successThreshold: successes needed to mark probe succeeded
initialDelaySeconds: seconds before liveness probes begin
periodSeconds: how often to probe
</details>

<details>
<summary>
<b>containers.name</b>
</summary>
Unique name of the container
</details>

<details>
<summary>
<b>containers.ports</b>
</summary>
Ports to expose from container
name:
protocol:
containerPort: #
hostIP:
</details>

<details>
<summary>
<b>containers.readinessProbe</b>
</summary>
Periodic probe of container service readiness.
Container removed from svc endpoints if probe fails
httpGet: request to perform
failureThreshold: failures needed to mark probe failed
successThreshold: successes needed to mark probe succeeded
initialDelaySeconds: seconds before liveness probes begin
periodSeconds: how often to probe
</details>

<details>
<summary>
<b>containers.securityContext</b>
</summary>
Container's security config
runAsUser:
runAsGroup:&nbsp;
runAsNonRoot:
capabilities:

privileged:
procMount:
seLinuxOptions:
readOnlyRootFilesystem:
allowPrivilegeEscalation:
</details>

<details>
<summary>
<b>containers.workingDir</b>
</summary>
Container's working directory
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
<b>Are pods intended to survive through scheduling failures, node failures or other evictions?</b>
</summary>
No
</details>

<details>
<summary>
<b>How can any container in a pod enable privileged mode?</b>
</summary>
Using the <b>privileged</b>&nbsp;flag in the security context of the container spec.
</details>

<details>
<summary>
<b>Why would you allow a container to run in privileged mode?</b>
</summary>
to allow Linux capabilities inside the container.
-----
Ex.:
accessing devicesnetwork stack manipulationwriting network and volume plugins
</details>

<details>
<summary>
<b>The <b>phase </b>of a pod is...</b>
</summary>
A high-level summary of where the pod is in its lifecycle
</details>

<details>
<summary>
<b><b>Pending</b> phase</b>
</summary>
<table><tbody><tr><td>The Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created. This includes time before being scheduled as well as time spent downloading images over the network, which could take a while.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Running</b>&nbsp;phase</b>
</summary>
<table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Succeeded </b>phase</b>
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
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
<b>The <b>lastProbeTime</b>&nbsp;condition field provides...</b>
</summary>
A timestamp for when the Pod condition was last probed.
</details>

<details>
<summary>
<b>A pod represents _____ processes running in your cluster.</b>
</summary>
Processes
</details>

<details>
<summary>
<b>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</b>
</summary>
a timestamp for when the Pod last transitioned from one status to another.
</details>

<details>
<summary>
<b>A pod is the basic _____ unit of Kubernetes.</b>
</summary>
execution
</details>

<details>
<summary>
<b>The <b>message&nbsp;</b>condition field provides...</b>
</summary>
a human-readable message indicating details about the transition from one status to another.
</details>

<details>
<summary>
<b>A pod encapsulates an application's...</b>
</summary>
container
<hr>
execution options
<hr>
IP address
<hr>
storage resources
</details>

<details>
<summary>
<b>The <b>reason&nbsp;</b>condition field provides...</b>
</summary>
a unique, one-word reason for the condition's last transition.
</details>

<details>
<summary>
<b>Do pods run a single container each?</b>
</summary>
Not necessarily. They can run multiple containers.
</details>

<details>
<summary>
<b>The <b>status</b>&nbsp;condition field provides...</b>
</summary>
One of the following:<b>
</b><b>"True"</b><b>
</b><b>"False"</b><b>
</b>"<b>Unknown"</b>
</details>

<details>
<summary>
<b>Are containers in a Pod automatically co-located and co-scheduled on the <b>same</b> physical or virtual machine in the cluster?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>The <b>type</b>&nbsp;condition field provides...</b>
</summary>
One of the following:
<b>PodScheduled</b>Pod has been scheduled to a node<b>
</b><b>Ready</b>Pod is able to serve requests<b>
</b><b>Initialized</b>All init containers have started successfully<b>
</b><b>ContainersReady</b>All containers in the pod are ready
</details>

<details>
<summary>
<b>Can a pod's containers share resources, dependensies, communicate with each other and coordinate their lifecycle?</b>
</summary>
Yes
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
<b>Example sidecar container pattern diagram</b>
</summary>
<img src="pod.svg">
</details>

<details>
<summary>
<b>A livenessProbe indicates whether a container is...</b>
</summary>
running
</details>

<details>
<summary>
<b>Do Pods each have a unique IP address?</b>
</summary>
Yes, for each address family
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
<b>If the readinessProbe fails, what happens?</b>
</summary>
The <b>endpoints controlller</b> removes the <b>Pod's IP address</b> from the endpoints of all <b>Services </b>that match the Pod
</details>

<details>
<summary>
<b>A container's default readiness state before the initial delay is...</b>
</summary>
Failure
</details>

<details>
<summary>
<b>startupProbe indicates whether...</b>
</summary>
the application in the container has started.
</details>

<details>
<summary>
<b>A startupProbe is provided to a container
What happens to the other probes?</b>
</summary>
All other probes are disabled until startupProbe succeeds.
</details>

<details>
<summary>
<b>If the startupProbe fails, the container...</b>
</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
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
<b>A container should be killed or restarted if a probe fails. What can be done to achieve this?</b>
</summary>
1. Specify a <b>livenessProbe&nbsp;</b>
2. Add a <b>restartPolicy </b>of <b>Always </b>or <b>OnFailure</b>
</details>

<details>
<summary>
<b>A Pod should only be sent traffic when a probe succeeds. What can achieve this?</b>
</summary>
readinessProbe
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
<b>A container is <b>Waiting </b>when...</b>
</summary>
It is neither <b>Running </b>or <b>Terminated</b>
A <b>Waiting </b>container still runs operations like pulling images, applying Secrets etc.
</details>

<details>
<summary>
<b>How to tell why a container is in&nbsp;<b>Waiting </b>state?</b>
</summary>
Check the state's&nbsp;<b>Reason </b>field
</details>

<details>
<summary>
<b>A container is in the <b>Running </b>state when...</b>
</summary>
It is executing without issues.
</details>

<details>
<summary>
<b>Which hook is executed prior to a container entering its <b>Running </b>state?</b>
</summary>
postStart
</details>

<details>
<summary>
<b>A container is in the <b>Terminated </b>state when...</b>
</summary>
It has successfully or unsuccessfully completed execution.
</details>

<details>
<summary>
<b>How to tell why a container is in <b>Terminated </b>state?</b>
</summary>
Check the state's <b>Reason </b>and <b>Exit Code</b> fields.
</details>

<details>
<summary>
<b>Which hook is executed before a container enters Terminated state?</b>
</summary>
preStop
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Inject extra feedback or signals into PodStatus via...</span></b>
</summary>
<b>Pod readiness</b>
</details>

<details>
<summary>
<b>You can add <b>Pod readiness</b> into <b>PodStatus </b>by...</b>
</summary>
<b>readinessGates</b>
Add it into PodSpec to specify a list of extra conditions for the kubelet to evaluate
Ex.:
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span>...<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">readinessGates</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">conditionType</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"www.example.com/feature-1"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">conditions</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">type</span>:<span style="color: rgb(187, 187, 187);"> </span>Ready<span style="color: rgb(187, 187, 187);">                              </span><span style="color: rgb(0, 136, 0); font-style: italic;"># a built in PodCondition</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"False"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastProbeTime</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">null</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastTransitionTime</span>:<span style="color: rgb(187, 187, 187);"> </span>2018-01-01T00:00:00Z<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">type</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"www.example.com/feature-1"</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># an extra PodCondition</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"False"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastProbeTime</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">null</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastTransitionTime</span>:<span style="color: rgb(187, 187, 187);"> </span>2018-01-01T00:00:00Z<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containerStatuses</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">containerID</span>:<span style="color: rgb(187, 187, 187);"> </span>docker://abcd...<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">ready</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">true</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span>...</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of...</span></b>
</summary>
<b>status.condition</b> fields for the Pod
If such a field isn't found, the status of the condition defaults to <b>"False"</b>
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
<b>Default restartPolicy is...</b>
</summary>
Always
</details>

<details>
<summary>
<b>Does a Pod's <b>restartPolicy </b>apply to all its containers?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Once bound to a node, will a Pod ever rebound to another node?</b>
</summary>
No
</details>

<details>
<summary>
<b>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at _____ and is reset after ten minutes of successful execution.</span></b>
</summary>
exponential back-off
5 minutes
</details>

<details>
<summary>
<b>A pod has one container. The container exits with <b>success</b>.
What happens depending on each possible <b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li></ul>
</details>

<details>
<summary>
<b>A pod has one container. The container exits with&nbsp;<b>failure</b>.
What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>Pod is running and has two Containers. Container 1 exits with <b>failure</b>.
What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Do not restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li></ul><span style="color: rgb(34, 34, 34);">If Container 1 is not running, and Container 2 exits:</span><ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>Pod is running and has one Container. Container runs <b>out of memory </b>(and terminates in failure)
What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Log failure event; Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>Pod is running, and a disk dies.
What happens?</b>
</summary>
<ul><li>Kill all Containers.</li><li>Log appropriate event.</li><li>Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<b>Pod is running, and its node is segmented out.
What happens?</b>
</summary>
<ul><li>Node controller waits for timeout.</li><li>Node controller sets Pod&nbsp;<code>phase</code>&nbsp;to Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A PodPreset allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></b>
</summary>
creation time
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></b>
</summary>
label selectors
</details>

<details>
<summary>
<b>What applies Pod Presets to incoming pod creation requests?</b>
</summary>
PodPreset admission controller
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></b>
</summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies the _____</span></b>
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
<b>How to&nbsp;disable Pod Preset for a Specific Pod</b>
</summary>
<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">podpreset.admission.kubernetes.io/exclude: "true"</span><span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span>Add the above annotation in the Pod Spec<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can use&nbsp;</span><em>topology spread constraints</em><span style="color: rgb(34, 34, 34);">&nbsp;to control...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains.&nbsp;</span><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains)</span>
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
<b><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></b>
</summary>
node labels
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can define one or multiple _____&nbsp;</span>to instruct the kube-scheduler how to place each incoming Pod in relation to the existing Pods across your cluster.</b>
</summary>
<code>topologySpreadConstraint</code>
</details>

<details>
<summary>
<b><strong>maxSkew</strong><span style="color: rgb(34, 34, 34);">&nbsp;describes...</span></b>
</summary>
the degree to which Pods may be unevenly distributed.
<span style="color: rgb(34, 34, 34);">It's the maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type.</span>
<span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">It must be greater than zero.</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one <b>topologyKey </b>and have identical values for that label, the scheduler treats both Nodes as _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Being in the same topology.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">The scheduler tries to place a balanced number of Pods into each topology domain</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b><strong>whenUnsatisfiable</strong><span style="color: rgb(34, 34, 34);">&nbsp;indicates...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the spread constraint</span>
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
<b><span style="color: rgb(34, 34, 34);">Only the Pods holding the same _____ as the incoming Pod can be matching candidates</span></b>
</summary>
namespace
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Nodes without&nbsp;</span><code>topologySpreadConstraints[*].topologyKey</code><span style="color: rgb(34, 34, 34);">&nbsp;present will be...</span></b>
</summary>
<b>bypassed</b><b>
</b>This implies that:
<ol><li>the Pods located on those nodes do not impact&nbsp;<code>maxSkew</code>&nbsp;calculation - in the above example, suppose "node1" does not have label "zone", then the 2 Pods will be disregarded, hence the incomingPod will be scheduled into "zoneA".</li><li>the incoming Pod has no chances to be scheduled onto this kind of nodes - in the above example, suppose a "node5" carrying label&nbsp;<code>{zone-typo: zoneC}</code>&nbsp;joins the cluster, it will be bypassed due to the absence of label key "zone".</li></ol>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If the incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></b>
</summary>
bypassed
</details>

<details>
<summary>
<b><h2>Comparison of Topology with PodAffinity/PodAntiAffinity</h2>In Kubernetes, directives related to "Affinity" control how Pods are scheduled - more packed or more scattered.
<ul><li>For <font face="monospace">_____</font>, you can try to pack any number of Pods into qualifying topology domain(s)</li><li>For&nbsp;<font face="monospace">_____</font>, only one Pod can be scheduled into a single topology domain.</li></ul></b>
</summary>
PodAffinity
PodAntiAffinity
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">It is possible to set default topology spread constraints for a cluster.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Default topology spread constraints are applied to a Pod if, and only if:</span></b>
</summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
</details>

<details>
<summary>
<b>Does deleting deployments or pods bypass Pod Disruption Budgets?</b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Ex.:</span><span style="color: rgb(34, 34, 34);">A quorum-based application would like to ensure that the number of replicas running is never brought below the number needed for a quorum.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total.</span><span style="color: rgb(34, 34, 34);">
</span></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></b>
</summary>
replicas
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ADeployment has a&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">It is supposed to have 5 pods at any given time.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">If its PDB allows for there to be 4 at a time, then the Eviction API will allow voluntary disruption of how many pods at a time?</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">One</span>
</details>

<details>
<summary>
<b>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring.&nbsp;
Do involuntary disruptions count against the budget?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</b>
</summary>
<b>No</b>
<span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec. (Learn about&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment">updating a deployment</a><span style="color: rgb(34, 34, 34);">.)</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An ephemeral container&nbsp; runs temporarily in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish...</span></b>
</summary>
<b>user-initiated actions</b>&nbsp;Such as troubleshooting and inspecting services
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Sometimes it's necessary to inspect the state of an existing Pod, however, for example to troubleshoot a hard-to-reproduce bug. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">in an existing Pod to _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">inspect its state and run arbitrary commands</span>
</details>

<details>
<summary>
<b>Will an ephemeral container ever be automatically restarted?</b>
</summary>
No
</details>

<details>
<summary>
<b>Do ephemeral containers have guaranteed resources?</b>
</summary>
No
</details>

<details>
<summary>
<b>Do ephemeral containers guarantee execution?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Ephemeral containers are described using...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the same&nbsp;</span><code>ContainerSpec</code><span style="color: rgb(34, 34, 34);">&nbsp;as regular containers</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">However, many fields are incompatible and disallowed</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</b>
</summary>
process namespace sharing
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____ indicates the importance of a Pod relative to other Pods.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Priority</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">priority</span>
</details>

<details>
<summary>
<b>A malicious user could create Pods at the highest possible priorities, causing other Pods to be evicted/not get scheduled. An administrator can use _____ to prevent users from creating pods at high priorities.</b>
</summary>
ResourceQuota
</details>

<details>
<summary>
<b>To use priority and preemption:<ol><li>Add one or more _____</li><li>Create Pods with<font face="monospace">&nbsp;_____</font>&nbsp;set to one of them. Of course you do not need to create the Pods directly; normally you would add&nbsp;<font face="monospace">_____&nbsp;</font>to the Pod template of a collection object like a Deployment.</li></ol></b>
</summary>
PriorityClasses
priorityClassName
</details>

<details>
<summary>
<b>Kubernetes already ships with two PriorityClasses: _____ and _____. These are common classes and are used to ensure that critical components are always scheduled first.</b>
</summary>
system-cluster-critical
system-node-critical
</details>

<details>
<summary>
<b>Critical pods rely on scheduler _____ to be scheduled when a cluster is under resource pressure. For this reason, it is not recommended to disable it.</b>
</summary>
preemption
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ is a non-namespaced object that defines a mapping from a priority class name to the integer value of the priority.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PriorityClass</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field indicates that the value of this PriorityClass should be used for Pods without a&nbsp;</span><code>priorityClassName</code><span style="color: rgb(34, 34, 34);">.&nbsp;</span><span style="color: rgb(34, 34, 34);">Only one such PriorityClass </span><span style="color: rgb(34, 34, 34);">can exist in the system.</span></b>
</summary>
<code>globalDefault</code>
</details>

<details>
<summary>
<b>Pods with <font face="monospace">_____</font>&nbsp;will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. A non-preempting pod waiting to be scheduled will stay in the scheduling queue, until sufficient resources are free, and it can be scheduled. Non-preempting pods, like other pods, are subject to scheduler back-off. This means that if the scheduler tries these pods and they cannot be scheduled, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them.Non-preempting pods may still be preempted by other, high-priority pods.</b>
</summary>
PreemptionPolicy: Never
</details>

<details>
<summary>
<b><code>PreemptionPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;defaults to&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).&nbsp;</span></b>
</summary>
PreemptLowerPriority
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An example use case for data science workloads: A user may submit a job that they want to be prioritized above other workloads, but do not wish to discard existing work by preempting running pods. The high priority job with </span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;will be scheduled ahead of other queued pods, as soon as sufficient cluster resources "naturally" become free.</span></b>
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
<b>Ready, ContainerReady, lastProbeTime, reason. These are the types of latest variable observations of an object's state called _____, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.</b>
</summary>
Conditions
</details>

