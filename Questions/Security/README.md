# Security 

<details>
<summary>A _____ contains a set of additive RBAC permissions</summary>
Role / Clusterrole
<br></details><details>
<summary>List some ways to improve Kubernetes security</summary>
Log everything in prod
Alert and apply new CVE fixes
Restrict access to nodes, etcd, sudo
Network segmentation
Resource quotas and policy rules&nbsp;
Secrets as volumes
Containers should be non-root, with read-only filesystems
<br></details><details>
<summary>How can any container in a pod enable privileged mode?</summary>
Using the <b>privileged</b>&nbsp;flag in the security context of the container spec.
<br></details><details>
<summary>The 4C's of Cloud Native security are...</summary>
Cloud, Clusters, Containers, Code
<br></details><details>
<summary>The three PodSecurityPolicy types are:</summary>
Privileged, Restricted, Default
<br></details><details>
<summary>Is there currently an API standard for whether a Pod is considered sandboxed?</summary>
No -&nbsp;<span style="color: rgb(34, 34, 34);">Sandbox Pods may be identified by the use of a sandboxed runtime (such as gVisor or Kata Containers), but there is no standard definition of what a sandboxed runtime is.</span>
<br></details><details>
<summary><i>S</i><span style="color: rgb(34, 34, 34);">ecurity sensitive aspects of pod specification, such as c</span><span style="color: rgb(34, 34, 34);">onditions that a pod must run with in order to be accepted into the system, as well as defaults for the related fields can be stored inside cluster-level resources called _____</span></summary>
PodSecurityPolicy
<br></details><details>
<summary>Some security tools with which clusters can be further protected, are...</summary>
Snyk, Aqua, kata containers
gVisor, AppArmor, seccomp, SELinux
<br></details><details>
<summary>Areas of Concern for Workload Security</summary>
Authentication
RBAC API authorization&nbsp;
Secret and encryption management
Pod security policies
Network policies
TLS
<br></details><details>
<summary>Do security contexts replace Pod Security Policy?</summary>
<span style="color: rgb(34, 34, 34);">Debatable. Numerous means of policy enforcement have arisen that augment or replace the use of PodSecurityPolicy.</span>
<br></details><details>
<summary>What are some tools with which clusters can be audited?</summary>
Sonobuoy
<br></details><details>
<summary>Area of Concern for Container Security</summary>
OS and dependency scanning
Image signing and enforcement
Minimalising user privilege
<br></details><details>
<summary>Security settings for Pods are typically applied by using _____, which<span style="color: rgb(34, 34, 34);">&nbsp;allow for the definition of privilege and access controls on a per-Pod basis.</span></summary>
security contexts
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;is a cluster-level resource that controls security sensitive aspects of the Pod specification.</span></summary>
Pod Security Policy
<br></details>