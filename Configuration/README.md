# Configuration 

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a config map currently consumed in a volume is updated, are projected keys eventually updated as well?</span></b>
</summary>
Yes
<span style="color: rgb(34, 34, 34);">The kubelet checks whether the mounted config map is fresh on every periodic sync. However, the kubelet uses its local configurable cache for getting the current value of the ConfigMap.&nbsp;</span>
</details>

<details>
<summary>
<b>Make a cluster faster by setting configmaps or secrets as _____, which&nbsp;improves performance of your cluster by significantly reducing load on kube-apiserver, by closing watches for secrets or config maps.</b>
</summary>
immutable
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Fractional requests are allowed. A Container with </span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;of&nbsp;</span><code>0.5</code><span style="color: rgb(34, 34, 34);">&nbsp;is guaranteed half as much CPU as one that asks for 1 CPU. The expression&nbsp;</span><code>0.1</code><span style="color: rgb(34, 34, 34);">&nbsp;is equivalent to the expression&nbsp;</span><code>100m</code><span style="color: rgb(34, 34, 34);">, which can be read as "one hundred millicpu". Some people say "one hundred millicores", and this is understood to mean the same thing. A request with a decimal point, like&nbsp;</span><code>0.1</code><span style="color: rgb(34, 34, 34);">, is converted to&nbsp;</span><code>100m</code><span style="color: rgb(34, 34, 34);">&nbsp;by the API, and precision finer than&nbsp;</span><code>1m</code><span style="color: rgb(34, 34, 34);">&nbsp;is not allowed. For this reason, the form&nbsp;</span><code>100m</code><span style="color: rgb(34, 34, 34);">&nbsp;might be preferred.</span></b>
</summary>
spec.containers[].resources.requests.cpu
</details>

<details>
<summary>
<b><ul><li>Different teams work in different namespaces. Currently this is voluntary, but support for making this mandatory via ACLs is planned.</li><li>The administrator creates one&nbsp;<font face="monospace">_____&nbsp;</font>for each namespace.</li><li>Users create resources (pods, services, etc.) in the namespace, and the quota system tracks usage to ensure it does not exceed hard resource limits defined in a&nbsp;<code>_____</code>.</li><li>If creating or updating a resource violates a quota constraint, the request will fail with HTTP status code&nbsp;<code>403 FORBIDDEN</code>&nbsp;with a message explaining the constraint that would have been violated.</li><li>If quota is enabled in a namespace for compute resources like&nbsp;<code>cpu</code>&nbsp;and&nbsp;<code>memory</code>, users must specify requests or limits for those values; otherwise, the quota system may reject pod creation. Hint: Use the&nbsp;<code>LimitRanger</code>&nbsp;admission controller to force defaults for pods that make no compute resource requirements.</li></ul></b>
</summary>
<code>ResourceQuota</code>
</details>

<details>
<summary>
<b>What is Custom resource in Kubernetes?</b>
</summary>
A&nbsp;<em>custom resource</em>&nbsp;is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation. It represents a customization of a particular Kubernetes installation. However, many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.
</details>

<details>
<summary>
<b>Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo</b>
</summary>
Edit standard pod YAML to add volumes with a <i>volumes.secret.secretName </i>value:
<i>spec:</i><i>&nbsp; volumes:</i><i>&nbsp; - name: foo</i><i>&nbsp; &nbsp; secret:</i><i>&nbsp; &nbsp; &nbsp; secretName: mysecret2</i><i>&nbsp; containers:</i><i>&nbsp; - image: nginx</i><i>&nbsp; &nbsp; volumeMounts:</i><i>&nbsp; &nbsp; - name: foo</i><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The administrator creates one LimitRange in one _____.</span></b>
</summary>
namespace
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">There is a concern that one Pod or Container could monopolize all available resources. A _____ is a policy to constrain resource allocations (to Pods or Containers) in a namespace.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">LimitRange</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The&nbsp;</span><code>LimitRanger</code><span style="color: rgb(34, 34, 34);">&nbsp;_____ controller enforces defaults and limits for all Pods and Containers that do not set compute resource requirements and tracks usage to ensure it does not exceed resource minimum, maximum and ratio defined in any LimitRange present in the namespace.</span></b>
</summary>
admission
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When several users or teams share a cluster with a fixed number of nodes, there is a concern that one team could use more than its fair share of resources. _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is a tool to address this concern.</span></b>
</summary>
ResorceQuota
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In a 2 node cluster with a capacity of 8 GiB RAM and 16 cores, to define constrain Pods in a namespace to request 100m of CPU with a max limit of 500m for CPU and request 200Mi for Memory with a max limit of 600Mi for Memory you could use...</span></b>
</summary>
LimitRange
</details>

<details>
<summary>
<b>To&nbsp;define default CPU limit and request to 150m and memory default request to 300Mi for Containers started with no cpu and memory requests in their specs, you could use...</b>
</summary>
LimitRange
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">provides constraints that limit aggregate resource consumption per namespace. It can limit the quantity of objects that can be created in a namespace by type, as well as the total amount of compute resources that may be consumed by resources in that project.</span></b>
</summary>
<code>ResourceQuota</code>
</details>

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
<b><span style="color: rgb(34, 34, 34);">The Kubernetes alpha feature </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;provides an option to set individual Secrets and ConfigMaps as immutable. For clusters that extensively use ConfigMaps (at least tens of thousands of unique ConfigMap to Pod mounts)</span></b>
</summary>
Immutable Secrets and ConfigMaps
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field is a list of references to secrets in the same namespace. You can use it&nbsp;</span><span style="color: rgb(34, 34, 34);">to pass a secret that contains a Docker (or other) image registry password to the kubelet.</span></b>
</summary>
<code>imagePullSecrets</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If the node where a Pod is running has enough of a resource available, it's possible (and allowed) for a container to use more resource than its </span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;for that resource specifies. However, a container is not allowed to use more than its resource&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">.</span></b>
</summary>
request
limit
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
<b>Limits and requests for CPU resources are measured in&nbsp;<em>cpu</em>&nbsp;units. One cpu, in Kubernetes, is equivalent to&nbsp;<strong>1 _____</strong>&nbsp;for cloud providers and&nbsp;<strong>1 _____&nbsp;</strong>on bare-metal Intel processors.</b>
</summary>
<strong>vCPU/Core</strong><strong>
</strong><strong>hyperthread</strong>&nbsp;<strong>
</strong>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The scheduler ensures that, for each resource type, the sum of the resource requests of the scheduled Containers is _____ than the capacity of the node.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">less</span>
</details>

<details>
<summary>
<b>When you run a Pod on a Node, the Pod itself takes an amount of system resources. These resources are additional to the resources needed to run the container(s) inside the Pod. <i>_____&nbsp;</i>is a feature for accounting for the resources consumed by the Pod infrastructure on top of the container requests &amp; limits.
It is set at&nbsp;<a href="https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/#what-are-admission-webhooks">admission</a>&nbsp;time according to the overhead associated with the Pod's&nbsp;<a href="https://kubernetes.io/docs/concepts/containers/runtime-class/">RuntimeClass</a>.
When enabled, the overhead is considered in addition to the sum of container resource requests when scheduling a Pod. Similarly, Kubelet will include the Pod overhead when sizing the Pod cgroup, and when carrying out Pod eviction ranking.</b>
</summary>
<em>Pod Overhead</em>
</details>

<details>
<summary>
<b>Suppose you have several clusters, and your users and components authenticate in a variety of ways. For example:<ul><li>A running kubelet might authenticate using certificates.</li><li>A user might authenticate using tokens.</li><li>Administrators might have sets of certificates that they provide to individual users.</li></ul>With _____ files, you can organize your clusters, users, contexts, and namespaces.</b>
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
<b><span style="color: rgb(34, 34, 34);">Each context has three parameters:&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">cluster, namespace, and user.&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">By default, containers run with unbounded&nbsp;</span><a href="https://kubernetes.io/docs/user-guide/compute-resources">compute resources</a><span style="color: rgb(34, 34, 34);">&nbsp;on a Kubernetes cluster. With _____, cluster administrators can restrict resource consumption and creation on a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces">namespace<span style="background-color: rgb(85, 85, 85); color: rgb(255, 255, 255);"></span></a><span style="color: rgb(34, 34, 34);">&nbsp;basis</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">resource quotas</span>
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
<b><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;are&nbsp;cluster-level resources that control security sensitive aspects of the pod specification. They define</span><span style="color: rgb(34, 34, 34);">&nbsp;a set of conditions that a pod must run with in order to be accepted into the system, as well as defaults for the related fields.</span></b>
</summary>
Pod Security Policy
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
<b>Limit the "testing" namespace to using 1 core and 1GiB RAM. Let the "production" namespace use any amount.
You could create this policy via...</b>
</summary>
ResourceQuota
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
<b>A file that is used to configure access to clusters is called a _____ file</b>
</summary>
kubeconfig
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">default kubeconfig filepath</span></b>
</summary>
$HOME/.kube/config
</details>

<details>
<summary>
<b>A <i>_____&nbsp;</i>provides constraints that can:<ul><li>Enforce minimum and maximum compute resources usage per Pod or Container in a namespace.</li><li>Enforce minimum and maximum storage request per PersistentVolumeClaim in a namespace.</li><li>Enforce a ratio between request and limit for a resource in a namespace.</li><li>Set default request/limit for compute resources in a namespace and automatically inject them to Containers at runtime</li></ul></b>
</summary>
<em>LimitRange</em>&nbsp;
</details>

<details>
<summary>
<b>In a cluster with a capacity of 32 GiB RAM, and 16 cores, let team A use 20 GiB and 10 cores, let B use 10GiB and 4 cores, and hold 2GiB and 2 cores in reserve for future allocation.
You could create this policy via...</b>
</summary>
ResourceQuota
</details>

