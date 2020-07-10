# Presets 

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A PodPreset allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></b>
</summary>
creation time
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></b>
</summary>
label selectors
</details>

<details>
<summary>
<b>What applies Pod Presets to incoming pod creation requests?</b>
</summary>
PodPreset admission controller
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></b>
</summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies the _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
</details>

<details>
<summary>
<b>How to&nbsp;disable Pod Preset for a Specific Pod</b>
</summary>
<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">podpreset.admission.kubernetes.io/exclude: "true"</span><div><span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span></div><div>Add the above annotation in the Pod Spec<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span></div>
</details>

