<details>
<summary>Kubernetes _____ provides a security-relevant chronological set of records documenting the sequence of activities that have affected system by individual users, administrators or other components of the system.</summary>
auditing
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit records begin their lifecycle inside the _____ Kubernetes</span><span style="color: rgb(34, 34, 34);">&nbsp;component.</span></summary>
<a href="https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/">kube-apiserver</a>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Each request on each stage of its execution generates an audit _____, which is then pre-processed according to a certain policy and written to a backend.</span></summary>
<span style="color: rgb(34, 34, 34);">event</span>
<br></details>

<details>
<summary>Audit logging usually _____ the memory consumption of the API server because some context required for auditing is stored for each request.</summary>
increases&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit _____ objects define rules about what events should be recorded and what data they should include.</span></summary>
<span style="color: rgb(34, 34, 34);">policy</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">When an event is processed, it's compared against the list of Audit Policy rules in order. The first matching rule sets the "_____" of the event.</span></summary>
<span style="color: rgb(34, 34, 34);">audit level</span>
<br></details>

<details>
<summary>The four audit levels are:
_____&nbsp;- don't log these events._____&nbsp;- log request metadata (requesting user, timestamp, resource, verb, etc.)&nbsp;_____&nbsp;- log event metadata and request body._____&nbsp;- log event metadata, request body and response bodies.</summary>
None
Metadata
Request
RequestResponse
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">Audit _____ persist audit events to an external storage.</span></summary>
<span style="color: rgb(34, 34, 34);">backends</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ audit backend writes event to a disk</span></summary>
log
<br></details>

<details>
<summary>Can you use log collectors like fluentd to collect/distribute Kubernetes audit events from log files?</summary>
Yes
<br></details>

<details>
<summary>Can you use log collectors like logstash to collect/distribute Kubernetes audit events from the webhook audit backend?</summary>
Yes
<br></details>

<details>
<summary>Kubernetes _____ allows cluster administrators to learn about the context of clusters events: What happened, when, where, who initiated it and from where.</summary>
auditing
<br></details>

<details>
<summary>The audit _____ determines what events are recorded and which backends (logs or webhooks) persist the records.</summary>
policy&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">The _____ audit backend sends events to an external API.</span></summary>
webhook
<br></details>

<details>
<summary>_____ failures might suggest a misconfigured service account, or the presence of an attacker.</summary>
RBAC audit
<br></details>

<details>
<summary>What are some tools with which clusters can be audited?</summary>
Sonobuoy
<br></details>