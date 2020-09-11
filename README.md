# Kubernetes FAQ

Learn Kubernetes by answering simple questions! [Flashcards](https://github.com/devsplit/kubernetes/releases/) included for spaced repetition.

### Table of Contents

1. [Admission](#admission)
1. [Auditing](#auditing)
1. [Authentication](#authentication)
1. [Authorization](#authorization)
1. [Cluster Architecture](#cluster-architecture)
1. [Cluster Security](#cluster-security)
1. [Configuration](#configuration)
1. [Container Security](#container-security)
1. [Deployments](#deployments)
1. [Nodes](#nodes)
1. [Pods](#pods)
1. [Services](#services)
1. [Storage](#storage)
1. [etcd](#etcd)

## Admission 
<details>
<summary><span style="color: rgb(34, 34, 34);">Admission Control Modules are software modules that can _____ or _____ requests.</span></summary>
<span style="color: rgb(34, 34, 34);">modify</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">reject</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Admission Control Modules can access the contents of the Kubernetes object that is being _____ or _____.</span></summary>
<span style="color: rgb(34, 34, 34);">created&nbsp;</span>
<span style="color: rgb(34, 34, 34);">
</span>modified
<br></details>

<details>
<summary>Can Admission controllers act on requests that create an object?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that delete an object?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that connect (proxy) to an object?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that read an object?</span></summary>
No
<br></details>

<details>
<summary>An admission controller module rejects a request. What happens to the request?</summary>
It is immediately rejected.
<br></details>

<details>
<summary>Can admission controllers set complex defaults for fields?</summary>
Yes
<br></details>

<details>
<summary>Does the admission or validation of a request happen first?</summary>
admission
<br></details>

<details>
<summary>Can resource quotas improve security by preventing internal denial of service attacks?</summary>
Yes
<br></details>

<details>
<summary>Open Policy Agent can manage your _____ controllers in order to block K8S features (like being able to run containers as root) from multiple teams.</summary>
admission&nbsp;
<br></details>

<details>
<summary>Is admission control's NodeRestriction enabled by default?</summary>
No!
<br></details>


## Auditing 
<details>
<summary>Kubernetes _____ provides a security-relevant chronological set of records documenting the sequence of activities that have affected system by individual users, administrators or other components of the system.</summary>
auditing
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit records begin their lifecycle inside the _____ Kubernetes</span><span style="color: rgb(34, 34, 34);">&nbsp;component.</span></summary>
<a href="https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/">kube-apiserver</a>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Each request on each stage of its execution generates an audit _____, which is then pre-processed according to a certain policy and written to a backend.</span></summary>
<span style="color: rgb(34, 34, 34);">event</span>
<br></details>

<details>
<summary>Audit logging usually _____ the memory consumption of the API server because some context required for auditing is stored for each request.</summary>
increases&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit _____ objects define rules about what events should be recorded and what data they should include.</span></summary>
<span style="color: rgb(34, 34, 34);">policy</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When an event is processed, it's compared against the list of Audit Policy rules in order. The first matching rule sets the "_____" of the event.</span></summary>
<span style="color: rgb(34, 34, 34);">audit level</span>
<br></details>

<details>
<summary>The four audit levels are:
_____&nbsp;- don't log these events._____&nbsp;- log request metadata (requesting user, timestamp, resource, verb, etc.)&nbsp;_____&nbsp;- log event metadata and request body._____&nbsp;- log event metadata, request body and response bodies.</summary>
None
Metadata
Request
RequestResponse
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit _____ persist audit events to an external storage.</span></summary>
<span style="color: rgb(34, 34, 34);">backends</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ audit backend writes event to a disk</span></summary>
log
<br></details>

<details>
<summary>Can you use log collectors like fluentd to collect/distribute Kubernetes audit events from log files?</summary>
Yes
<br></details>

<details>
<summary>Can you use log collectors like logstash to collect/distribute Kubernetes audit events from the webhook audit backend?</summary>
Yes
<br></details>

<details>
<summary>Kubernetes _____ allows cluster administrators to learn about the context of clusters events: What happened, when, where, who initiated it and from where.</summary>
auditing
<br></details>

<details>
<summary>The audit _____ determines what events are recorded and which backends (logs or webhooks) persist the records.</summary>
policy&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ audit backend sends events to an external API.</span></summary>
webhook
<br></details>

<details>
<summary>_____ failures might suggest a misconfigured service account, or the presence of an attacker.</summary>
RBAC audit
<br></details>

<details>
<summary>What are some tools with which clusters can be audited?</summary>
Sonobuoy
<br></details>


## Authentication 
<details>
<summary>Suppose you have several clusters, and your users and components authenticate in a variety of ways. For example:<ul><li>A running kubelet might authenticate using certificates.</li><li>A user might authenticate using tokens.</li><li>Administrators might have sets of certificates that they provide to individual users.</li></ul>With _____ files, you can organize your clusters, users, contexts, and namespaces.</summary>
kubeconfig
<br></details>

<details>
<summary>A file that is used to configure access to clusters is called a _____ file</summary>
kubeconfig
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">element in a kubeconfig file is used to group access parameters under a convenient name.</span></summary>
context
<br></details>

<details>
<summary>The&nbsp;KUBECONFIG&nbsp;environment variable holds a list of _____</summary>
kubeconfig files
<br></details>

<details>
<summary>The command _____ finds the clusters available to you inside your kubeconfig file.</summary>
kubectl config get-contexts
<br></details>

<details>
<summary>Kubernetes authentication examines the incoming HTTP request's _____ and _____.</summary>
headers
certificate
<br></details>

<details>
<summary>Are Client Certificates a valid authentication module?</summary>
Yes
<br></details>

<details>
<summary>Are passwords a valid Kubernetes authentication module?</summary>
Yes
<br></details>

<details>
<summary>Are plain, bootstrap and JWT tokens a valid Kubernetes authentication module?</summary>
Yes
<br></details>

<details>
<summary>If a request cannot be authenticated, it is rejected with status code _____</summary>
401
<br></details>

<details>
<summary>Although Kubernetes uses "_____" for access control decisions and logging, it does not store or even define any concrete "user" object.</summary>
usernames&nbsp;
<br></details>

<details>
<summary>Kubernetes has two categories of users: _____ and _____.</summary>
normal users and service accounts
<br></details>

<details>
<summary>Can normal users be added to a cluster through an API call?</summary>
No
<br></details>

<details>
<summary>What is the Kubernetes API object that represents a normal user?</summary>
There is none!
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Any request that presents a valid certificate signed by _____ is considered authenticated.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">the cluster's certificate authority (CA)</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____ are users managed by the Kubernetes API.</span></summary>
<span style="color: rgb(34, 34, 34);">Service accounts</span>
<br></details>

<details>
<summary>Are service accounts bound to specific namespaces?</summary>
Yes
<br></details>

<details>
<summary>Service accounts are tied to a set of credentials stored as _____, which are mounted into _____ allowing in-cluster processes to talk to the Kubernetes API.</summary>
Secrets
pods
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">API requests are tied to either a normal user or a service account, or are treated as _____</span><span style="color: rgb(34, 34, 34);">.</span></summary>
<a href="https://kubernetes.io/docs/reference/access-authn-authz/authentication/#anonymous-requests">anonymous requests</a>
<br></details>

<details>
<summary>Are client certificates a valid authentication method?</summary>
Yes
<br></details>

<details>
<summary>Are bearer tokens a valid authentication method?</summary>
Yes
<br></details>

<details>
<summary>Are authentication proxies a valid authentication method?</summary>
Yes
<br></details>

<details>
<summary>Is basic auth a valid authentication method?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____&nbsp;</span><span style="color: rgb(34, 34, 34);">are a set of strings, each of which indicates the user's membership in a named logical collection of users.</span></summary>
<span style="color: rgb(34, 34, 34);">Groups</span><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details>

<details>
<summary>You can enable multiple authentication methods at once. You should usually use at least two methods: one for _____ and one for _____.</summary>
normal users

service accounts
<br></details>

<details>
<summary>The _____&nbsp;group is included in the list of groups for all authenticated users.</summary>
system:authenticated&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Authentication protocols (LDAP, SAML, Kerberos, etc) can be integrated by using an _____</span><span style="color: rgb(34, 34, 34);">&nbsp;or _____</span></summary>
<a href="https://kubernetes.io/docs/reference/access-authn-authz/authentication/#authenticating-proxy">authenticating proxy</a>
<a href="https://kubernetes.io/docs/reference/access-authn-authz/authentication/#webhook-token-authentication">authentication webhook</a>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">By default, requests to the kubelet's HTTPS endpoint that are not rejected by other configured authentication methods are treated as _____ requests.</span></summary>
<span style="color: rgb(34, 34, 34);">anonymous</span>
<br></details>

<details>
<summary>Your cluster user credentials can be found in _____ on your local machine.</summary>
kubeconfig
<br></details>

<details>
<summary>Your current, in-use cluster is stored in _____ on your local machine.</summary>
the kubeconfig file
<br></details>

<details>
<summary>Your current, in-use cluster namespace is stored in _____ on your local machine.</summary>
the kubeconfig file
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Kubernetes determines the username of an incoming request from the common name field in the subject field of the _____ (e.g., "/CN=IcelynJennings")</span></summary>
<span style="color: rgb(34, 34, 34);">certificate</span>
<br></details>

<details>
<summary>The command _____ lists service accounts.</summary>
<i>kubectl get sa</i>
<br></details>


## Authorization 
<details>
<summary>A better alternative to applying RBAC resources, is the command _____. It causes semantically-aware merging of rules and subjects. Missing objects/namespaces are created if required.</summary>
kubectl auth reconcile
<br></details>

<details>
<summary>The _____ and _____ Objects contain sets of additive authorization permissions</summary>
Role and ClusterRole
<br></details>

<details>
<summary>A _____ grants a role's permissions to a set of users, groups or service accounts.</summary>
RoleBinding
<br></details>

<details>
<summary>Pods that need to connect to the apiserver can automatically inject the _____ certificate and valid _____ into themselves via a service account.&nbsp;</summary>
public root
bearer token
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">After the request is authenticated as coming from a specific user, the request must be _____.</span></summary>
<span style="color: rgb(34, 34, 34);">authorized</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A request must include the _____ of the requester, the requested _____, and the _____ affected by the action.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">username&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">action</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">object</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When an administrator creates a cluster, they configure the authorization modules that should be used in the API server. The default ones are</span><span style="color: rgb(34, 34, 34);">&nbsp;_____, _____, and _____.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">ABAC</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">RBAC</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Webhook</span>
<br></details>

<details>
<summary>If a request is authorized by an authorization module, does it get checked by other authorization modules before proceeding?</summary>
No - it's immediately authorized.
<br></details>

<details>
<summary>Does a user need a Role and RoleBinding to access Kubernetes resources?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Kubernetes authorizes API requests at the _____</span></summary>
kube-apiserver
<br></details>

<details>
<summary>An attacker authorized to create objects can escalate their privileges further by creating _____ that can read secrets and edit their privileges, or that run under a _____ with greater permissions.</summary>
pods&nbsp;
serviceaccount
<br></details>

<details>
<summary>Is Kubelet RBAC enabled by default?</summary>
No!!!
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A request is authorized if an existing policy declares that the user has permissions to complete the requested _____.</span></summary>
action
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An authorization request is denied with status code _____</span></summary>
403
<br></details>

<details>
<summary>Pods that do not need to use the api server should have their default _____ disabled for security.</summary>
service account
<br></details>

<details>
<summary>Is RBAC enabled for a new cluster by default?</summary>
No!
<br></details>


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


## Cluster Security 
<details>
<summary>Nodes should be provisioned with valid client credentials and&nbsp;a _____ certificate&nbsp;to connect to the apiserver.</summary>
public root certificate
<br></details>

<details>
<summary>Does the <b>apiserver</b> verify the <b>kubelet's</b> serving certificate by default?</summary>
No. The connection is subject to MITM attacks by default.
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The kubelet uses _____ for authenticating to the Kubernetes API.</span></summary>
<span style="color: rgb(34, 34, 34);">certificates (with&nbsp;</span><span style="color: rgb(34, 34, 34);">1 year expiration)</span>
<br></details>

<details>
<summary>kubelet _____ is a feature that automatically generates a new key and requests a new certificate from the Kubernetes API before the current certificate's expiration.</summary>
certificate rotation
<br></details>

<details>
<summary>The _____ kubelet flag controls its automatic certificate rotation.</summary>
--rotate-certificates
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The command _____ views the status of certificate signing requests.</span></summary>
kubectl get csr
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A kubelet's certificate signing request (CSR) will initially have a status of&nbsp;</span><code>Pending</code><span style="color: rgb(34, 34, 34);">. If the CSR meets specific criteria, it will become&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><code>Approved&nbsp;</code><span style="color: rgb(34, 34, 34);">by the _____</span></summary>
<span style="color: rgb(34, 34, 34);">kube controller manager</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Whenever a kubelet retrieves a new signed certificate from the Kubernetes API it will write it to the _____</span></summary>
disk
<br></details>

<details>
<summary>When a kubelet starts, it looks for its _____ file, retrieves the _____ URL and credentials (normally a TLS key and signed cert), then attempts to communicate to it.</summary>
kubeconfig
kube-apiserver
<br></details>

<details>
<summary>A kubelet's kubeconfig file requires _____ inside it to connect to kube-apiserver.</summary>
a key and a cert
<br></details>

<details>
<summary>Does a kubelet's kubeconfig require a certificate signed by a CA (Certificate Authority) trusted by kube-apiserver?</summary>
Yes
<br></details>

<details>
<summary>Do you need to distribute a CA certificate to each kubelet?</summary>
No - only the master nodes where kube-apiserver is running.
<br></details>

<details>
<summary>Do you need to distribute a key and signed certificate for each kubelet?</summary>
Yes - ideally unique ones.
<br></details>

<details>
<summary>A Certificate Authority _____ and _____ are required to sign kubelet certificates.</summary>
key and certificate
<br></details>

<details>
<summary>A kubelet's initial bootstrap credentials for TLS can be either authentication file _____, or "bootstrap".</summary>
tokens
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When TLS bootstrapping, the kubelet must be able to authenticate as a user with the rights to create and retrieve _____</span></summary>
CSRs
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In order to approve CSRs, you allow the _____ to approve them.</span></summary>
<span style="color: rgb(34, 34, 34);">kube-controller-manager</span>
<br></details>

<details>
<summary>Kubelet's _____ kubeconfig field points to a CA file used to validate the server certificate presented by kube-apiserver.</summary>
certificate-authority
<br></details>

<details>
<summary>The command _____ approves a CSR.</summary>
kubectl certificate approve &lt;cert&gt;
<br></details>

<details>
<summary>The command _____ denies a CSR.</summary>
kubectl certificate deny &lt;cert&gt;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Once Cluster TLS is established, incoming requests can begin the _____ step when trying to communicate to the cluster.</span></summary>
<span style="color: rgb(34, 34, 34);">Authentication</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a request reaches kube-api-server, it goes through several stages: _____, _____, and _____</span></summary>
Authentication, Authorization, Admission Control<img src="access-control-overview.svg">
<br></details>

<details>
<summary>The _____&nbsp;<span style="color: rgb(34, 34, 34);">resource type allows a client to ask for an X.509 certificate be issued, based on a signing request.</span></summary>
<em>CertificateSigningRequest</em>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ resource is used to request that a certificate be signed by a denoted signer, after which the request may be approved or denied before finally being signed.</span></summary>
<span style="color: rgb(34, 34, 34);">CertificateSigningRequest (CSR)</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The CertificateSigningRequest object includes a _____-encoded PKCS#10 signing request in the&nbsp;</span><code>spec.request</code><span style="color: rgb(34, 34, 34);">&nbsp;field.</span></summary>
<span style="color: rgb(34, 34, 34);">PEM</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The CertificateSigningRequest denotes the </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">(the recipient that the request is being made to) using the&nbsp;</span><code>spec.signerName</code><span style="color: rgb(34, 34, 34);">&nbsp;field.</span></summary>
<em>signer</em><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Once created, a CertificateSigningRequest must be approved before it can be _____.</span></summary>
<span style="color: rgb(34, 34, 34);">signed</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A normal user must have a certificate issued by the Kubernetes Cluster, and then present it to the API call as the&nbsp;</span><span style="color: rgb(34, 34, 34);">Certificate&nbsp;</span><span style="color: rgb(34, 34, 34);">_____, or through the kubectl.</span></summary>
<span style="color: rgb(34, 34, 34);">Header</span>
<br></details>

<details>
<summary>A CSR object requires a request value, which can be generated via _____ for example.</summary>
openssl
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Kubernetes requires _____ certificates for authentication over TLS.</span></summary>
<span style="color: rgb(34, 34, 34);">PKI&nbsp;</span>
<br></details>

<details>
<summary>PKI certificates are usually stored in the _____ directory.</summary>
/etc/kubernetes/pki
<br></details>

<details>
<summary>Can network segmentation improve Kubernetes security?</summary>
Yes
<br></details>

<details>
<summary>The API server should have a _____ restricting it to be accessible only by specific IPs.</summary>
firewall
<br></details>

<details>
<summary>Should you rotate your kubelet certs periodically?</summary>
Yes
<br></details>

<details>
<summary>A _____ like Istio can trace and profile requests inside a cluster. An administrator can then disable the possibility to make requests that aren't expect to ever happen.</summary>
service mesh
<br></details>

<details>
<summary>Can service meshes encrypt in-cluster traffic (and automatically rotate certificates)?</summary>
Yes
<br></details>

<details>
<summary>Tools like _____ can benchmark your cluster.</summary>
kube-bench
<br></details>

<details>
<summary>Once an attacker has control of your Kubernetes node, can they potentialy access the cloud provider's _____ to exfiltrate credentials to your cloud account.</summary>
user and metadata APIs
<br></details>

<details>
<summary>Which K8S object can prevent an attacker inside a pod from running the services of another pod?</summary>
NetworkPolicy
<br></details>

<details>
<summary>A public image registry might be compromised, so it is useful to use _____ registries.</summary>
dedicated, private
<br></details>

<details>
<summary>Does a service mesh make your workloads more isolated by default?</summary>
Yes
<br></details>

<details>
<summary>_____ objects require a specific backend running in the cluster that implements them, such as Calico or Flannel.</summary>
NetworkPolicy
<br></details>

<details>
<summary>A _____ object can divide your apps into in-cluster network tiers, locking them by default, with the ability specifically allow communication between them, or between namespaces.</summary>
NetworkPolicy
<br></details>

<details>
<summary>A NetworkPolicy uses _____ to specify how groups of pods&nbsp;are allowed to communicate with each other and other network endpoints.</summary>
labels
<br></details>

<details>
<summary>NetworkPolicies don't usually conflict each other. If<span style="color: rgb(34, 34, 34);">&nbsp;several policies select a pod, it becomes restricted to what is allowed by the _____ of those policies' ingress/egress rules.</span></summary>
<span style="color: rgb(34, 34, 34);">union</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Once there is any _____ in a namespace selecting a particular pod, that pod will reject any connections that are not allowed by it.</span></summary>
<span style="color: rgb(34, 34, 34);">NetworkPolicy</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can secure an Ingress by specifying a</span><span style="color: rgb(34, 34, 34);">&nbsp;Secret&nbsp;</span><span style="color: rgb(34, 34, 34);">that contains a TLS _____ and _____.</span></summary>
<span style="color: rgb(34, 34, 34);">private key and certificate</span>
<br></details>


## Configuration 
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


## Container Security 
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
<summary><i>_____ </i>objects&nbsp;contain senstivie aspects of pod specification, such as the conditions they must meet or their default fields.</summary>
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


## Deployments 
<details>
<summary>Jobs on a repeating schedule are called _____</summary>
CronJobs
<br></details>

<details>
<summary>One CronJob object is like one line of a _____ file. It runs a job periodically on a given schedule, written in Cron format.</summary>
crontab
<br></details>

<details>
<summary>Can CronJobs be used for running backups?</summary>
Yes
<br></details>

<details>
<summary>Because it is not guaranteed only one job will launch per execution time of its schedule, Jobs should be&nbsp;<i>_____&nbsp;</i></summary>
idempotent
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A CronJob is counted as _____ if it&nbsp;</span><span style="color: rgb(34, 34, 34);">has failed to be created at its scheduled time.</span></summary>
missed
<br></details>

<details>
<summary>A job's default parallelism value is 1.<span style="color: rgb(34, 34, 34);">&nbsp;If it is set to _____ instead, then the Job&nbsp;</span><span style="color: rgb(34, 34, 34);">is paused until it is increased.</span></summary>
0
<br></details>

<details>
<summary>A job's _____ is&nbsp;<span style="color: rgb(34, 34, 34);">the number of Job pods running at any instant.</span></summary>
parallelism
<br></details>

<details>
<summary>A Kubernetes&nbsp;resource which ensures that all (or some)&nbsp;Nodes run a copy of a Pod is the _____</summary>
DaemonSet
<br></details>

<details>
<summary>What will happen to ReplicaSet pods inside a node when that node gets deleted?</summary>
These pods will be replaced on another node, or nodes.
<br></details>

<details>
<summary>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</summary>
sticky identity
<br></details>

<details>
<summary>An application requires several of the following:<ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>Which workload object could work best?</summary>
StatefulSet
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Will deleting or scaling a StatefulSet down also delete&nbsp;</span><span style="color: rgb(34, 34, 34);">the volumes associated with it?</span></summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet is linked to its Pods via their _____ field.</span><span style="color: rgb(34, 34, 34);">&nbsp;It's through this link that the ReplicaSet knows of the state of the Pods it is maintaining and plans accordingly.</span></summary>
metadata.ownerReferences
<br></details>

<details>
<summary>_____&nbsp;<span style="color: rgb(34, 34, 34);">is an object which can own ReplicaSets and update them and their Pods via declarative, server-side rolling updates.</span></summary>
Deployment
<br></details>

<details>
<summary>Is running a logs collection daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary>Can you perform a rolling update on a DaemonSet?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ provides a TTL (time to live) mechanism to limit the lifetime of resource objects that have finished execution.</span></summary>
<span style="color: rgb(34, 34, 34);">TTL controller</span>
<br></details>

<details>
<summary>All CronJob schedules are based on the timezone of _____</summary>
the <b>kube-controller-manager</b>.
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a CronJob's&nbsp;</span><code>concurrencyPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;is set to&nbsp;</span><code>Forbid,</code><span style="color: rgb(34, 34, 34);">&nbsp;and it attempted to be scheduled when there was a previous schedule still running, then it would count as _____.</span></summary>
missed
<br></details>

<details>
<summary>The number of old ReplicaSets to retain for rollback is defined in a deployment's .spec._____</summary>
revisionHistoryLimit
<br></details>

<details>
<summary>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about the _____ and _____of these Pods</summary>
ordering and uniqueness
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, you should deploy your application using a _____ - a&nbsp;</span><span style="color: rgb(34, 34, 34);">workload object that provides a set of stateless replicas.</span></summary>
Deployment
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A ReplicaSet identifies new Pods to acquire by using its _____.&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;If there is a Pod that has no OwnerReference or the Ow</span>nerReference is not a&nbsp;<a href="https://kubernetes.io/docs/concepts/architecture/controller/">Controller</a>&nbsp;an<span style="color: rgb(34, 34, 34);">d the _____ matches, it will be immediately acquired by said ReplicaSet.</span></summary>
selector
<br></details>

<details>
<summary>Is running a cluster storage daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary>Pods waiting to be scheduled are usually created in <b>Pending </b>state. Are DaemonSet pods created in <b>Pending </b>state?</summary>
No - it is an inconsistency due to being scheduled by the DaemonSet controller.
<br></details>

<details>
<summary>When <b>Pod preemption</b> is enabled, does the DaemonSet controller consider <b>pod priority</b> and <b>preemption </b>when making scheduling decisions?</summary>
No - <b>Pod preemption</b> is handled by the <b>default scheduler</b>, DaemonSet pods are scheduled by the <b>DaemonSet controller</b>.
<br></details>

<details>
<summary>If node labels are changed, the DaemonSet will _____ Pods to newly matching nodes.</summary>
Add
<br></details>

<details>
<summary>If node labels are changed, the DaemonSet will _____ Pods from newly not-matching nodes.</summary>
Delete
<br></details>

<details>
<summary>Can CronJobs be used for sending e-mails?</summary>
Yes
<br></details>

<details>
<summary>The Job Controller counts how many jobs had missed in the last X seconds, but only if a CronJob's _____ field<b>&nbsp;</b>is set.</summary>
startingDeadlineSeconds&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ creates one or more Pods and ensures that a specified number of them successfully terminate.&nbsp;</span><span style="color: rgb(34, 34, 34);">As pods successfully complete, it tracks the successful completions until a certain number of successful completions is reached.</span></summary>
<span style="color: rgb(34, 34, 34);">Job</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">For </span>a&nbsp;fixed completion count<span style="color: rgb(34, 34, 34);">&nbsp;Job, you should set its .spec._____ field</span></summary>
completions
<br></details>

<details>
<summary>A _____&nbsp;ensures that all (or some) Nodes run a copy of a Pod.</summary>
DaemonSet
<br></details>

<details>
<summary>What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</summary>
These pods will be garbage collected
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____. Although its Pods are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
<br></details>

<details>
<summary>Is running a node monitoring daemon on every node a valid DaemonSet use case?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Normally, the node that a Pod runs on is selected by the Kubernetes scheduler. However, DaemonSet pods are created and scheduled by _____ instead.</span></summary>
<span style="color: rgb(34, 34, 34);">the DaemonSet controller</span>
<br></details>

<details>
<summary>DaemonSets are similar to Deployments in that they both...</summary>
<span style="color: rgb(34, 34, 34);">create Pods, with processes which are not expected to terminate (web servers, storage servers etc).</span>
<br></details>

<details>
<summary>Every dependent (i.e. owned) object has a metadata._____&nbsp;field that points to the owning object. The owning object is usually a&nbsp;Job, CronJob,&nbsp;Deployment, DaemonSet,&nbsp;StatefulSet,&nbsp;ReplicationController, ReplicaSet.</summary>
ownerReferences
<br></details>

<details>
<summary>Identical Pods in a deployment are referred to as _____</summary>
Replicas
<br></details>

<details>
<summary>_____ run a Pod a specified number of times before completing. _____ run a Pod periodically at specified times.</summary>
Jobs
CronJobs
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Deployment&nbsp;</span><span style="color: rgb(34, 34, 34);">is supposed to have 5 pods at any given time, with</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">If a PodDisruptionBudget allows for there to be 4 at a time, then how many pods at a time are allowed to be voluntarily disrupted by the Eviction API?</span></summary>
<span style="color: rgb(34, 34, 34);">One</span>
<br></details>

<details>
<summary>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</summary>
<b>No!&nbsp;</b><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec.</span>
<br></details>

<details>
<summary>When deleting a DaemonSet with kubectl, you can specify the flag _____, then the Pods will remain on the nodes.&nbsp;</summary>
--cascade=false
<br></details>

<details>
<summary>Given that you can start daemon processes on a node directly via systemd, why use a DaemonSet?</summary>
<ul><li>Ability to monitor and manage logs for daemons in the same way as applications.</li><li>Same config language and tools (e.g. Pod templates,&nbsp;<code>kubectl</code>) for daemons and applications.</li><li>Running daemons in containers with resource limits increases isolation between daemons from app containers. However, this can also be accomplished by running the daemons in a container but not in a Pod (e.g. start directly via Docker).</li></ul>
<br></details>

<details>
<summary>_____ allow you to schedule one copy of a Pod on every node (for example, a logging agent).</summary>
DaemonSets
<br></details>

<details>
<summary>_____ start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.</summary>
StatefulSets&nbsp;
<br></details>

<details>
<summary>Does deleting deployments or pods bypass PodDisruptionBudgets?</summary>
Yes
<br></details>

<details>
<summary>Minimum time in seconds for which a new pod should be ready to be considered available is defined in deployment.spec._____</summary>
minReadySeconds
<br></details>

<details>
<summary>The count of hash collisions for a deployment is stored in its deployment.deploymentstatus._____ status field. It is used for collision avoidance.</summary>
collisionCount
<br></details>

<details>
<summary>_____ differ from Deployments in that Pods are created sequentially, each given an incrementing index number.&nbsp;</summary>
StatefulSets
<br></details>


## Nodes 
<details>
<summary>The 3 possible values for volume.spec.accessMode are:
_____ - Can be used by 1 node_____ - Can be used by many nodes_____ - Can be read from many nodes</summary>
<b>ReadWriteOnce</b>
<b>ReadWriteMany</b>
<b>ReadOnlyMany</b>
<br></details>

<details>
<summary>_____ allow a node to repel a set of Pods, based on certain properties of the node.</summary>
Taints
<br></details>

<details>
<summary>A _____ is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster.&nbsp;</summary>
Node
<br></details>

<details>
<summary>To prevent a kubelet from self-registering the node in the control-plane, you could pass the _____ flag.</summary>
--register-node=false
<br></details>

<details>
<summary>A node's _____ condition<b>&nbsp;</b>is True when its disk capacity is low</summary>
DiskPressure
<br></details>

<details>
<summary>A Node's <b>_____ </b>condition&nbsp;is True when the node's memory is low</summary>
MemoryPressure&nbsp;&nbsp;
<br></details>

<details>
<summary>A Node's <b>_____ </b>condition is&nbsp;True when there are too many processes running.</summary>
PIDPressure
<br></details>

<details>
<summary>A Node's <b>_____&nbsp;</b>condition is True when its network is not correctly configured</summary>
<b>NetworkUnavailable</b>
<br></details>

<details>
<summary>Node heartbeats are sent by...</summary>
kubelet
<br></details>

<details>
<summary>The .spec.____ field is a preference-order list of Node labels, which will be used to sort endpoints when accessing this Service. Traffic will be directed to a Node whose value for the first label matches the originating Node's value for that label. If there is no backend for the Service on a matching Node, then the second label will be considered, and so forth, until no labels remain.</summary>
topologyKeys
<br></details>

<details>
<summary>A Node's "Ready" status is False when...</summary>
It's unhealthy and not accepting pods
<br></details>

<details>
<summary>A _____ is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster.</summary>
Node
<br></details>

<details>
<summary>A node's _____ contains four domains of information - its Addresses, Conditions, Capacity/Allocatable and Info.</summary>
status
<br></details>

<details>
<summary>Addresses in a node's status include...</summary>
HostName, InternalIP, ExternalIP
<br></details>

<details>
<summary>Capacity fields describe the total amount of _____ that a Node has</summary>
resources
<br></details>

<details>
<summary>The Kubernetes control plane component that manages various aspects of nodes is the...</summary>
Node controller
<br></details>

<details>
<summary>The three roles of the <b>Node Controller </b>in a Node's life</summary>
CIDR block assignment

Synchronize internal list of nodes
Node health monitoring
<br></details>

<details>
<summary>Two types of node Heartbeats</summary>
NodeStatus updates
Lease Object
<br></details>

<details>
<summary>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</summary>
operating system
node component versions
<br></details>

<details>
<summary>_____ enables a service to route traffic based upon the Node topology of the cluster.&nbsp;</summary>
Service Topology
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone by using _____</span></summary>
Service Topology
<br></details>

<details>
<summary>A Node's "Ready" status is Unknown when...</summary>
40 seconds have passed since the Node Controller has heard from the node
<br></details>

<details>
<summary>In terms of network, the Node Controller assigns a _____ to a Node upon its registration.</summary>
CIDR block
<br></details>

<details>
<summary>Which Kubernetes component is responsible for a node's self-registration into the control plane?</summary>
kubelet
<br></details>

<details>
<summary>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b>
What happens to the Pods on the node?</summary>
All Pods on the node are scheduled for deletion by the node controller
<br></details>

<details>
<summary>Allocatable describes the amount of the Node's resources that are _____</summary>
available to be consumed by Pods
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If an incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></summary>
bypassed
<br></details>

<details>
<summary>You can control Service traffic routing by specifying the .spec._____&nbsp;field.&nbsp;</summary>
topologyKeys&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice's Endpoints can contain labels about its topology information, such as...</span></summary>
Node - kubernetes.io/hostnameZone - topology.kubernetes.io/zoneRegion - topology.kubernetes.io/region
<br></details>

<details>
<summary>A Node's "Ready" status is True when...</summary>
It's healthy and accepts pods
<br></details>

<details>
<summary>_____ are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won�t be scheduled on nodes with them.</summary>
Taints
<br></details>

<details>
<summary>The kubernetes components inside a worker node are...</summary>
kubelet, kube-proxy, container runtime
<br></details>

<details>
<summary>_____ allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.</summary>
Tolerations
<br></details>

<details>
<summary>Pod _____ express a preference for Pods to be scheduled on the same node as other Pods, when they benefit from it.</summary>
affinities
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler&nbsp;</span><span style="color: rgb(34, 34, 34);">tries to place a _____ number of Pods into each topology domain</span></summary>
balanced
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can use </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;to control&nbsp;</span><span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains&nbsp;</span><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains).</span></summary>
topology spread constraints
<br></details>

<details>
<summary><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one&nbsp;<b>topologyKey&nbsp;</b>and have identical values for that label, the scheduler treats both Nodes as being in the same _____&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">topology&nbsp;</span>
<br></details>

<details>
<summary>_____ attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.</summary>
Node affinities
<br></details>

<details>
<summary>While _____ can block a Pod from running on a node, _____ are more like suggestions to the scheduler. You can combine multiple, with different weights.</summary>
hard node affinities
soft node affinities
<br></details>

<details>
<summary>The controller that creates services, endpoints and updates iptables on each node is _____</summary>
kube-proxy
<br></details>

<details>
<summary>The LoadBalancer Service creates an external IP address, but itself does not know any Pod IP's. Instead,&nbsp;it chooses a _____ to send packets to.</summary>
Node
<br></details>

<details>
<summary>A node's _____ tell an incoming packet where in the node to go.</summary>
iptables
<br></details>

<details>
<summary>When running several copies of your Pod for the sake of fault tolerance, the _____ they are running on may still fail. It's important to place your Pods across several of them.</summary>
nodes
<br></details>

<details>
<summary>Restricting access to your cluster _____ can prevent privilege escalation to your cloud provider.</summary>
nodes / VMs (especially master)
<br></details>

<details>
<summary>Node heartbeats are inside the _____ namespace.</summary>
kube-node-lease
<br></details>

<details>
<summary>Are nodes namespaced?</summary>
No
<br></details>

<details>
<summary>Which taints are tolerated by default by Pods?</summary>
None
<br></details>

<details>
<summary>Taints are set on _____</summary>
nodes
<br></details>

<details>
<summary>Tolerations are set on _____</summary>
Pods
<br></details>

<details>
<summary>Do taints and tolerations guarantee which node a Pod will be scheduled to?</summary>
No - you need Node Affinity
<br></details>

<details>
<summary>Every node in a Kubernetes cluster runs a _____, responsible for implementing a form of virtual IP for Services of type other than ExternalName.</summary>
kube-proxy
<br></details>


## Pods 
<details>
<summary>When you run a Pod on a Node, the Pod itself takes an amount of system resources. These resources are additional to the resources needed to run the container(s) inside the Pod.&nbsp;<i>_____&nbsp;</i>is a feature for accounting for the resources consumed by the Pod infrastructure on top of the container requests &amp; limits.</summary>
Pod Overhead
<br></details>

<details>
<summary>Can a Pod have a single IPv4 and IPv6 address assigned?</summary>
Yes - via enabling IPv4/IPv6 dual-stack.
<br></details>

<details>
<summary>Pod Overhead is set at _____&nbsp;time according to the overhead associated with the Pod's _____. When enabled, it is considered in addition to the sum of container resource requests when scheduling a Pod. Similarly, Kubelet will include the Pod overhead when sizing the Pod cgroup, and when carrying out Pod eviction ranking.</summary>
admission
RuntimeClass
<br></details>

<details>
<summary>The _____ ensures a specific number of pod replicas are running at any one time across nodes</summary>
replication controller
<br></details>

<details>
<summary>A Pod can opt out of being modified by PodPresets altogether via the metadata _____ podpreset.admission.kubernetes.io/exclude: "true"</summary>
annotation
<br></details>

<details>
<summary>Containers within a single pod share ____ and _____ resources.</summary>
storage and network
<br></details>

<details>
<summary>Ready, ContainerReady, lastProbeTime, reason. These are the types of latest variable observations of an object's state called _____, used when the details of an observation are not known apriori, or would not apply to all instances of a given Kind.</summary>
Conditions
<br></details>

<details>
<summary>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</summary>
an owner
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called a&nbsp;<i>_____ </i>deletion.</span></summary>
cascading
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When configuring a container, the _____ field allows you t</span><span style="color: rgb(34, 34, 34);">o pass a secret that contains a Docker (or other) image registry password.</span></summary>
imagePullSecrets&nbsp;
<br></details>

<details>
<summary>Does a Service load balance traffic across multiple Pods?</summary>
Yes
<br></details>

<details>
<summary>Containers within a single pod share network resources - _____ and _____</summary>
IP address and port space
<br></details>

<details>
<summary>A _____ is an API resource for injecting additional runtime requirements into a label-selected Pod at creation time.</summary>
Pod Preset
<br></details>

<details>
<summary>A logical group of containers with shared network and storage and specifications for how to run each is called a _____</summary>
Pod
<br></details>

<details>
<summary>Are containers in a Pod automatically co-located and co-scheduled on the same node?</summary>
Yes
<br></details>

<details>
<summary>Can a pod's containers share resources, dependencies, communicate with each other and coordinate their lifecycle?</summary>
Yes
<br></details>

<details>
<summary>A pod's _____ is the high-level summary of where the pod is in its lifecycle.</summary>
phase
<br></details>

<details>
<summary><table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting. This is the _____ phase of a Pod's lifecycle.</td></tr></tbody></table></summary>
Running
<br></details>

<details>
<summary>List all 5 Pod <b>phases</b></summary>
Pending
Running
Succeeded
Failed
Unknown
<br></details>

<details>
<summary>The six fields of a _____ are&nbsp;reason, status, message, type, lastProbeTime, lastTransitionTime.</summary>
PodCondition&nbsp;
<br></details>

<details>
<summary>A Pod's <b>_____&nbsp;</b>condition field provides a unique, one-word reason for the condition's last transition.</summary>
reason&nbsp;
<br></details>

<details>
<summary>The four possible values of a Pod's <b>_____</b>&nbsp;condition field are&nbsp;PodScheduled,&nbsp;Ready,&nbsp;Initialized,&nbsp;ContainersReady</summary>
type
<br></details>

<details>
<summary>If the _____ probe fails, the Pod's IP address&nbsp;is removed from the endpoints of all&nbsp;<b>Services&nbsp;</b>that match the Pod.</summary>
readiness
<br></details>

<details>
<summary>If the _____ probe fails, the container is killed by the kubelet, then subjected to the container's&nbsp;<b>restart policy</b>.</summary>
startup
<br></details>

<details>
<summary>To find out why a container is in&nbsp;<b>Waiting </b>state, you can check its state's <b>_____&nbsp;</b>field</summary>
Reason
<br></details>

<details>
<summary>The _____ hook is executed prior to a container entering its <b>Running </b>state.</summary>
postStart
<br></details>

<details>
<summary>Once bound to a node, will a Pod ever rebound to another node?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></summary>
label selectors
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
<br></details>

<details>
<summary>The annotation to&nbsp;disable PodPreset for a Specific Pod is...</summary>
podpreset.admission.kubernetes.io/exclude: "true"
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></summary>
node labels
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>Do ephemeral containers guarantee execution?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can specify relationships between an owner and dependents by manually setting their .metadata._____ field</span></summary>
ownerReference
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In _____</span><span style="color: rgb(34, 34, 34);">, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents in the background.</span></summary>
background cascading deletion
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In </span><i>_____</i><span style="color: rgb(34, 34, 34);">, the root object first enters a "deletion in progress" state.&nbsp;</span>Once the "deletion in progress" state is set, the garbage collector deletes the object's dependents. Once the garbage collector has deleted all dependents,&nbsp;it deletes the owner object.</summary>
foreground cascading deletion
<br></details>

<details>
<summary>To control the cascading deletion policy, set the _____&nbsp;field on the _____&nbsp;argument when deleting an Object.&nbsp;</summary>
propagationPolicy&nbsp;
deleteOptions
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a Pod cannot be scheduled, the scheduler tries to preempt (evict) lower _____ Pods to make scheduling of the pending Pod possible.</span></summary>
<span style="color: rgb(34, 34, 34);">priority</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ is a non-namespaced object that defines a mapping from a priority class name to the integer value of the priority.</span></summary>
<span style="color: rgb(34, 34, 34);">PriorityClass</span>
<br></details>

<details>
<summary>Is there currently an API standard for whether a Pod is considered sandboxed?</summary>
No -&nbsp;<span style="color: rgb(34, 34, 34);">Sandbox Pods may be identified by the use of a sandboxed runtime (such as gVisor or Kata Containers), but there is no standard definition of what a sandboxed runtime is.</span>
<br></details>

<details>
<summary>_____ optimize a given metric (e.g. CPU utilization) across a set of Pods. They increase or decrease the number of replicas to achieve it.</summary>
Horizontal Pod Autoscalers (HPA)
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A _____ allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">PodPreset</span>
<br></details>

<details>
<summary>_____ restrict the scheduler�s freedom, trading off one application against another.&nbsp;</summary>
Pod affinities
<br></details>

<details>
<summary>Do pods run a single container each?</summary>
Not necessarily. They can run multiple containers.
<br></details>

<details>
<summary>Do Pods each have a unique IP address?</summary>
Yes, for each address family
<br></details>

<details>
<summary><b>Failed </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
<br></details>

<details>
<summary><b>Unknown </b>phase</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
<br></details>

<details>
<summary>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</summary>
a timestamp for when the Pod last transitioned from one status to another.
<br></details>

<details>
<summary>The three possible values for the&nbsp;<b>status</b>&nbsp;Pod condition field are...</summary>
<b>"True"</b>
<b>
</b><b>"False"</b><b>
</b>"<b>Unknown"</b>
<br></details>

<details>
<summary>A probe can have one of three results:</summary>
<b>Success</b>The Container passed the diagnostic
<b>
</b><b>Failure</b>The Container failed the diagnostic<b>
</b><b>Unknown</b>The diagnostic failed, so no action should be taken
<br></details>

<details>
<summary>If a container's _____ probe fails, the container is killed by the kubelet, then subjected to the container's&nbsp;restart policy.</summary>
liveness&nbsp;
<br></details>

<details>
<summary>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe
What will be the state of each probe of the container?</summary>
<b>Success </b>on all of them
<br></details>

<details>
<summary>A _____ probe indicates whether a container is ready to service requests.</summary>
readiness&nbsp;
<br></details>

<details>
<summary>A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;
Do you still need a livenessProbe?</summary>
Not necessarily.&nbsp;
The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;restartPolicy.
<br></details>

<details>
<summary>A container is in the <b>_____&nbsp;</b>state when it has successfully or unsuccessfully completed execution.</summary>
Terminated
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at 5 minutes, and is reset after ten minutes of successful execution.</span></summary>
exponential back-off
<br></details>

<details>
<summary>The degree to which Pods may be unevenly distributed (i.e. t<span style="color: rgb(34, 34, 34);">he maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type) is called the _____</span></summary>
maxSkew
<br></details>

<details>
<summary><b>whenUnsatisfiable </b>possible values:</summary>
<b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span>
<br></details>

<details>
<summary>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring. Do involuntary disruptions count against the budget?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A temporary "_____" container may be ran in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish user-initiated actions such as, t</span>roubleshooting and inspecting services.</summary>
<span style="color: rgb(34, 34, 34);">ephemeral&nbsp;</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">To troubleshoot a hard-to-reproduce bug, you might need to inspect the state of an existing Pod and its containers, or run some arbitrary commands. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">inside an existing Pod.</span></summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container</span>
<br></details>

<details>
<summary>Do ephemeral containers have guaranteed resources?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</summary>
process namespace sharing
<br></details>

<details>
<summary>If you delete an object without deleting its dependents automatically, the dependents are said to become&nbsp;<i>_____</i></summary>
orphaned
<br></details>

<details>
<summary>PodPresets cannot be used to override a Pod�s own configuration, only to fill in settings which the Pod itself _____</summary>
&nbsp;hasn't specified.
<br></details>

<details>
<summary>_____ can inject bits of common configuration into all selected Pods at creation time. For example, you could use it to mount a particular Volume on all matching Pods.</summary>
PodPresets&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A quorum-based application must ensure that the number of running replicas is never brought below the minimum required for a quorum. This can be achieved with a _____</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>A pod represents _____ running in your cluster.</summary>
Processes
<br></details>

<details>
<summary>In terms of Docker constructs, a Pod is modelled as a group of Docker containers with shared _____ and shared _____</summary>
namespaces
filesystem volumes
<br></details>

<details>
<summary><table><tbody><tr><td>A Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created, either still being scheduled or download images. This describes a Pod's _____ phase.</td></tr></tbody></table></summary>
Pending
<br></details>

<details>
<summary><b>Succeeded </b>phase</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
<br></details>

<details>
<summary>A Pod's _____&nbsp;condition field provides a timestamp for when the Pod condition was last probed.</summary>
lastProbeTime&nbsp;
<br></details>

<details>
<summary>The <b>message&nbsp;</b>condition field provides...</summary>
a human-readable message indicating details about the transition from one status to another.
<br></details>

<details>
<summary>A container's _____ probe indicates whether the application in the container has started.</summary>
startup
<br></details>

<details>
<summary>All other probes are disabled until _____ succeeds.</summary>
startupProbe
<br></details>

<details>
<summary>A Pod should only be sent traffic when a probe succeeds. Which probe can achieve this?</summary>
readinessProbe
<br></details>

<details>
<summary>A container is <b>_____&nbsp;</b>when it is neither&nbsp;<b>Running&nbsp;</b>or&nbsp;<b>Terminated</b>. It is likely pulling images, applying secrets etc.</summary>
Waiting
<br></details>

<details>
<summary>A container is in the <b>_____&nbsp;</b>state when it is executing without issues.</summary>
Running
<br></details>

<details>
<summary>To tell why a container is in <b>Terminated </b>state, check its state's&nbsp;<b>_____&nbsp;</b>and&nbsp;<b>_____&nbsp;</b>fields.</summary>
Reason and Exit Code
<br></details>

<details>
<summary>The _____ hook is executed before a container enters Terminated state.</summary>
preStop
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of the .status._____ fields for the Pod.&nbsp;</span>If such a field isn't found, the status of the condition defaults to&nbsp;<b>"False"</b></summary>
conditions
<br></details>

<details>
<summary>Does a Pod's <b>restartPolicy </b>apply to all its containers?</summary>
Yes
<br></details>

<details>
<summary>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></summary>
creation time
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies their _____</span></summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the topology spread constraint is indicated in the _____ field.</span></summary>
<strong>whenUnsatisfiable</strong>
<br></details>

<details>
<summary>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></summary>
replicas
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></summary>
Yes
<br></details>

<details>
<summary>Will an ephemeral container ever be automatically restarted?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____ indicates the importance of a Pod relative to other Pods.</span></summary>
<span style="color: rgb(34, 34, 34);">Priority</span>
<br></details>

<details>
<summary>Critical pods rely on scheduler _____ to be scheduled when a cluster is under resource pressure.</summary>
preemption
<br></details>

<details>
<summary>The _____&nbsp;field indicates that the value of this PriorityClass should be used for Pods without a&nbsp;priorityClassName.&nbsp;Only one such PriorityClass can exist in the system.</summary>
globalDefault
<br></details>

<details>
<summary>Pods with PreemptionPolicy:_____&nbsp;will be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods. It will stay in the scheduling queue, until sufficient resources are free.&nbsp;</summary>
Never
<br></details>

<details>
<summary>PreemptionPolicy&nbsp;defaults to&nbsp;_____, which will allow pods of that PriorityClass to preempt lower-priority pods (as is existing default behavior).&nbsp;</summary>
PreemptLowerPriority
<br></details>

<details>
<summary>_____ repel other Pods instead of attracting. Ex.: One to replicas of the same Pod can help spread your replicas evenly across the cluster.</summary>
anti-affinity
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total. This can be achieved via a _____</span></summary>
PodDisruptionBudget
<br></details>

<details>
<summary>If non-preempting pods cannot be scheduled at a given time, they will be retried with lower frequency, allowing other pods with lower priority to be scheduled before them. This is because non-preempting pods are subject to scheduler...</summary>
back-off
<br></details>

<details>
<summary>The kubelet manages the _____ file for each container of a Pod to prevent Docker from modifying it.</summary>
hosts
<br></details>

<details>
<summary>The three available ImagePullPolicies of a container are Always, Never and _____ (default)</summary>
IfNotPresent
<br></details>

<details>
<summary><code>kubectl exec</code>&nbsp;was insufficient to interactively troubleshoot a container, because it has crashed, and didn't have any debugging utilities.

To troubleshoot, you can use _____ containers.</summary>
Ephemeral containers / busybox
<br></details>

<details>
<summary>.spec._____&nbsp;adds entries to a Pod's /etc/hosts&nbsp;file, overriding its hostname resolution when DNS and other options are not applicable.&nbsp;</summary>
HostAliases
<br></details>

<details>
<summary>A container without a readinessProbe is assumed to be ready for traffic once it starts. What are some potential problems with this?&nbsp;</summary>
The containerised application might need time to start after its enclosing container has. All requests to the app will fail throughout this process, because the container was "Ready" before the app started.
<br></details>

<details>
<summary>If a container crashes inside a pod due to an unrecoverable error (such as a typo in the code), should you signal the liveness probe?</summary>
No. Let it crash by exiting the process, allowing kubelet to restart it.&nbsp;<a href="https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-revisited-how-to-avoid-shooting-yourself-in-the-other-foot/#letitcrash">https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-revisited-how-to-avoid-shooting-yourself-in-the-other-foot/#letitcrash</a>
<br></details>

<details>
<summary>Liveness probes are designed to _____ your containers when stuck, such as in an infinite loop, where there is no way for the process to seek help externally, or even exit.</summary>
restart
<br></details>

<details>
<summary>A stuck process consuming 100% CPU won't reply to _____ probes. If you don't have a _____ probe, it will stay uselessly&nbsp;<em>Running,</em>&nbsp;serving no requests and consuming resources.</summary>
Readiness
Liveness
<br></details>

<details>
<summary>_____ probes are used for recovery when a process is not responsive.</summary>
Liveness&nbsp;
<br></details>

<details>
<summary>Liveness and Readiness probes pointing to the same endpoint inside a container will cause the container to be detached from the Service and deleted at the same time. Is this okay?</summary>
No - it will cause connection drops due to the unready container running out of time to drain its current connections due to being deleted.
<br></details>

<details>
<summary>Should readiness probes be allowed to depend on other services (databases, APIs...) to succeed?</summary>
No&nbsp;<a href="https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-how-to-avoid-shooting-yourself-in-the-foot/#shootingyourselfinthefootwithreadinessprobes">https://blog.colinbreck.com/kubernetes-liveness-and-readiness-probes-how-to-avoid-shooting-yourself-in-the-foot/#shootingyourselfinthefootwithreadinessprobes</a>
<br></details>

<details>
<summary>While it's in its termination grace period, you might want an app to process remaining incoming requests by adding a _____ handler.</summary>
preStop
<br></details>

<details>
<summary>Most applications should log to _____ and send errors to _____, which are then aggregated by another service.</summary>
stdout
stderr
<br></details>

<details>
<summary>Does each Pod have a unique IP?</summary>
Yes
<br></details>

<details>
<summary>A _____ is like a machine with its own IP address and ports, running containers inside which can map their ports to it.</summary>
Pod
<br></details>

<details>
<summary>Does a Pod have its own network namespace inside?</summary>
Yes
<br></details>

<details>
<summary>Does a Pod have its own virtual ethernet connection?</summary>
Yes
<br></details>

<details>
<summary>Is running backups a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>Is running database synchronisation a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>Is running authentication proxies a valid use case for a sidecar container inside a Pod?</summary>
Yes
<br></details>

<details>
<summary>The "pause" container (also called sandbox container) inside each Pod reserves and holds the network _____, enabling containers to communicate with each other and retaining the IP address of the pod.</summary>
namespace (netns)
<br></details>

<details>
<summary>A _____ is an abstract way to expose on the network an application running on a set of Pods.</summary>
service
<br></details>

<details>
<summary>Each Kubernetes Node has its own _____ range from which it assigns its pods unique IPs.</summary>
CIDR IP block
<br></details>


## Services 
<details>
<summary>A _____ is like a virtual server on your cluster.</summary>
Service
<br></details>

<details>
<summary>The service type that&nbsp;<span style="color: rgb(34, 34, 34);">exposes a Service on a cluster-internal IP, making it only reachable from within the cluster is _____</span></summary>
ClusterIP
<br></details>

<details>
<summary>The _____ service type&nbsp;maps the Service to the contents of the _____ field (e.g. foo.bar.example.com), by returning a CNAME record.</summary>
ExternalName
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In order to allow you to choose a port number for your Services, we must ensure that no two Services can collide. Kubernetes does that by allocating each Service its own _____</span></summary>
<span style="color: rgb(34, 34, 34);">IP address.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In some cases, multiple paths within an Ingress will match a request. In those cases precedence will be given first to the _____.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">longest matching path</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In an Ingress, if two paths are still equally matched by a request, precedence will be given to paths with the _____ path type over _____ path type.</span></summary>
exact
prefix
<br></details>

<details>
<summary>The 5 possible ServiceTypes for Kubernetes Service are:
_____ - Exposes as an in-cluster IP (default)_____ - Exposes as a port on each node_____ - Exposes externally via your cloud provider's LB_____ - Maps to the contents of the ExternalName, returns a CNAME record with the value_____</summary>
ClusterIP
NodePort
LoadBalancer
ExternalName
Headless
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice is full</span><span style="color: rgb(34, 34, 34);">&nbsp;once it reaches _____ endpoints (by default), at which point additional EndpointSlices will be created.</span></summary>
<span style="color: rgb(34, 34, 34);">100</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.</span></summary>
Ingress controller
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets currently require manually creating a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods.</span></summary>
headless service
<br></details>

<details>
<summary>A Service for with no ClusterIP, proxying, load-balancing, nor handled by kube-proxy is called _____</summary>
headless
<br></details>

<details>
<summary>The _____ service type exposes a Service on each Node's IP at a static port.</summary>
NodePort
<br></details>

<details>
<summary>The _____ service type&nbsp;exposes the Service externally using a cloud provider's load balancer.</summary>
LoadBalancer
<br></details>

<details>
<summary>EndpointSlices support three address types: _____, _____, _____.</summary>
IPv4, IPv6, Fully Qualified Domain Name
<br></details>

<details>
<summary>_____ resources route requests to different services, depending on a set of rules, for example, matching parts of the request URL.&nbsp;</summary>
Ingress
<br></details>

<details>
<summary>The NodePort type is an extension of the _____ type. So a NodePort service also has a _____ address.</summary>
ClusterIP
<br></details>

<details>
<summary>The LoadBalancer service type is an extension of the _____ type. A LoadBalancer Service has a clusterIP address and one or more _____ values.</summary>
NodePort
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____</span><span style="color: rgb(34, 34, 34);">&nbsp;provide a more scalable alternative to Endpoints, distributing network endpoints across multiple resources.</span></summary>
EndpointSlices
<br></details>

<details>
<summary>To ensure each Service receives a unique IP, an internal allocator atomically updates a global allocation map in _____ prior to creating each Service.</summary>
etcd
<br></details>

<details>
<summary>An Ingress with no rules sends all traffic to a single _____, which is typically a configuration option of the Ingress Controller&nbsp;and is not specified in your Ingress resources. If none of the hosts or paths match the HTTP request in the Ingress objects, the traffic is routed to it.</summary>
default backend
<br></details>

<details>
<summary>It takes time for kube-proxy or the Ingress controller to be notified of endpoint changes. Traffic will then remain flowing to a Pod even after its _____. Graceful _____ is required of an app upon its container being sent a SIGTERM signal, stopping it from accepting new requests, and consecutively closing existing connections.</summary>
termination
connection termination

<a href="https://freecontent.manning.com/handling-client-requests-properly-with-kubernetes/">https://freecontent.manning.com/handling-client-requests-properly-with-kubernetes/</a>
<br></details>

<details>
<summary>An Ingress TLS secret must contain keys named&nbsp;_____&nbsp;that contain the certificate and private key to use for TLS.</summary>
tls.crt&nbsp;and&nbsp;tls.key
<br></details>

<details>
<summary>Can ingress objects terminate TLS connections for your application?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____ exposes HTTP and HTTPS routes from outside the cluster to services</span><span style="color: rgb(34, 34, 34);">&nbsp;within the cluster. Traffic routing is controlled by rules defined on the _____ resource.</span></summary>
Ingress
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An _____ may be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL / TLS, and offer name based virtual hosting.</span></summary>
<span style="color: rgb(34, 34, 34);">Ingress</span>
<br></details>

<details>
<summary>The resources that expose deployments on a network are _____</summary>
Services
<br></details>

<details>
<summary>When you don't need load-balancing and a single Service IP, you can create _____</summary>
headless services
<br></details>

<details>
<summary>Headless services are created by setting the Service's .spec._____ field to _____</summary>
clusterIP

"None"
<br></details>

<details>
<summary>The <b>kubernetes </b>service is configured in all namespaces&nbsp;with virtual IP address that is redirected via _____ to the apiserver.</summary>
kube-proxy
<br></details>

<details>
<summary>Inside a Kubernetes cluster, you might wish to reuse an existing DNS entry, or have legacy systems that are configured for a specific IP address and difficult to re-configure. A Service can specify its own cluster IP address by setting the .spec._____ field.</summary>
clusterIP
<br></details>

<details>
<summary>Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should reference an _____ that contains additional configuration including the name of the controller that should implement it.</summary>
IngressClass&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You may deploy any number of Ingress controllers</span><span style="color: rgb(34, 34, 34);">&nbsp;within a cluster. When you create an ingress, you should annotate each ingress with the appropriate _____&nbsp;</span><span style="color: rgb(34, 34, 34);">to indicate which ingress controller should be used if more than one exists within your cluster.</span></summary>
ingressClass
<br></details>

<details>
<summary>The _____ service type exposes the Service on each Node�s IP at a static port. A ClusterIP Service, to which the it routes, is automatically created.&nbsp;</summary>
NodePort
<br></details>


## Storage 
<details>
<summary>Is a Volume preserved after its Pod's deletion?</summary>
No
<br></details>

<details>
<summary>To use a volume, a Pod specifies what volumes to provide for the Pod in the _____ field,&nbsp;and where to mount those into Containers in the&nbsp;_____&nbsp;field.</summary>
.spec.volumes
.spec.containers[*].volumeMounts&nbsp;
<br></details>

<details>
<summary>Can Volumes have hard links to other Volumes?</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using&nbsp;Storage Classes.</span><span style="color: rgb(34, 34, 34);">&nbsp;It is a resource in the cluster just like a node is a cluster resource.&nbsp;</span></summary>
PersistentVolume&nbsp;
<br></details>

<details>
<summary>A <i>_____&nbsp;</i>is a request for storage by a user.&nbsp;</summary>
PersistentVolumeClaim&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In _____ provisioning, a cluster administrator creates a number of PVs. They carry the details of the real storage, which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption.</span></summary>
static
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A cluster is provisioned with several 50Gi PVs. A PVC requests 100Gi PV. What happens?</span></summary>
<span style="color: rgb(34, 34, 34);">Nothing.&nbsp;</span><span style="color: rgb(34, 34, 34);">The PVC can only be bound once a 100Gi PV is added to the cluster.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a user deletes a PVC in active use by a Pod, the PVC is...</span></summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">PVC removal is postponed until _____</span></summary>
<span style="color: rgb(34, 34, 34);">the PVC is no longer actively used by any Pods.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">&nbsp;PV removal is postponed until...</span></summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the PV is no longer bound to a PVC.</span>
<br></details>

<details>
<summary>A PV or a PVC is protected when its status its&nbsp;metadata.finalizers&nbsp;list includes&nbsp;_____</summary>
kubernetes.io/pvc-protection
<br></details>

<details>
<summary>Generally, a PV will have a specific storage capacity. This is set using the PV's _____&nbsp;attribute.</summary>
capacity&nbsp;
<br></details>

<details>
<summary>You can set the value of&nbsp;volumeMode&nbsp;to&nbsp;_____&nbsp;to use a volume as a raw block device. Such volume is presented into a Pod as a block device, without any filesystem on it. This mode is useful to provide a Pod the fastest possible way to access a volume, without any filesystem layer between the Pod and the volume. On the other hand, the application running in the Pod must know how to handle a raw block device.</summary>
Block
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">ReadOnlyMany&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted read-only by many nodes</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A volume is said to be _____ when the</span>&nbsp;volume has failed its automatic reclamation.</summary>
Failed
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">PersistentVolumes binds are exclusive, and since PersistentVolumeClaims are namespaced objects, mounting claims with "Many" modes (</span><code>ROX</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>RWX</code><span style="color: rgb(34, 34, 34);">) is only possible within _____</span></summary>
<span style="color: rgb(34, 34, 34);">one namespace</span>
<br></details>

<details>
<summary>A _____&nbsp;is a request for snapshot of a volume by a user. It is similar to a PersistentVolumeClaim.</summary>
VolumeSnapshot&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Are&nbsp;</span><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeSnapshotClass</code><span style="color: rgb(34, 34, 34);">&nbsp;part of the core API?&nbsp;</span></summary>
No - they are CustomResourceDefinitions.
<br></details>

<details>
<summary>In volume snapshots, _____&nbsp;are resources in the cluster.&nbsp;_____&nbsp;are requests for those resources.&nbsp;</summary>
VolumeSnapshotContents&nbsp;
VolumeSnapshots&nbsp;<span style="color: rgb(34, 34, 34);">
</span>
<br></details>

<details>
<summary>While a snapshot is being taken of a PersistentVolumeClaim, that PersistentVolumeClaim is in-use. If you delete a PersistentVolumeClaim API object in active use as a snapshot source, the PersistentVolumeClaim object is not removed immediately. Instead, removal of the PersistentVolumeClaim object is postponed until the snapshot is _____</summary>
readyToUse or aborted.
<br></details>

<details>
<summary>_____&nbsp;is the unique identifier of the volume created on the storage backend and returned by the CSI driver during the volume creation. This field is required for dynamically provisioning a snapshot. It specifies the volume source of the snapshot.</summary>
volumeHandle&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You can provision a new volume, pre-populated with data from a snapshot, by using the </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">field in the&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">&nbsp;object.</span></summary>
<em>dataSource</em><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details>

<details>
<summary>PersistentVolumes that are dynamically created by a StorageClass will have a&nbsp;_____defined, which can be&nbsp;Delete&nbsp;or&nbsp;Retain</summary>
reclaimPolicy&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">To enable dynamic volume provisioning, a cluster administrator needs to pre-create one or more _____ objects for users.</span></summary>
<span style="color: rgb(34, 34, 34);">StorageClass</span>
<br></details>

<details>
<summary>When a Container crashes, kubelet will restart it, but its on-disk files will be lost unless stored on a _____</summary>
Volume
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If a PV was dynamically provisioned for a new PVC, the loop will always _____ that PV to the PVC.</span></summary>
binds
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Pod uses a PersistentVolume. This PV has a node affinity towards certain nodes. Where will the Pod be scheduled?</span></summary>
To the node where the PV is available from.
<br></details>

<details>
<summary>A volume is said to be _____ when it is free and not yet bound to a claim.</summary>
Available
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When running Containers together in a&nbsp;</span><code>Pod</code><span style="color: rgb(34, 34, 34);">&nbsp;it is often necessary to share files between those Containers. The Kubernetes&nbsp;_____&nbsp;</span><span style="color: rgb(34, 34, 34);">abstraction solves this problem.</span></summary>
Volume&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Is a volume just a directory with data, accessible to the Containers in its enclosing Pod?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Volumes mount into other volumes?</span></summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A control loop in the master watches for new PVCs, finds a matching PV (if possible), and _____ them.&nbsp;</span></summary>
binds
<br></details>

<details>
<summary>You can only expand a PVC if its storage class's _____&nbsp;field is set to true.&nbsp;To request a larger volume for a PVC, edit the PVC object and specify a larger size. This triggers expansion of the volume that backs the underlying PersistentVolume. A new PersistentVolume is never created to satisfy the claim. Instead, an existing volume is resized.</summary>
allowVolumeExpansion&nbsp;
<br></details>

<details>
<summary>Can you resize an in-use PVC?</summary>
Yes - since Kubernetes 1.15.&nbsp;<span style="color: rgb(136, 136, 136);">The&nbsp;</span><code>ExpandInUsePersistentVolumes</code>&nbsp;feature must be enabled.
<br></details>

<details>
<summary>Kubernetes supports two _____&nbsp;of PersistentVolumes:&nbsp;Filesystem&nbsp;and&nbsp;Block.</summary>
volumeModes&nbsp;
<br></details>

<details>
<summary>volumeMode&nbsp;is an optional API parameter.&nbsp;_____&nbsp;is the default mode used when&nbsp;volumeMode&nbsp;parameter is omitted.</summary>
Filesystem&nbsp;
<br></details>

<details>
<summary>A volume with _____&nbsp;is&nbsp;mounted&nbsp;into Pods into a directory. If the volume is backed by a block device and the device is empty, Kuberneretes creates a filesystem on the device before mounting it for the first time.</summary>
volumeMode: Filesystem
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">ReadWriteMany&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the volume can be mounted as read-write by many nodes</span>
<br></details>

<details>
<summary>A PV can have a class, which is specified by setting the _____&nbsp;attribute to the name of a&nbsp;<a href="https://kubernetes.io/docs/concepts/storage/storage-classes/">StorageClass</a>.&nbsp;</summary>
storageClassName
<br></details>

<details>
<summary>A claim can request a particular class by specifying the name of a StorageClass&nbsp;using the attribute&nbsp;_____.&nbsp;</summary>
storageClassName
<br></details>

<details>
<summary>Similar to how API resources&nbsp;PersistentVolume&nbsp;and&nbsp;PersistentVolumeClaim&nbsp;are used to provision volumes for users and administrators,&nbsp;_____&nbsp;and&nbsp;_____&nbsp;API resources are provided to create volume snapshots for users and administrators.</summary>
VolumeSnapshot&nbsp;
VolumeSnapshotContent&nbsp;
<br></details>

<details>
<summary><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">&nbsp;support is only available for _____ drivers.</span></summary>
<span style="color: rgb(34, 34, 34);">CSI&nbsp;</span>
<br></details>

<details>
<summary>The CRDs and snapshot controller installations are the responsibility of _____</summary>
the Kubernetes distribution
<br></details>

<details>
<summary>The snapshot controller handles the binding of a&nbsp;<code>VolumeSnapshot</code>&nbsp;object with an appropriate&nbsp;<code>VolumeSnapshotContent</code>&nbsp;object, in both pre-provisioned and dynamically provisioned scenarios. The binding is a _____ mapping.&nbsp;
In the case of pre-provisioned binding, the VolumeSnapshot will remain unbound until the requested VolumeSnapshotContent object is created.</summary>
one-to-one
<br></details>

<details>
<summary>An administrator can mark a specific&nbsp;StorageClass&nbsp;as default by adding the&nbsp;_____&nbsp;annotation to it.</summary>
storageclass.kubernetes.io/is-default-class
<br></details>

<details>
<summary>Can you attach as many volumes as you want to a node?</summary>
No - depends on the cloud provider's permitted limit.
<br></details>

<details>
<summary>A PVC to PV binding is a one-to-one mapping, using a <b>_____&nbsp;</b>which is a bi-directional binding between the PersistentVolume and the PersistentVolumeClaim.&nbsp;</summary>
ClaimRef
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A PV of a particular class can only be bound to PVCs requesting that class. A PV with no&nbsp;</span>_____&nbsp;<span style="color: rgb(34, 34, 34);">has no class and can only be bound to PVCs that request no particular class.</span></summary>
storageClassName
<br></details>

<details>
<summary>A volume is called _____ when it is bound to a claim.</summary>
Bound
<br></details>

<details>
<summary>A volume is said to be _____, when the claim has been deleted, but the resource is not yet reclaim by the cluster.</summary>
Released
<br></details>

<details>
<summary>Mounted directories accessible from inside containers are called _____</summary>
Volumes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A Kubernetes volume has an explicit lifetime - the same as _____</span></summary>
The Pod that encloses it
<br></details>

<details>
<summary>Is a Volume preserved across Container restarts?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Managing storage is a distinct problem from managing compute instances. The PersistentVolume subsystem provides an API for users and administrators that abstracts details of how storage is provided from how it is consumed. To do this, we introduce two new API resources: _____ and _____.</span></summary>
<span style="color: rgb(34, 34, 34);">PersistentVolume&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">PersistentVolumeClaim</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Do PersistentVolumes have a lifecycle dependent on the Pods that use the PV?</span></summary>
No
<br></details>

<details>
<summary>The two ways that PVs may be provisioned are either _____ or _____.</summary>
statically or dynamically.
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When none of the static PVs the administrator created match a user's PersistentVolumeClaim, the cluster may try to _____ provision a volume specially for the PVC. This provisioning is based on StorageClasses: the PVC must request a storage class</span><span style="color: rgb(34, 34, 34);">&nbsp;and the administrator must have created and configured that class for dynamic provisioning to occur.</span></summary>
<span style="color: rgb(34, 34, 34);">dynamically</span>
<br></details>

<details>
<summary>Once bound, PersistentVolumeClaim binds are _____, regardless of how they were bound.&nbsp;</summary>
exclusive
<br></details>

<details>
<summary>Once a user has a claim and that claim is bound, the bound PV belongs to the user for as long as they need it. Users schedule Pods and access their claimed PVs by including a _____&nbsp;section in a Pod's&nbsp;_____&nbsp;block.</summary>
persistentVolumeClaim
volumes&nbsp;<code>
</code>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">If an admin deletes a PV that is bound to a PVC, the PV is...</span></summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When a user is done with their volume, they can delete the PVC objects from the API that allows reclamation of the resource. The reclaim policy for a PersistentVolume tells the cluster what to do with the volume after it has been released of its claim. Currently, volumes can either be _____, _____, _____.</span></summary>
<span style="color: rgb(34, 34, 34);">Retained, Recycled, Deleted.</span>
<br></details>

<details>
<summary>The _____&nbsp;reclaim policy allows for manual reclamation of the resource. When the PersistentVolumeClaim is deleted, the PersistentVolume still exists and the volume is considered "released". But it is not yet available for another claim because the previous claimant's data remains on the volume.</summary>
Retain
<br></details>

<details>
<summary>For volume plugins that support the _____&nbsp;reclaim policy, deletion removes both the PersistentVolume object from Kubernetes, as well as the associated storage asset in the external cloud infrastructure. Volumes that were dynamically provisioned inherit the&nbsp;<a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy">reclaim policy of their StorageClass</a>, which defaults to&nbsp;_____. The administrator should configure the StorageClass according to users' expectations; otherwise, the PV must be edited or patched after it is created.</summary>
Delete&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">ReadWriteOnce&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted as read-write by a single node</span>
<br></details>

<details>
<summary>Can a volume be mounted using several access modes at a time?&nbsp;</summary>
No
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A PV can specify _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to define constraints that limit what nodes this volume can be accessed from.&nbsp;</span></summary>
node affinity
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In Kubernetes, a </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">represents a snapshot of a volume on a storage system.</span></summary>
<em>VolumeSnapshot</em>
<br></details>

<details>
<summary>A _____&nbsp;is a snapshot taken from a volume in the cluster that has been provisioned by an administrator. It is a resource in the cluster just like a PersistentVolume is a cluster resource.</summary>
VolumeSnapshotContent&nbsp;
<br></details>

<details>
<summary>_____&nbsp;allows you to specify different attributes belonging to a&nbsp;VolumeSnapshot. These attributes may differ among snapshots taken from the same volume on the storage system and therefore cannot be expressed by using the same&nbsp;StorageClass&nbsp;of a&nbsp;PersistentVolumeClaim.</summary>
VolumeSnapshotClass&nbsp;
<br></details>

<details>
<summary>There are two ways snapshots may be provisioned: _____ or _____.</summary>
pre-provisioned or dynamically provisioned.
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">A cluster administrator creates a number of&nbsp;</span><code>VolumeSnapshotContents</code><span style="color: rgb(34, 34, 34);">. They carry the details of the real volume snapshot on the storage system which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption. This is the description of _____ snapshot provisioning.</span></summary>
pre-provisioned
<br></details>

<details>
<summary>Instead of using a pre-existing snapshot, you can request that a snapshot to be _____ taken from a PersistentVolumeClaim. The&nbsp;<a href="https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/">VolumeSnapshotClass</a>&nbsp;specifies storage provider-specific parameters to use when taking a snapshot.</summary>
dynamically
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Users request dynamically provisioned storage by including a _____ in their&nbsp;</span><code>PersistentVolumeClaim</code></summary>
<span style="color: rgb(34, 34, 34);">.spec.storageClassName</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Claims will remain _____ indefinitely if a matching volume does not exist, and will be bound as matching volumes become available.&nbsp;</span></summary>
unbound
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Only PVs of the requested class, ones with the same&nbsp;</span>_____&nbsp;<span style="color: rgb(34, 34, 34);">as the PVC, can be bound to the PVC.</span></summary>
StorageClassName
<br></details>

<details>
<summary>Are volumes namespaced?</summary>
No
<br></details>


## etcd 
<details>
<summary>Can attackers manipulate cluster data in etcd, bypassing the api server completely?</summary>
Yes
<br></details>

<details>
<summary>etcd should have authentication, be firewalled and be _____ at rest.</summary>
encrypted
<br></details>

<details>
<summary>Should you be able to freely send network traffic to etcd from the cluster?</summary>
No
<br></details>

<details>
<summary>Can attackers remove network policies from within etcd?</summary>
Yes
<br></details>

<details>
<summary>Should you run etcd on dedicated nodes?</summary>
Yes
<br></details>

<details>
<summary>Restricting access to _____ prevents an attacker from modifying the desired cluster state.</summary>
etcd
<br></details>
