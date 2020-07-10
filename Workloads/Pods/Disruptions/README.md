# Disruptions 

<details>
<summary>
Does deleting deployments or pods bypass Pod Disruption Budgets?

</summary>
Yes
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Ex.:</span></div><div><span style="color: rgb(34, 34, 34);">A quorum-based application would like to ensure that the number of replicas running is never brought below the number needed for a quorum.&nbsp;</span></div><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total.</span><span style="color: rgb(34, 34, 34);">
</span></div>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Cluster managers and hosting providers should use tools which respect Pod Disruption Budgets by calling _____&nbsp;</span><span style="color: rgb(34, 34, 34);">instead of directly deleting pods or deployments</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">An example is the _____ command.</span></div>
</summary>
the Eviction API<div>
</div><div>kubectl drain</div>
</details>

<details>
<summary>
A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span>
</summary>
replicas
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">ADeployment has a&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">It is supposed to have 5 pods at any given time.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">If its PDB allows for there to be 4 at a time, then the Eviction API will allow voluntary disruption of how many pods at a time?</span></div>
</summary>
<span style="color: rgb(34, 34, 34);">One</span>
</details>

<details>
<summary>
PodDisruptionBudgets cannot prevent involuntary disruptions from occurring.&nbsp;<div>
</div><div>Do involuntary disruptions count against the budget?</div>
</summary>
No
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span>
</summary>
Yes
</details>

<details>
<summary>
Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?
</summary>
*No*<div>
</div><div><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec. (Learn about&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment">updating a deployment</a><span style="color: rgb(34, 34, 34);">.)</span></div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span>
</summary>
Yes
</details>

