<details>
<summary>The 4C's of Cloud Native security are _____, _____, _____ and _____.</summary>
Cloud, Clusters, Containers and Code
<br></details>

<details>
<summary>_____ <span style="color: rgb(34, 34, 34);">allow defining privilege and access controls per-Pod or per-container.</span></summary>
securityContexts
<br></details>

<details>
<summary>The three PodSecurityPolicy types are _____, _____ and Default.</summary>
Privileged, Restricted, Default
<br></details>

<details>
<summary><i>_____ </i>objects&nbsp;contain sensitive aspects of pod specification, such as the conditions they must meet or their default fields.</summary>
PodSecurityPolicy
<br></details>

<details>
<summary>Can Snyk improve container security?</summary>
Yes
<br></details>

<details>
<summary>AppArmor profiles are specified per _____</summary>
container
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">To specify the AppArmor profile to run a Pod container with, add the profile-specifying _____ into the Pod's metadata.</span></summary>
<span style="color: rgb(34, 34, 34);">annotation&nbsp;</span>
<br></details>

<details>
<summary>Do AppArmor profiles have to be loaded onto the host before applying the annotation?</summary>
Yes - except the container runtime's default profile.
<br></details>

<details>
<summary>The command _____ verifies that a container's root process is running the correct AppArmor profile by checking its <b>/proc/1/attr/current</b>&nbsp;file.</summary>
kubectl exec &lt;pod&gt; cat&nbsp;/proc/1/attr/current
<br></details>

<details>
<summary>Do you usually need to upload AppArmor profiles to all of your nodes?</summary>
Yes - since you don't know which node the pod will be scheduled to.
<br></details>

<details>
<summary>Containers in production should be running as a non-root user, which is set in their securityContext via _____</summary>
runAsNonRoot: true
<br></details>

<details>
<summary>You can improve a container's security by dropping Linux _____ such as "all", "CHOWN", "NET_RAW", "SETPCAP" via the securityContext.</summary>
capabilities&nbsp;
<br></details>

<details>
<summary>Containers should ideally run with read-only root filesystems, set in their security contexts via _____&nbsp;</summary>
readOnlyRootFilesystem: true
<br></details>

<details>
<summary>Does container/host operating system scanning improve security?</summary>
Yes
<br></details>

<details>
<summary>Should you enforce image signing in production?</summary>
Yes
<br></details>

<details>
<summary>Once an attacker gets control of a container, they might obtain control of the _____ it runs on, and then the internal network.</summary>
node
<br></details>

<details>
<summary>By default, any Pod in a cluster gets a service account with certain permissions allowing it to communicate with the API server. These service account should be disabled for Pods that never need to talk to the API server, as an attacker could otherwise steal the _____.</summary>
auth token
<br></details>

<details>
<summary>Attackers can break out of the container by exloiting the _____, _____, etc.</summary>
container runtime
kernel
<br></details>

<details>
<summary>Setting securityContext._____ to False makes it harder to escalate privileges inside a container.</summary>
allowPrivilegeEscalation
<br></details>

<details>
<summary>Tools like _____ or _____ are able to sandbox Pods from each other on the same host, giving you two additional layers of isolation - the Sandbox and the Container Linux Kernel.</summary>
gVisor&nbsp;
kata containers
<br></details>

<details>
<summary>_____ is a user space kernel that can intercept and implement syscalls in userspace, effectively sandboxing the Pod to an environment with low capabilities and restricted seccomp filters.</summary>
gVisor
<br></details>

<details>
<summary>True or False? Kubernetes obviously automatically applies its own container runtime's default seccomp and AppArmor profiles to Pods, so no extra annotations must be applied to them.</summary>
FALSE! A Kubernetes Pod has LESS default restrictions applied than if it were ran directly from a container runtime.
<br></details>

<details>
<summary>A Pod has free access to the Internet. Can an attacker use this to download exploits?</summary>
Yes
<br></details>

<details>
<summary>A container has network access to a <b>/metrics</b> endpoint. Could an attacker potentially find almost everything about the cluster from inside the container by reading cAdvisor/Heapster output at the endpoint?</summary>
Yes
<br></details>

<details>
<summary>Tools like _____ audit the OS, container runtime, K8S, configuration using CIS benchmarks.</summary>
kube-auto-analyzer, kube-bench
<br></details>

<details>
<summary>Can maintaining standard, secure base images for all containers improve overall workload security?</summary>
Yes
<br></details>

<details>
<summary>To improve security, you could ideally collect logs from all containers - but especially _____ access/deny logs.</summary>
RBAC
<br></details>

<details>
<summary>The default Pod service account can be disabled by setting _____</summary>
autonomousServiceAccountToken: false
<br></details>

<details>
<summary>Cluster-wide _____ objects can enforce container restrictions, thus protecting the node they run on.</summary>
PodSecurityPolicy&nbsp;
<br></details>

<details>
<summary>PodSecurityPolicies are _____-level resources.</summary>
Cluster
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;is a cluster-level resource that controls security sensitive aspects of the Pod specification.</span></summary>
Pod Security Policy
<br></details>

<details>
<summary>Should you minimise user privilege inside your containers in production?</summary>
Yes
<br></details>