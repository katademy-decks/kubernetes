# cloud-controller-manager 

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
<b>Create / destroy nodes&nbsp;</b>when new servers are created and destroyed in your cloud infrastructure
<b>Annotate Nodes</b>with cloud-specific information, such as Region
<b>Get Node information</b>Hostname, address, health
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
Node Controller
Route ControllerVolume ControllerService Controller
</details>

