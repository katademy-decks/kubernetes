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