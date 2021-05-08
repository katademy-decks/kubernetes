## Cluster Architecture 
<details>
<summary>An object's _____ status field denotes its parent object. If empty, the child object will be garbage collected and removed.</summary>
metadata.ownerReference
<br></details>

<details>
<summary>Managing multiple clusters as one known as _____, requires many considerations to implement, such as cross-cluster DNS, service discovery, loadbalancing and resource sync.</summary>
Cluster federation
<br></details>

<details>
<summary>An object's _____ field is a list of string items which must be removed the list before the object can ever be deleted from the cluster. The permission to remove these items is explicitly given to desired actors.</summary>
metadata.finalizers
<br></details>

<details>
<summary>ClusterRoles can be created by combining other ClusterRoles using an _____</summary>
aggregationRule
<br></details>

<details>
<summary>Selectable and attachable Key/Value pairs on objects such as pods are called _____</summary>
Labels
<br></details>

<details>
<summary>A _____&nbsp;is an extension of the Kubernetes API. Many core Kubernetes functions are now built using them, making Kubernetes more modular.</summary>
<em>custom resource</em>
<br></details>

<details>
<summary>Each of a Service's ports can specify the application protocol to use via the _____ field.</summary>
AppProtocol
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a process in the container tries to consume more than the allowed amount of memory, the system kernel _____ the process that attempted the allocation, with an _____ error</span></summary>
<span style="color: rgb(34, 34, 34);">terminates</span>

OOM (Out of Memory)
<br></details>

<details>
<summary>_____ are key-value pairs that identify resources, and can be used with _____ to match a specified group of resources.</summary>
Labels
Selectors
<br></details>

<details>
<summary>The Kubernetes Master is a collection of three processes that run on a single node in your cluster. These processes are _____</summary>
kube-apiserver, scheduler, kube-controller-manager
<br></details>

<details>
<summary>By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.</summary>
cloud-controller-manager
<br></details>

<details>
<summary>The _____ is the only way to access ExternalName Services.</summary>
Kubernetes&nbsp;DNS server
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Even though health checks are not exposed directly through the Ingress, there exist parallel concepts in Kubernetes such as _____</span><span style="color: rgb(34, 34, 34);">&nbsp;that allow you to achieve the same end result.&nbsp;</span></summary>
readinessProbes
<br></details>

<details>
<summary>In a LoadBalancer service, the _____ annotation removes the double-hop problem by allowing users to define their own balancing.</summary>
OnlyLocal
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In a Kubernetes cluster, the components on the worker nodes - kubelet and kube-proxy - need to communicate with Kubernetes master components, specifically _____.</span></summary>
<span style="color: rgb(34, 34, 34);">kube-apiserver</span>
<br></details>

<details>
<summary>_____ allow you to create your own custom Kubernetes objects, to store any data you wish.&nbsp;</summary>
Custom Resource Definitions (CRDs)
<br></details>

<details>
<summary>A _____ is like a virtual cluster inside the Kubernetes cluster.</summary>
namespace
<br></details>

<details>
<summary>Kubernetes system processes are inside the _____ namespace</summary>
kube-system
<br></details>

<details>
<summary>Public data in the Kubernetes cluster is inside the _____ namespace.</summary>
kube-public
<br></details>

<details>
<summary>Can you use K8S resources across namespaces?</summary>
No - except Services.
<br></details>

<details>
<summary>The command kubectl _____ shows global (non-namespaced) resources.</summary>
kubectl api-resources --namespaced=false
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">For some Services, you need to expose more than one port. Kubernetes lets you configure multiple port definitions on a Service object. When using multiple ports for a Service, you must give all of your ports _____ so that these are unambiguous.</span></summary>
<span style="color: rgb(34, 34, 34);">names</span>
<br></details>

<details>
<summary>The _____ service type exposes the Service externally using a cloud provider�s load balancer.</summary>
LoadBalancer
<br></details>

<details>
<summary>The component that creates, annotates, destroys nodes and gets their information (like hostname, address or health) is called the...</summary>
Node controller
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ is a daemon that embeds the core control loops shipped with Kubernetes.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">kube-controller-manager</span>
<br></details>

<details>
<summary>All API usage from nodes and pods terminate at the following control plane components:</summary>
apiserver only.
<br></details>

<details>
<summary>A <b>Service </b>can map any incoming port to a _____. By default and for convenience, it has the same value as the port field.</summary>
targetPort
<br></details>