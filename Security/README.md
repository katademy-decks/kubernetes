# Security 

<details>
<summary>
<b>How to harden the security of the container?</b>
</summary>
containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
<b> &nbsp;securityContext:
</b><strong>&nbsp; &nbsp;<font color="#ab1aff">readOnlyRootFilesystem: true</font></strong><b><font color="#ab1aff">
</font></b><strong>&nbsp; &nbsp;<i><font color="#ff5d83">runAsNonRoot: true</font></i></strong><b>
 &nbsp;&nbsp;&nbsp;runAsUser: 1000</b>
&nbsp; &nbsp;# setuid&nbsp;mechanism can temporarily gain the privileges of the user that&nbsp;<em>owns</em>&nbsp;the binary<b>
</b>&nbsp; &nbsp;allowPrivilegeEscalation: false
&nbsp; &nbsp;capabilities:&nbsp;&nbsp; &nbsp; &nbsp;drop: ["all"]&nbsp;&nbsp; &nbsp; &nbsp;drop: ["CHOWN", "NET_RAW", "SETPCAP"]&nbsp;&nbsp; &nbsp; &nbsp;add: ["NET_ADMIN"]<strong>
</strong>
</details>

<details>
<summary>
<b>The 4C's of Cloud Native security are...</b>
</summary>
Cloud, Clusters, Containers, Code
</details>

<details>
<summary>
<b>Areas of Concern for Workload Security</b>
</summary>
Authentication
RBAC API authorization&nbsp;
Secret and encryption management
Pod security policies
Network policies
TLS
</details>

<details>
<summary>
<b>Area of Concern for Container Security</b>
</summary>
OS and dependency scanning
Image signing and enforcement
Minimalising user privilege
</details>

<details>
<summary>
<b>Security settings for Pods are typically applied by using _____, which<span style="color: rgb(34, 34, 34);">&nbsp;allow for the definition of privilege and access controls on a per-Pod basis.</span></b>
</summary>
security contexts
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;is a cluster-level resource that controls security sensitive aspects of the Pod specification.</span></b>
</summary>
Pod Security Policy
</details>

<details>
<summary>
<b>Do security contexts replace Pod Security Policy?</b>
</summary>
<span style="color: rgb(34, 34, 34);">Debatable. Numerous means of policy enforcement have arisen that augment or replace the use of PodSecurityPolicy.</span>
</details>

<details>
<summary>
<b>The three PodSecurityPolicy types are:</b>
</summary>
Privileged, Restricted, Default
</details>

<details>
<summary>
<b>Is there currently an API standard for whether a Pod is considered sandboxed?</b>
</summary>
No -&nbsp;<span style="color: rgb(34, 34, 34);">Sandbox Pods may be identified by the use of a sandboxed runtime (such as gVisor or Kata Containers), but there is no standard definition of what a sandboxed runtime is.</span>
</details>

<details>
<summary>
<b>A _____ contains a set of additive RBAC permissions</b>
</summary>
Role / Clusterrole
</details>

