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