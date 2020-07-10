# Control_Plane 

<details>
<summary>
Control plane components
</summary>
<div>Kubernetes Master&nbsp;
</div><div>kubelets<div><div>etcd</div></div></div>
</details>

<details>
<summary>
All API usage from nodes and pods terminate at the following control plane components:
</summary>
*apiserver*<div><div><hr><div>no other control plane components exposes remote services</div></div></div>
</details>

<details>
<summary>
Nodes should be provisioned with _____ for the cluster such that they can connect securely to the apiserver along with valid client credentials
</summary>
public root certificate
</details>

<details>
<summary>
Pods that wish to securely connect to the apiserver can leverage a _____ so that K8S will automatically inject the public root certificate and valid bearer token into the new pod.
</summary>
service account
</details>

<details>
<summary>
The *kubernetes *service (in all namespaces) is configured with _____ that is redirected via _____ to the apiserver
</summary>
a virtual IP address<div>
</div><div>kube-proxy</div>
</details>

<details>
<summary>
the apiserver is configured to listen for remote connections on _____ with one or more forms of _____ enabled
</summary>
a secure HTTPS port<div>
</div><div>client authentication</div>
</details>

<details>
<summary>
<div>apiserver to kubelet connections are used for</div>
</summary>
Fetching pod logs<div>
</div><div>*kubectl attach*'ing into pods</div><div>
</div><div>*kubectl port-forward*'ing into pods</div>
</details>

<details>
<summary>
apiserver to kubelet connections terminate at
</summary>
the kubelet's HTTPS endpoint
</details>

<details>
<summary>
Does the *apiserver* verify the *kubelet's* serving certificate by default?
</summary>
No<div>-----</div><div>The connection is subject to MITM attacks by default</div>
</details>

<details>
<summary>
apiserver to kubelet connection can be verified via
</summary>
<div>SSH tunneling</div><div>
</div><div>OR&nbsp;</div><div>
</div>*apiserver --kubelet-certificate-authority*
</details>

<details>
<summary>
Are *apiserver*&nbsp;connections to *nodes, pods and services*&nbsp;authenticated or encrypted?
</summary>
No :(<div>
</div><div>They can be run over HTTPS but will not validate the certificate</div>
</details>

<details>
<summary>
By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.
</summary>
cloud-controller-manager
</details>

<details>
<summary>
Node controller
</summary>
*Create / destroy nodes&nbsp;*<div>when new servers are created and destroyed in your cloud infrastructure</div><div>
</div><div>*Annotate Nodes*</div><div>with cloud-specific information, such as Region</div><div>
</div><div>*Get Node information*</div><div>Hostname, address, health</div>
</details>

<details>
<summary>
Route controller
</summary>
Configures addresses and routes between K8S nodes in your cloud
</details>

<details>
<summary>
Service Controller
</summary>
Sets up Load Balancers and other infrastructure components needed by *Service *k8s objects
</details>

<details>
<summary>
cloud-controller-manager runs the following controllers:
</summary>
<div>Node Controller
</div><div>Route Controller</div><div>Volume Controller</div><div>Service Controller</div>
</details>

<details>
<summary>
kube-controller-manager
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
List processes running on every Kubernetes Master
</summary>
1. kube-apiserver
2. kube-controller-manager
3. kube-scheduler

<img src="paste-d842301571ce981466b41d198776a3b6b0df20e8.jpg">
</details>

<details>
<summary>
Kubernetes Master
</summary>
<div><div>kube-controller-manager
kube-apiserver<div>kube-scheduler</div></div><div>
</div>Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

