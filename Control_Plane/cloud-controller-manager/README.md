# cloud-controller-manager 

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

