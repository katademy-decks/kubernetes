# Configuration 

<details>
<summary>_____ allow you to create your own custom Kubernetes objects, to store any data you wish.&nbsp;</summary>
Custom Resource Definitions (CRDs)
<br></details><details>
<summary>The resource for storing sensitive information in Kubernetes.</summary>
Secrets
<br></details><details>
<summary>What Are Labels?</summary>
Key/value pairs that are attached to objects, such as pods.
<br></details><details>
<summary>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;on bare-metal Intel processors.</summary>
<strong>hyperthread</strong>&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The scheduler ensures that, for each resource type, the sum of the resource requests of the scheduled Containers is _____ than the capacity of the node.</span></summary>
<span style="color: rgb(34, 34, 34);">less</span>
<br></details><details>
<summary>Suppose you have several clusters, and your users and components authenticate in a variety of ways. For example:<ul><li>A running kubelet might authenticate using certificates.</li><li>A user might authenticate using tokens.</li><li>Administrators might have sets of certificates that they provide to individual users.</li></ul>With _____ files, you can organize your clusters, users, contexts, and namespaces.</summary>
kubeconfig
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Each context has three parameters:&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">cluster, namespace, and user.&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">There is a concern that one Pod or Container could monopolize all available resources. A _____ is a policy to constrain resource allocations (to Pods or Containers) in a namespace.</span></summary>
<span style="color: rgb(34, 34, 34);">LimitRange</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">provides constraints that limit aggregate resource consumption per namespace. It can limit the quantity of objects that can be created in a namespace by type, as well as the total amount of compute resources that may be consumed by resources in that project.</span></summary>
<code>ResourceQuota</code>
<br></details><details>
<summary>Do containers run with unbounded compute resources on a Kubernetes cluster?</summary>
By default - yes. Limits and ResourceQuotas are recommended.
<br></details><details>
<summary>You can enforce minimum and maximum compute resources usage per Pod or Container in a namespace using a...</summary>
LimitRange
<br></details><details>
<summary>You can&nbsp;<span style="background-color: rgb(255, 255, 255);">enforce minimum and maximum storage request per PersistentVolumeClaim in a namespace using a...</span></summary>
LimitRange
<br></details><details>
<summary>You can enforce a ratio between request and limit for a resource in a namespace using a...</summary>
LimitRange
<br></details><details>
<summary>You can set default request/limit for compute resources in a namespace and automatically inject them to Containers at runtime using a...</summary>
LimitRange
<br></details><details>
<summary>When you run a Pod on a Node, the Pod itself takes an amount of system resources. These resources are additional to the resources needed to run the container(s) inside the Pod.&nbsp;<i>_____&nbsp;</i>is a feature for accounting for the resources consumed by the Pod infrastructure on top of the container requests &amp; limits.</summary>
Pod Overhead
<br></details><details>
<summary>The _____ is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod’s environment.</summary>
ConfigMap
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The Kubernetes alpha feature </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;provides an option to set individual Secrets and ConfigMaps as immutable. For clusters that extensively use ConfigMaps (at least tens of thousands of unique ConfigMap to Pod mounts)</span></summary>
Immutable Secrets and ConfigMaps
<br></details><details>
<summary>You can significantly reduce load on kube-apiserver and improve cluster performance by closing watches for secrets or config maps and, setting them as _____.</summary>
immutable
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If the node where a Pod is running has enough of a resource available, it's allowed for a container to use more resources than defined in its resource&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">. However, a container is not allowed to use more than its resource&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">.</span></summary>
request
limit
<br></details><details>
<summary>A file that is used to configure access to clusters is called a _____ file</summary>
kubeconfig
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">element in a kubeconfig file is used to group access parameters under a convenient name.</span></summary>
context
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">default kubeconfig filepath</span></summary>
$HOME/.kube/config
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The administrator creates one LimitRange per _____.</span></summary>
namespace
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The <font face="monospace">_____&nbsp;</font></span>admission&nbsp;<span style="color: rgb(34, 34, 34);">controller enforces defaults and limits for all Pods and Containers that do not set compute resource requirements and tracks usage to ensure it does not exceed resource minimum, maximum and ratio defined in any LimitRange present in the namespace.</span></summary>
<code>LimitRanger</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary>To&nbsp;define default CPU limit and request to 150m and memory default request to 300Mi for Containers started with no cpu and memory requests in their specs, you could use...</summary>
LimitRange
<br></details><details>
<summary>In a cluster with a capacity of 32 GiB RAM, and 16 cores, let team A use 20 GiB and 10 cores, let B use 10GiB and 4 cores, and hold 2GiB and 2 cores in reserve for future allocation.
You could create this policy via...</summary>
ResourceQuota
<br></details><details>
<summary>Pod Overhead is set at _____&nbsp;time according to the overhead associated with the Pod's _____. When enabled, it is considered in addition to the sum of container resource requests when scheduling a Pod. Similarly, Kubelet will include the Pod overhead when sizing the Pod cgroup, and when carrying out Pod eviction ranking.</summary>
admission
RuntimeClass
<br></details><details>
<summary>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;for cloud providers.</summary>
core
<br></details><details>
<summary>What is Custom resource in Kubernetes?</summary>
A&nbsp;<em>custom resource</em>&nbsp;is an extension of the Kubernetes API. Many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a config map currently consumed in a volume is updated, are projected keys inside the Pods eventually updated as well?</span></summary>
Yes
<span style="color: rgb(34, 34, 34);">The kubelet checks whether the mounted config map is fresh on every periodic sync. However, the kubelet also uses its local configurable cache for getting the current value of the ConfigMap.&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">T</span><span style="color: rgb(34, 34, 34);">o pass a secret that contains a Docker (or other) image registry password to the kubelet, you can use...</span></summary>
<code>imagePullSecrets</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a process in the container tries to consume more than the allowed amount of memory, the system kernel _____ the process that attempted the allocation, with an _____ error</span></summary>
<span style="color: rgb(34, 34, 34);">terminates</span>

OOM (Out of Memory)
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When several users or teams share a cluster with a fixed number of nodes, there is a concern that one team could use more than its fair share of resources. _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is a tool to address this concern.</span></summary>
ResorceQuota
<br></details><details>
<summary>_____ are key-value pairs that identify resources, and can be used with _____ to match a specified group of resources.</summary>
Labels
Selectors
<br></details><details>
<summary>If the data you want to store are confidential, use a _____ rather than a ConfigMap</summary>
Secret
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A _____ is an API object used to store non-confidential data in key-value pairs.&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/">Pods<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">&nbsp;can consume them as environment variables, command-line arguments, or as configuration files in a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/volumes/">volume<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">.</span></summary>
<span style="color: rgb(34, 34, 34);">ConfigMap</span>
<br></details><details>
<summary>Mounting ConfigMaps in a Pod is done in its .spec._____</summary>
volumes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The&nbsp;</span><code>KUBECONFIG</code><span style="color: rgb(34, 34, 34);">&nbsp;environment variable holds...</span></summary>
A list of kubeconfig files
<br></details>