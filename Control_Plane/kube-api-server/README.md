# kube-api-server 

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

