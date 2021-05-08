<details>
<summary><span style="color: rgb(34, 34, 34);">Admission Control Modules are software modules that can _____ or _____ requests.</span></summary>
<span style="color: rgb(34, 34, 34);">modify</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">reject</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Admission Control Modules can access the contents of the Kubernetes object that is being _____ or _____.</span></summary>
<span style="color: rgb(34, 34, 34);">created&nbsp;</span>
<span style="color: rgb(34, 34, 34);">
</span>modified
<br></details>

<details>
<summary>Can Admission controllers act on requests that create an object?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that delete an object?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that connect (proxy) to an object?</span></summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Can Admission controllers act on requests that read an object?</span></summary>
No
<br></details>

<details>
<summary>An admission controller module rejects a request. What happens to the request?</summary>
It is immediately rejected.
<br></details>

<details>
<summary>Can admission controllers set complex defaults for fields?</summary>
Yes
<br></details>

<details>
<summary>Does the admission or validation of a request happen first?</summary>
admission
<br></details>

<details>
<summary>Can resource quotas improve security by preventing internal denial of service attacks?</summary>
Yes
<br></details>

<details>
<summary>Open Policy Agent can manage your _____ controllers in order to block K8S features (like being able to run containers as root) from multiple teams.</summary>
admission&nbsp;
<br></details>

<details>
<summary>Is admission control's NodeRestriction enabled by default?</summary>
No!
<br></details>