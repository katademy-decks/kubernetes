# Lifecycle 

<details>
<summary>
The *phase *of a pod is...
</summary>
A high-level summary of where the pod is in its lifecycle
</details>

<details>
<summary>
*Pending* phase
</summary>
<table><tbody><tr><td>The Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created. This includes time before being scheduled as well as time spent downloading images over the network, which could take a while.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
*Running*&nbsp;phase
</summary>
<table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
*Succeeded *phase
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
*Failed *phase
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
*Unknown *phase
</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
</details>

<details>
<summary>
List all 5 Pod *phases*
</summary>
Pending<div>
</div><div>Running</div><div>
</div><div>Succeeded</div><div>
</div><div>Failed</div><div>
</div><div>Unknown</div>
</details>

<details>
<summary>
List all six fields in a *PodCondition*
</summary>
reason<div>
</div><div>status</div><div>
</div><div>message</div><div>
</div><div>type</div><div>
</div><div>lastProbeTime</div><div>
</div><div>lastTransitionTime</div>
</details>

<details>
<summary>
The *lastProbeTime*&nbsp;condition field provides...
</summary>
A timestamp for when the Pod condition was last probed.
</details>

<details>
<summary>
The&nbsp;*lastTransitionTime*&nbsp;condition field provides...
</summary>
a timestamp for when the Pod last transitioned from one status to another.
</details>

<details>
<summary>
The *message&nbsp;*condition field provides...
</summary>
a human-readable message indicating details about the transition from one status to another.
</details>

<details>
<summary>
The *reason&nbsp;*condition field provides...
</summary>
a unique, one-word reason for the condition's last transition.
</details>

<details>
<summary>
The *status*&nbsp;condition field provides...
</summary>
<div>One of the following:</div><div>*
*</div><div>*"True"*</div><div>*
*</div><div>*"False"*</div><div>*
*</div><div>"*Unknown"*</div>
</details>

<details>
<summary>
The *type*&nbsp;condition field provides...
</summary>
One of the following:<div>
</div><div>*PodScheduled*</div><div>Pod has been scheduled to a node</div><div>*
*</div><div>*Ready*</div><div>Pod is able to serve requests</div><div>*
*</div><div>*Initialized*</div><div>All init containers have started successfully</div><div>*
*</div><div>*ContainersReady*</div><div>All containers in the pod are ready</div>
</details>

<details>
<summary>
<div>A probe can have one of three results:</div>
</summary>
*Success*<div>The Container passed the diagnostic
<div>*
*</div><div>*Failure*</div><div>The Container failed the diagnostic</div><div>*
*</div><div>*Unknown*</div></div><div>The diagnostic failed, so no action should be taken</div>
</details>

<details>
<summary>
A livenessProbe indicates whether a container is...
</summary>
running
</details>

<details>
<summary>
If a livenessProbe fails, the container...
</summary>
is killed by the kubelet, then subjected to the container's *restart policy*.
</details>

<details>
<summary>
A container does not provide a livenessProbe, a readinessProbe nor a startupProbe<div>
</div><div>What will be the state of each probe of the container?</div>
</summary>
*Success *on all of them
</details>

<details>
<summary>
readinessProbe indicates whether...
</summary>
a container is ready to service requests.
</details>

<details>
<summary>
If the readinessProbe fails, what happens?
</summary>
The *endpoints controlller* removes the *Pod's IP address* from the endpoints of all *Services *that match the Pod
</details>

<details>
<summary>
A container's default readiness state before the initial delay is...
</summary>
Failure
</details>

<details>
<summary>
startupProbe indicates whether...
</summary>
the application in the container has started.
</details>

<details>
<summary>
A startupProbe is provided to a container<div>
</div><div>What happens to the other probes?</div>
</summary>
All other probes are disabled until startupProbe succeeds.
</details>

<details>
<summary>
If the startupProbe fails, the container...
</summary>
is killed by the kubelet, then subjected to the container's *restart policy*.
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Do you still need a livenessProbe?</span></div>
</summary>
Not necessarily.&nbsp;<div>
</div><div><span style="color: rgb(34, 34, 34);">The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;</span><code>restartPolicy</code><span style="color: rgb(34, 34, 34);">.</span>
</div>
</details>

<details>
<summary>
A container should be killed or restarted if a probe fails. What can be done to achieve this?
</summary>
1. Specify a *livenessProbe&nbsp;*<div>
</div><div>2. Add a *restartPolicy *of *Always *or *OnFailure*</div>
</details>

<details>
<summary>
A Pod should only be sent traffic when a probe succeeds. What can achieve this?
</summary>
readinessProbe
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">A Container should be able to take itself down for maintenance. What can achieve this?</span>
</summary>
A *readinessProbe *that checks an endpoints specific to readiness that is different from the liveness probe.
</details>

<details>
<summary>
The three possible states of containers are...
</summary>
Waiting<div>
</div><div>Running</div><div>
</div><div>Terminated</div>
</details>

<details>
<summary>
A container is *Waiting *when...
</summary>
It is neither *Running *or *Terminated*<div>
</div><div>A *Waiting *container still runs operations like pulling images, applying Secrets etc.</div>
</details>

<details>
<summary>
How to tell why a container is in&nbsp;*Waiting *state?
</summary>
Check the state's&nbsp;*Reason *field
</details>

<details>
<summary>
A container is in the *Running *state when...
</summary>
It is executing without issues.
</details>

<details>
<summary>
Which hook is executed prior to a container entering its *Running *state?
</summary>
postStart
</details>

<details>
<summary>
A container is in the *Terminated *state when...
</summary>
It has successfully or unsuccessfully completed execution.
</details>

<details>
<summary>
How to tell why a container is in *Terminated *state?
</summary>
Check the state's *Reason *and *Exit Code* fields.
</details>

<details>
<summary>
Which hook is executed before a container enters Terminated state?
</summary>
preStop
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Inject extra feedback or signals into PodStatus via...</span>
</summary>
*Pod readiness*
</details>

<details>
<summary>
You can add *Pod readiness* into *PodStatus *by...
</summary>
*readinessGates*<div>
</div><div>Add it into PodSpec to specify a list of extra conditions for the kubelet to evaluate</div><div>
</div><div>Ex.:</div><div>
</div><div><pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
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
</span><span style="color: rgb(187, 187, 187);"></span>...</code></pre></div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of...</span>
</summary>
*status.condition* fields for the Pod<div>
</div><div>If such a field isn't found, the status of the condition defaults to *"False"*</div>
</details>

<details>
<summary>
*restartPolicy *possible values are...
</summary>
Always<div>
</div><div>Never</div><div>
</div><div>OnFailure</div>
</details>

<details>
<summary>
Default restartPolicy is...
</summary>
Always
</details>

<details>
<summary>
Does a Pod's *restartPolicy *apply to all its containers?
</summary>
Yes
</details>

<details>
<summary>
Once bound to a node, will a Pod ever rebound to another node?
</summary>
No
</details>

<details>
<summary>
Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span>
</summary>
Yes
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at _____ and is reset after ten minutes of successful execution.</span>
</summary>
exponential back-off<div>
</div><div>5 minutes</div>
</details>

<details>
<summary>
Example livenessProbe spec
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
A pod has one container. The container exits with *success*.<div>
</div><div>What happens depending on each possible *restartPolicy*?</div>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li></ul>
</details>

<details>
<summary>
A pod has one container. The container exits with&nbsp;*failure*.<div>
</div><div>What happens depending on each possible&nbsp;*restartPolicy*?</div>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<div><div>Pod is running and has two Containers. Container 1 exits with *failure*.</div></div><div>
</div><div>What happens depending on each possible&nbsp;*restartPolicy*?</div>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Do not restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li></ul><div><span style="color: rgb(34, 34, 34);">If Container 1 is not running, and Container 2 exits:</span></div><div><ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul></div>
</details>

<details>
<summary>
<div><div><div>Pod is running and has one Container. Container runs *out of memory *(and terminates in failure)</div></div></div><div>
</div><div>What happens depending on each possible&nbsp;*restartPolicy*?</div>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Log failure event; Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<div><div><div><div>Pod is running, and a disk dies.</div></div></div></div><div>
</div><div>What happens?</div>
</summary>
<ul><li>Kill all Containers.</li><li>Log appropriate event.</li><li>Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<div><div><div><div><div>Pod is running, and its node is segmented out.</div></div></div></div></div><div>
</div><div>What happens?</div>
</summary>
<ul><li>Node controller waits for timeout.</li><li>Node controller sets Pod&nbsp;<code>phase</code>&nbsp;to Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

