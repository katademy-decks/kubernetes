# Lifecycle 

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
<b>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</b>
</summary>
a timestamp for when the Pod last transitioned from one status to another.
</details>

<details>
<summary>
<b>The <b>message&nbsp;</b>condition field provides...</b>
</summary>
a human-readable message indicating details about the transition from one status to another.
</details>

<details>
<summary>
<b>The <b>reason&nbsp;</b>condition field provides...</b>
</summary>
a unique, one-word reason for the condition's last transition.
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
<b>A probe can have one of three results:</b>
</summary>
<b>Success</b>The Container passed the diagnostic
<b>
</b><b>Failure</b>The Container failed the diagnostic<b>
</b><b>Unknown</b>The diagnostic failed, so no action should be taken
</details>

<details>
<summary>
<b>A livenessProbe indicates whether a container is...</b>
</summary>
running
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
<b>Example livenessProbe spec</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">test</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness-http<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">args</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- /server<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/liveness<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">livenessProbe</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">httpGet</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># when "host" is not defined, "PodIP" will be used</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># host: my-host</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># when "scheme" is not defined, "HTTP" scheme will be used. Only "HTTP" and "HTTPS" are allowed</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># scheme: HTTPS</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">path</span>:<span style="color: rgb(187, 187, 187);"> </span>/healthz<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">port</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">8080</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">httpHeaders</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>X-Custom-Header<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">value</span>:<span style="color: rgb(187, 187, 187);"> </span>Awesome<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">initialDelaySeconds</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">15</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">timeoutSeconds</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness</code></pre>
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

