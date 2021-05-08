<details>
<summary>The resources for storing sensitive information in Kubernetes are _____</summary>
Secrets
<br></details>

<details>
<summary>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;on bare-metal Intel processors.</summary>
<strong>hyperthread</strong>&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">There is a concern that one Pod or Container could monopolize all available resources. A _____ is a policy to constrain resource allocations (to Pods or Containers) in a namespace.</span></summary>
<span style="color: rgb(34, 34, 34);">LimitRange</span>
<br></details>

<details>
<summary>A _____&nbsp;provides constraints that limit aggregate resource consumption per namespace. It can limit the quantity of objects that can be created in a namespace by type, as well as the total amount of compute resources that may be consumed by resources in that project.</summary>
ResourceQuota
<br></details>

<details>
<summary>Do containers run with unbounded compute resources on a Kubernetes cluster?</summary>
By default - yes. Limits and ResourceQuotas are recommended.
<br></details>

<details>
<summary>You can enforce minimum and maximum compute resources usage per Pod or Container in a namespace using a _____</summary>
LimitRange
<br></details>

<details>
<summary>You can&nbsp;<span style="background-color: rgb(255, 255, 255);">enforce minimum and maximum storage request per PersistentVolumeClaim in a namespace using a _____</span></summary>
LimitRange
<br></details>

<details>
<summary>You can enforce a ratio between request and limit for a resource in a namespace using a _____</summary>
LimitRange
<br></details>

<details>
<summary>You can set default request/limit for compute resources in a namespace and automatically inject them to Containers at runtime using a _____</summary>
LimitRange
<br></details>

<details>
<summary>The _____ is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod�s environment.</summary>
ConfigMap
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The Kubernetes alpha feature </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;provides an option to set individual Secrets and ConfigMaps as immutable. For clusters that extensively use ConfigMaps (at least tens of thousands of unique ConfigMap to Pod mounts)</span></summary>
Immutable Secrets and ConfigMaps
<br></details>

<details>
<summary>You can significantly reduce load on kube-apiserver and improve cluster performance by closing watches for secrets or config maps and, setting them as _____.</summary>
immutable
<br></details>

<details>
<summary>If the node where a Pod is running has enough of a resource available, it's allowed for a container to use more resources than defined in its resource&nbsp;_____. However, a container is not allowed to use more than its resource&nbsp;_____.</summary>
request
limit
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The administrator creates one LimitRange per _____.</span></summary>
namespace
<br></details>

<details>
<summary>To&nbsp;define default CPU limit and request to 150m and memory default request to 300Mi for Containers started with no cpu and memory requests in their specs, you could use...</summary>
LimitRange
<br></details>

<details>
<summary>One cpu, in Kubernetes request/limit terms, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;for cloud providers.</summary>
core
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a config map currently consumed in a volume is updated, are projected keys inside the Pods eventually updated as well?</span></summary>
Yes
<span style="color: rgb(34, 34, 34);">The kubelet checks whether the mounted config map is fresh on every periodic sync. However, the kubelet also uses its local configurable cache for getting the current value of the ConfigMap.&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When several users or teams share a cluster with a fixed number of nodes, there is a concern that one team could use more than its fair share of resources. _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is a tool to address this concern.</span></summary>
ResorceQuota
<br></details>

<details>
<summary>A malicious user could create Pods at the highest possible priorities, causing other Pods to be evicted/not get scheduled. An administrator can use _____ to prevent users from creating pods at high priorities.</summary>
ResourceQuota
<br></details>

<details>
<summary>If the data you want to store are confidential, use a _____ rather than a ConfigMap</summary>
Secret
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ is an API object used to store non-confidential data in key-value pairs.&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/">Pods<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">&nbsp;can consume them as environment variables, command-line arguments, or as configuration files in a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/volumes/">volume<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">.</span></summary>
<span style="color: rgb(34, 34, 34);">ConfigMap</span>
<br></details>

<details>
<summary>Mounting ConfigMaps in a Pod is done in its .spec._____</summary>
volumes
<br></details>

<details>
<summary>The command ______ creates a new Kubernetes Secret.</summary>
kubectl create secret
<br></details>

<details>
<summary>Should you set resource limits for all containers?</summary>
Yes
<br></details>

<details>
<summary>Outside CPU-intensive jobs, it's good to set container CPU requests up to _____</summary>
1 CPU
<br></details>

<details>
<summary>A CPU limit of 1 means 1 CPU second per _____</summary>
second
<br></details>

<details>
<summary>A process with one thread cannot consume more than _____. The more threads, the less time it takes to consume it.</summary>
1 CPU second per second
<br></details>

<details>
<summary>Is it necessary to set CPU limits for your app?</summary>
Usually no.&nbsp;<a href="https://medium.com/@betz.mark/understanding-resource-limits-in-kubernetes-cpu-time-9eff74d3161b">https://medium.com/@betz.mark/understanding-resource-limits-in-kubernetes-cpu-time-9eff74d3161b</a>
<br></details>

<details>
<summary>If you don't set limits for each container, the limits will be inferred from the namespace's _____, if set.</summary>
LimitRange
<br></details>