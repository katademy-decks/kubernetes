# Security 

<details>
<summary>
<b>A _____ contains a set of additive RBAC permissions</b>
</summary>
Role / Clusterrole
</details>

<details>
<summary>
<b>List some ways to improve Kubernetes security</b>
</summary>
Log everything in prod
Alert and apply new CVE fixes
Restrict access to nodes, etcd, sudo
Network segmentation
Resource quotas and policy rules&nbsp;
Secrets as volumes
Containers should be non-root, with read-only filesystems
</details>

<details>
<summary>
<b>How can any container in a pod enable privileged mode?</b>
</summary>
Using the <b>privileged</b>&nbsp;flag in the security context of the container spec.
</details>

<details>
<summary>
<b>The 4C's of Cloud Native security are...</b>
</summary>
Cloud, Clusters, Containers, Code
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
<b><i>S</i><span style="color: rgb(34, 34, 34);">ecurity sensitive aspects of pod specification, such as c</span><span style="color: rgb(34, 34, 34);">onditions that a pod must run with in order to be accepted into the system, as well as defaults for the related fields can be stored inside cluster-level resources called _____</span></b>
</summary>
PodSecurityPolicy
</details>

<details>
<summary>
<b>Some security tools with which clusters can be further protected, are...</b>
</summary>
Snyk, Aqua, kata containers
gVisor, AppArmor, seccomp, SELinux
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
<b>Do security contexts replace Pod Security Policy?</b>
</summary>
<span style="color: rgb(34, 34, 34);">Debatable. Numerous means of policy enforcement have arisen that augment or replace the use of PodSecurityPolicy.</span>
</details>

<details>
<summary>
<b>What are some tools with which clusters can be audited?</b>
</summary>
Sonobuoy
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

