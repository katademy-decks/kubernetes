# ConfigMaps 

<details>
<summary>
<b>ConfigMaps</b>
</summary>
The ConfigMap is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod’s environment.
</details>

<details>
<summary>
<b>How to Pass an environment variable to entrypoint? Where env varaible derived from configMaps</b>
</summary>
spec:
 &nbsp;containers:
 &nbsp;&nbsp;&nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello-config-args
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;args:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- "-greeting"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- "$(GREETING)"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- containerPort: 8888
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;env:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name: GREETING
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valueFrom:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configMapKeyRef:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: demo-config
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key: greeting
</details>

<details>
<summary>
<b>Updating Pods on a Config Change</b>
</summary>
<strong>checksum/config: {{ include (print $.Template.BasePath "/configmap.yaml") . | sha256sum }}</strong>
<strong>
</strong>Deployment template now includes a hash sum of the config settings, if these settings change, then so will the hash.&nbsp;When we run&nbsp;pod-name upgrade, POD will detect that the Deployment spec has changed, and restart all the Pods.<strong>
</strong>
</details>

