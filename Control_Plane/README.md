# Control_Plane 

<details>
<summary>
<b>Pods that wish to securely connect to the apiserver can automatically inject the public root certificate and valid bearer token into themselves. This is done by using a...</b>
</summary>
service account
</details>

<details>
<summary>
<b>apiserver to kubelet connection can be verified by adding the apiserver flag _____ or via _____</b>
</summary>
<b>--kubelet-certificate-authority</b>
<b>
</b>SSH tunneling
</details>

<details>
<summary>
<b>By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.</b>
</summary>
cloud-controller-manager
</details>

<details>
<summary>
<b>the apiserver is configured to listen for remote connections on a secure _____ port with one or more forms of client _____ enabled</b>
</summary>
HTTPS
authentication
</details>

<details>
<summary>
<b>Are <b>apiserver</b>&nbsp;connections to <b>nodes, pods and services</b>&nbsp;authenticated or encrypted?</b>
</summary>
They can run over HTTPS but will NOT validate the certificate :(
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The _____ is a daemon that embeds the core control loops shipped with Kubernetes.&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">kube-controller-manager</span>
</details>

<details>
<summary>
<b>The Kubernetes Master is a collection of three processes that run on a single node in your cluster. These processes are...</b>
</summary>
apiserver, scheduler, controller-manager
</details>

<details>
<summary>
<b>Nodes should be provisioned with _____ for the cluster such that they can connect securely to the apiserver along with valid client credentials</b>
</summary>
public root certificate
</details>

<details>
<summary>
<b>The <b>kubernetes </b>service is configured in all namespaces&nbsp;with virtual IP address that is redirected via _____ to the apiserver.</b>
</summary>
kube-proxy
</details>

<details>
<summary>
<b>apiserver to kubelet connections terminate at</b>
</summary>
the kubelet's HTTPS endpoint
</details>

<details>
<summary>
<b>Does the <b>apiserver</b> verify the <b>kubelet's</b> serving certificate by default?</b>
</summary>
No. The connection is subject to MITM attacks by default.
</details>

<details>
<summary>
<b>The component that creates, annotates, destroys nodes and gets their information (like hostname, address or health) is called the...</b>
</summary>
Node controller
</details>

<details>
<summary>
<b>The three main control plane components are...</b>
</summary>
kubelets, master, etcd
</details>

<details>
<summary>
<b>All API usage from nodes and pods terminate at the following control plane components:</b>
</summary>
apiserver only.
</details>

