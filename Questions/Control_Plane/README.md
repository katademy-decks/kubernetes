# Control_Plane 

<details>
<summary>Pods that wish to securely connect to the apiserver can automatically inject the public root certificate and valid bearer token into themselves. This is done by using a...</summary>
service account
<br></details><details>
<summary>apiserver to kubelet connection can be verified by adding the apiserver flag _____ or via _____</summary>
<b>--kubelet-certificate-authority</b>
<b>
</b>SSH tunneling
<br></details><details>
<summary>By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.</summary>
cloud-controller-manager
<br></details><details>
<summary>the apiserver is configured to listen for remote connections on a secure _____ port with one or more forms of client _____ enabled</summary>
HTTPS
authentication
<br></details><details>
<summary>Are <b>apiserver</b>&nbsp;connections to <b>nodes, pods and services</b>&nbsp;authenticated or encrypted?</summary>
They can run over HTTPS but will NOT validate the certificate :(
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The _____ is a daemon that embeds the core control loops shipped with Kubernetes.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">kube-controller-manager</span>
<br></details><details>
<summary>The Kubernetes Master is a collection of three processes that run on a single node in your cluster. These processes are...</summary>
apiserver, scheduler, controller-manager
<br></details><details>
<summary>Nodes should be provisioned with _____ for the cluster such that they can connect securely to the apiserver along with valid client credentials</summary>
public root certificate
<br></details><details>
<summary>The <b>kubernetes </b>service is configured in all namespaces&nbsp;with virtual IP address that is redirected via _____ to the apiserver.</summary>
kube-proxy
<br></details><details>
<summary>apiserver to kubelet connections terminate at</summary>
the kubelet's HTTPS endpoint
<br></details><details>
<summary>Does the <b>apiserver</b> verify the <b>kubelet's</b> serving certificate by default?</summary>
No. The connection is subject to MITM attacks by default.
<br></details><details>
<summary>The component that creates, annotates, destroys nodes and gets their information (like hostname, address or health) is called the...</summary>
Node controller
<br></details><details>
<summary>The three main control plane components are...</summary>
kubelets, master, etcd
<br></details><details>
<summary>All API usage from nodes and pods terminate at the following control plane components:</summary>
apiserver only.
<br></details>