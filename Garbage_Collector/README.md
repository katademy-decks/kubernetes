# Garbage_Collector 

<details>
<summary>
<b>The role of the Kubernetes garbage collector is to delete certain objects that once had _____, but no longer have one.</b>
</summary>
an owner
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Owned objects are called&nbsp;</span><em>dependents</em><span style="color: rgb(34, 34, 34);">&nbsp;of the owner object. Every dependent object has a&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;field that points to the owning object. The field is&nbsp;</span><span style="color: rgb(34, 34, 34);">automatically set </span><span style="color: rgb(34, 34, 34);">for objects created or adopted by ReplicationController, ReplicaSet, StatefulSet, DaemonSet, Deployment, Job and CronJob.</span></b>
</summary>
metadata.ownerReferences
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Can you specify relationships between owners and dependents manually?</span></b>
</summary>
Yes - by&nbsp;setting the&nbsp;ownerReference&nbsp;field.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When you delete an object, you can specify whether the object's dependents are also deleted automatically. Deleting dependents automatically is called <i>_____</i></span></b>
</summary>
cascading deletion
</details>

<details>
<summary>
<b>If you delete an object without deleting its dependents automatically, the dependents are said to be <i>_____</i></b>
</summary>
orphaned
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In _____</span><span style="color: rgb(34, 34, 34);">, Kubernetes deletes the owner object immediately and the garbage collector then deletes the dependents in the background.</span></b>
</summary>
background cascading deletion
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In </span><i>_____</i><span style="color: rgb(34, 34, 34);">, the root object first enters a "deletion in progress" state.&nbsp;</span>Once the "deletion in progress" state is set, the garbage collector deletes the object's dependents. Once the garbage collector has deleted all dependents,&nbsp;it deletes the owner object.</b>
</summary>
foreground cascading deletion
</details>

<details>
<summary>
<b>To control the cascading deletion policy, set the&nbsp;<code>propagationPolicy</code>&nbsp;field on the&nbsp;<code>deleteOptions</code>&nbsp;argument when deleting an Object. Possible values include "Orphan", "Foreground", or "Background".</b>
</summary>
TODO
</details>

