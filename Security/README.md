# Security 

<details>
<summary>
<b>How to harden the security of the container?</b>
</summary>
containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
<b> &nbsp;securityContext:
</b><strong>&nbsp; &nbsp;<font color="#ab1aff">readOnlyRootFilesystem: true</font></strong><b><font color="#ab1aff">
</font></b><strong>&nbsp; &nbsp;<i><font color="#ff5d83">runAsNonRoot: true</font></i></strong><b>
 &nbsp;&nbsp;&nbsp;runAsUser: 1000</b>
&nbsp; &nbsp;# setuid&nbsp;mechanism can temporarily gain the privileges of the user that&nbsp;<em>owns</em>&nbsp;the binary<b>
</b>&nbsp; &nbsp;allowPrivilegeEscalation: false
&nbsp; &nbsp;capabilities:&nbsp;&nbsp; &nbsp; &nbsp;drop: ["all"]&nbsp;&nbsp; &nbsp; &nbsp;drop: ["CHOWN", "NET_RAW", "SETPCAP"]&nbsp;&nbsp; &nbsp; &nbsp;add: ["NET_ADMIN"]<strong>
</strong>
</details>

<details>
<summary>
<b>Role</b>
</summary>
A role contains a set of permissions
Permissions are additivite (no "deny" rules)
Role (namespace)ClusterRole (cluster)
rules:&nbsp; &nbsp; - apiGroups: [""] # "" = core API group&nbsp; &nbsp; &nbsp; resources: ["pods"]&nbsp; &nbsp; &nbsp; verbs: ["get", "watch", "list"]
</details>

