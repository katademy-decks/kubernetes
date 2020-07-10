# Control_Plane 

<details>
<summary>
<b>Control plane components</b>
</summary>
<div>Kubernetes Master&nbsp;
</div><div>kubelets<div><div>etcd</div></div></div>
</details>

<details>
<summary>
<b>All API usage from nodes and pods terminate at the following control plane components:</b>
</summary>
<b>apiserver</b><div><div><hr><div>no other control plane components exposes remote services</div></div></div>
</details>

<details>
<summary>
<b>Nodes should be provisioned with _____ for the cluster such that they can connect securely to the apiserver along with valid client credentials</b>
</summary>
public root certificate
</details>

<details>
<summary>
<b>Pods that wish to securely connect to the apiserver can leverage a _____ so that K8S will automatically inject the public root certificate and valid bearer token into the new pod.</b>
</summary>
service account
</details>

<details>
<summary>
<b>The <b>kubernetes </b>service (in all namespaces) is configured with _____ that is redirected via _____ to the apiserver</b>
</summary>
a virtual IP address<div>
</div><div>kube-proxy</div>
</details>

<details>
<summary>
<b>the apiserver is configured to listen for remote connections on _____ with one or more forms of _____ enabled</b>
</summary>
a secure HTTPS port<div>
</div><div>client authentication</div>
</details>

<details>
<summary>
<b><div>apiserver to kubelet connections are used for</div></b>
</summary>
Fetching pod logs<div>
</div><div><b>kubectl attach</b>'ing into pods</div><div>
</div><div><b>kubectl port-forward</b>'ing into pods</div>
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
No<div>-----</div><div>The connection is subject to MITM attacks by default</div>
</details>

<details>
<summary>
<b>apiserver to kubelet connection can be verified via</b>
</summary>
<div>SSH tunneling</div><div>
</div><div>OR&nbsp;</div><div>
</div><b>apiserver --kubelet-certificate-authority</b>
</details>

<details>
<summary>
<b>Are <b>apiserver</b>&nbsp;connections to <b>nodes, pods and services</b>&nbsp;authenticated or encrypted?</b>
</summary>
No :(<div>
</div><div>They can be run over HTTPS but will not validate the certificate</div>
</details>

<details>
<summary>
<b>By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.</b>
</summary>
cloud-controller-manager
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
<b>Create / destroy nodes&nbsp;</b><div>when new servers are created and destroyed in your cloud infrastructure</div><div>
</div><div><b>Annotate Nodes</b></div><div>with cloud-specific information, such as Region</div><div>
</div><div><b>Get Node information</b></div><div>Hostname, address, health</div>
</details>

<details>
<summary>
<b>Route controller</b>
</summary>
Configures addresses and routes between K8S nodes in your cloud
</details>

<details>
<summary>
<b>Service Controller</b>
</summary>
Sets up Load Balancers and other infrastructure components needed by <b>Service </b>k8s objects
</details>

<details>
<summary>
<b>cloud-controller-manager runs the following controllers:</b>
</summary>
<div>Node Controller
</div><div>Route Controller</div><div>Volume Controller</div><div>Service Controller</div>
</details>

<details>
<summary>
<b>kube-controller-manager</b>
</summary>
Daemon controlling core K8S control loops<div>
</div><div>Node controller</div><div>Replication controller</div><div>Service account controller</div><div>Endpoints controller
<div>Garbage collector (can be disabled)
</div><div>
</div><div>HPA
</div><div>Leader election</div><div><div>Reconcilliation interval</div></div><div><div>Feature gates</div></div><div><div>Cluster CIDR</div><div>Pod CIDR</div></div></div>
</details>

<details>
<summary>
<b>List processes running on every Kubernetes Master</b>
</summary>
1. kube-apiserver
2. kube-controller-manager
3. kube-scheduler

<img src="paste-d842301571ce981466b41d198776a3b6b0df20e8.jpg">
</details>

<details>
<summary>
<b>Kubernetes Master</b>
</summary>
<div><div>kube-controller-manager
kube-apiserver<div>kube-scheduler</div></div><div>
</div>Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

