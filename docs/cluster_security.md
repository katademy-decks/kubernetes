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