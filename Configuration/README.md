# Configuration 

<details>
<summary>
<b>How would you improve Kubernetes security</b>
</summary>
Log everything in prod
Alert and apply new CVE fixes
Use audit&nbsp;services (Sonobuoy)

No access to nodes
No access to ETCD
Network segmentation
Resource quotas and policy rules&nbsp;
Secrets as volumes
Scan containers (Snyk, Aqua)

Non-root containers
Read-only filesystems on containers
Disallow sudo
Use kata containers&nbsp;

gVisorAppArmor (lockbox)seccomp (lockbox)SELinux
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ is an API object used to store non-confidential data in key-value pairs.&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/">Pods<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">&nbsp;can consume them as environment variables, command-line arguments, or as configuration files in a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/volumes/">volume<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">ConfigMap</span>
</details>

<details>
<summary>
<b>If the data you want to store are confidential, use a _____ rather than a ConfigMap</b>
</summary>
Secret
</details>

<details>
<summary>
<b>Each ConfigMap you want to mount in a Pod needs to be referred to in...</b>
</summary>
&nbsp;<code>.spec.volumes</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The&nbsp;</span><code>KUBECONFIG</code><span style="color: rgb(34, 34, 34);">&nbsp;environment variable holds...</span></b>
</summary>
A list of kubeconfig files
</details>

<details>
<summary>
<b><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;are&nbsp;cluster-level resources that control security sensitive aspects of pod specification. They define</span><span style="color: rgb(34, 34, 34);">&nbsp;a set of conditions that a pod must run with in order to be accepted into the system, as well as defaults for the related fields.</span></b>
</summary>
PodSecurityPolicy
</details>

<details>
<summary>
<b>The resource for storing sensitive information in Kubernetes.</b>
</summary>
Secrets
</details>

<details>
<summary>
<b>What Are Labels?</b>
</summary>
Key/value pairs that are attached to objects, such as pods.
</details>

<details>
<summary>
<b>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;on bare-metal Intel processors.</b>
</summary>
<strong>hyperthread</strong>&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The scheduler ensures that, for each resource type, the sum of the resource requests of the scheduled Containers is _____ than the capacity of the node.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">less</span>
</details>

<details>
<summary>
<b>Suppose you have several clusters, and your users and components authenticate in a variety of ways. For example:<ul><li>A running kubelet might authenticate using certificates.</li><li>A user might authenticate using tokens.</li><li>Administrators might have sets of certificates that they provide to individual users.</li></ul>With _____ files, you can organize your clusters, users, contexts, and namespaces.</b>
</summary>
kubeconfig
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Each context has three parameters:&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">cluster, namespace, and user.&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">There is a concern that one Pod or Container could monopolize all available resources. A _____ is a policy to constrain resource allocations (to Pods or Containers) in a namespace.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">LimitRange</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">provides constraints that limit aggregate resource consumption per namespace. It can limit the quantity of objects that can be created in a namespace by type, as well as the total amount of compute resources that may be consumed by resources in that project.</span></b>
</summary>
<code>ResourceQuota</code>
</details>

<details>
<summary>
<b>Do containers run with unbounded compute resources on a Kubernetes cluster?</b>
</summary>
By default - yes. Limits and ResourceQuotas are recommended.
</details>

<details>
<summary>
<b>You can enforce minimum and maximum compute resources usage per Pod or Container in a namespace using a...</b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>You can&nbsp;<span style="background-color: rgb(255, 255, 255);">enforce minimum and maximum storage request per PersistentVolumeClaim in a namespace using a...</span></b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>You can enforce a ratio between request and limit for a resource in a namespace using a...</b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>You can set default request/limit for compute resources in a namespace and automatically inject them to Containers at runtime using a...</b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>When you run a Pod on a Node, the Pod itself takes an amount of system resources. These resources are additional to the resources needed to run the container(s) inside the Pod.&nbsp;<i>_____&nbsp;</i>is a feature for accounting for the resources consumed by the Pod infrastructure on top of the container requests &amp; limits.</b>
</summary>
Pod Overhead
</details>

<details>
<summary>
<b>The _____ is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod’s environment.</b>
</summary>
ConfigMap
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The Kubernetes alpha feature </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;provides an option to set individual Secrets and ConfigMaps as immutable. For clusters that extensively use ConfigMaps (at least tens of thousands of unique ConfigMap to Pod mounts)</span></b>
</summary>
Immutable Secrets and ConfigMaps
</details>

<details>
<summary>
<b>You can significantly reduce load on kube-apiserver and improve cluster performance by closing watches for secrets or config maps and, setting them as _____.</b>
</summary>
immutable
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If the node where a Pod is running has enough of a resource available, it's allowed for a container to use more resources than defined in its resource&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">. However, a container is not allowed to use more than its resource&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">.</span></b>
</summary>
request
limit
</details>

<details>
<summary>
<b>A file that is used to configure access to clusters is called a _____ file</b>
</summary>
kubeconfig
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">element in a kubeconfig file is used to group access parameters under a convenient name.</span></b>
</summary>
context
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">default kubeconfig filepath</span></b>
</summary>
$HOME/.kube/config
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The administrator creates one LimitRange per _____.</span></b>
</summary>
namespace
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The <font face="monospace">_____&nbsp;</font></span>admission&nbsp;<span style="color: rgb(34, 34, 34);">controller enforces defaults and limits for all Pods and Containers that do not set compute resource requirements and tracks usage to ensure it does not exceed resource minimum, maximum and ratio defined in any LimitRange present in the namespace.</span></b>
</summary>
<code>LimitRanger</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b>To&nbsp;define default CPU limit and request to 150m and memory default request to 300Mi for Containers started with no cpu and memory requests in their specs, you could use...</b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>In a cluster with a capacity of 32 GiB RAM, and 16 cores, let team A use 20 GiB and 10 cores, let B use 10GiB and 4 cores, and hold 2GiB and 2 cores in reserve for future allocation.
You could create this policy via...</b>
</summary>
ResourceQuota
</details>

<details>
<summary>
<b>Pod Overhead is set at _____&nbsp;time according to the overhead associated with the Pod's _____. When enabled, it is considered in addition to the sum of container resource requests when scheduling a Pod. Similarly, Kubelet will include the Pod overhead when sizing the Pod cgroup, and when carrying out Pod eviction ranking.</b>
</summary>
admission
RuntimeClass
</details>

<details>
<summary>
<b>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;for cloud providers.</b>
</summary>
core
</details>

<details>
<summary>
<b>What is Custom resource in Kubernetes?</b>
</summary>
A&nbsp;<em>custom resource</em>&nbsp;is an extension of the Kubernetes API. Many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a config map currently consumed in a volume is updated, are projected keys inside the Pods eventually updated as well?</span></b>
</summary>
Yes
<span style="color: rgb(34, 34, 34);">The kubelet checks whether the mounted config map is fresh on every periodic sync. However, the kubelet also uses its local configurable cache for getting the current value of the ConfigMap.&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">T</span><span style="color: rgb(34, 34, 34);">o pass a secret that contains a Docker (or other) image registry password to the kubelet, you can use...</span></b>
</summary>
<code>imagePullSecrets</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a process in the container tries to consume more than the allowed amount of memory, the system kernel _____ the process that attempted the allocation, with an _____ error</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">terminates</span>

OOM (Out of Memory)
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When several users or teams share a cluster with a fixed number of nodes, there is a concern that one team could use more than its fair share of resources. _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is a tool to address this concern.</span></b>
</summary>
ResorceQuota
</details>

