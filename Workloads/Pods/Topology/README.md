# Topology 

<details>
<summary>
<span style="color: rgb(34, 34, 34);">You can use&nbsp;</span><em>topology spread constraints</em><span style="color: rgb(34, 34, 34);">&nbsp;to control...</span>
</summary>
<span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains)</span></div>
</details>

<details>
<summary>
<div><div>You have a 4-node cluster with the following labels:</div><pre><code>NAME    STATUS   ROLES    AGE     VERSION   LABELS
node1   Ready    &lt;none&gt;   4m26s   v1.16.0   node=node1,zone=zoneA
node2   Ready    &lt;none&gt;   3m58s   v1.16.0   node=node2,zone=zoneA
node3   Ready    &lt;none&gt;   3m17s   v1.16.0   node=node3,zone=zoneB
node4   Ready    &lt;none&gt;   2m43s   v1.16.0   node=node4,zone=zoneB</code></pre></div><div>What would the cluster logically look like?</div>
</summary>
<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+</code></pre>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span>
</summary>
node labels
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">You can define one or multiple _____&nbsp;</span>to instruct the kube-scheduler how to place each incoming Pod in relation to the existing Pods across your cluster.
</summary>
<code>topologySpreadConstraint</code>
</details>

<details>
<summary>
*topologySpreadConstraints *syntax
</summary>
<pre><code>apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  topologySpreadConstraints:
    - maxSkew: &lt;integer&gt;
      topologyKey: &lt;string&gt;
      whenUnsatisfiable: &lt;string&gt;
      labelSelector: &lt;object&gt;</code></pre>
</details>

<details>
<summary>
<strong>maxSkew</strong><span style="color: rgb(34, 34, 34);">&nbsp;describes...</span>
</summary>
the degree to which Pods may be unevenly distributed.<div>
</div><div><span style="color: rgb(34, 34, 34);">It's the maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type.</span>
</div><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">It must be greater than zero.</span><span style="color: rgb(34, 34, 34);">
</span></div>
</details>

<details>
<summary>
<strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span>
</summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
</details>

<details>
<summary>
<div><div><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one *topologyKey *and have identical values for that label, the scheduler treats both Nodes as _____</span></div></div><div>
</div><div>
</div>
</summary>
<span style="color: rgb(34, 34, 34);">Being in the same topology.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">The scheduler tries to place a balanced number of Pods into each topology domain</span><span style="color: rgb(34, 34, 34);">
</span></div>
</details>

<details>
<summary>
<strong>whenUnsatisfiable</strong><span style="color: rgb(34, 34, 34);">&nbsp;indicates...</span>
</summary>
<span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the spread constraint</span>
</details>

<details>
<summary>
*whenUnsatisfiable *possible values:
</summary>
<div>*<code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span>*</div><div><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">
</span></div><div>*<code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>*<span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span></div>
</details>

<details>
<summary>
<div><h3>Example: One TopologySpreadConstraint</h3></div><div>Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):</div><pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre><div>If we want an incoming Pod to be evenly spread with existing Pods across zones, the spec can be given as:</div>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>mypod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologySpreadConstraints</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">maxSkew</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologyKey</span>:<span style="color: rgb(187, 187, 187);"> </span>zone<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">whenUnsatisfiable</span>:<span style="color: rgb(187, 187, 187);"> </span>DoNotSchedule<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labelSelector</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">matchLabels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>pause<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/pause:<span style="color: rgb(102, 102, 102);">3.1</span></code></pre><pre><code><div><code>topologyKey: zone</code>&nbsp;implies the even distribution will only be applied to the nodes which have label pair "zone:&lt;any value&gt;" present.&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;tells the scheduler to let it stay pending if the incoming Pod can’t satisfy the constraint.</div><div>If the scheduler placed this incoming Pod into "zoneA", the Pods distribution would become [3, 1], hence the actual skew is 2 (3 - 1) - which violates&nbsp;<code>maxSkew: 1</code>. In this example, the incoming Pod can only be placed onto "zoneB":</div><pre><code>+---------------+---------------+      +---------------+---------------+
|     zoneA     |     zoneB     |      |     zoneA     |     zoneB     |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |  OR  | node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
|   P   |   P   |   P   |   P   |      |   P   |   P   |  P P  |       |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
</code></pre><div>You can tweak the Pod spec to meet various kinds of requirements:</div><ul><li>Change&nbsp;<code>maxSkew</code>&nbsp;to a bigger value like "2" so that the incoming Pod can be placed onto "zoneA" as well.</li><li>Change&nbsp;<code>topologyKey</code>&nbsp;to "node" so as to distribute the Pods evenly across nodes instead of zones. In the above example, if&nbsp;<code>maxSkew</code>&nbsp;remains "1", the incoming Pod can only be placed onto "node4".</li><li>Change&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;to&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code>&nbsp;to ensure the incoming Pod to be always schedulable (suppose other scheduling APIs are satisfied). However, it’s preferred to be placed onto the topology domain which has fewer matching Pods. (Be aware that this preferability is jointly normalized with other internal scheduling priorities like resource usage ratio, etc.)<code>topologyKey: zone</code><span style="font-family: Arial;">&nbsp;</span><span style="font-family: Arial;">implies the even distribution will only be applied to the nodes which have label pair "zone:&lt;any value&gt;" present.</span><span style="font-family: Arial;">&nbsp;</span><code>whenUnsatisfiable: DoNotSchedule</code><span style="font-family: Arial;">&nbsp;</span><span style="font-family: Arial;">tells the scheduler to let it stay pending if the incoming Pod can’t satisfy the constraint.</span><div>If the scheduler placed this incoming Pod into "zoneA", the Pods distribution would become [3, 1], hence the actual skew is 2 (3 - 1) - which violates&nbsp;<code>maxSkew: 1</code>. In this example, the incoming Pod can only be placed onto "zoneB":</div><pre><code>+---------------+---------------+      +---------------+---------------+
|     zoneA     |     zoneB     |      |     zoneA     |     zoneB     |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |  OR  | node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
|   P   |   P   |   P   |   P   |      |   P   |   P   |  P P  |       |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
</code></pre><div>You can tweak the Pod spec to meet various kinds of requirements:</div><ul><li>Change&nbsp;<code>maxSkew</code>&nbsp;to a bigger value like "2" so that the incoming Pod can be placed onto "zoneA" as well.</li><li>Change&nbsp;<code>topologyKey</code>&nbsp;to "node" so as to distribute the Pods evenly across nodes instead of zones. In the above example, if&nbsp;<code>maxSkew</code>&nbsp;remains "1", the incoming Pod can only be placed onto "node4".</li><li>Change&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;to&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code>&nbsp;to ensure the incoming Pod to be always schedulable (suppose other scheduling APIs are satisfied). However, it’s preferred to be placed onto the topology domain which has fewer matching Pods. (Be aware that this preferability is jointly normalized with other internal scheduling priorities like resource usage ratio, etc.)</li></ul></li></ul></code></pre><pre><code><span style="color: rgb(102, 102, 102);">
</span></code></pre>
</details>

<details>
<summary>
<h3>Example: Multiple TopologySpreadConstraints<a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/#example-multiple-topologyspreadconstraints"></a></h3><div>&nbsp;Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):</div><pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre><div>You can use 2 TopologySpreadConstraints to control the Pods spreading on both zone and node:</div>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>mypod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologySpreadConstraints</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">maxSkew</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologyKey</span>:<span style="color: rgb(187, 187, 187);"> </span>zone<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">whenUnsatisfiable</span>:<span style="color: rgb(187, 187, 187);"> </span>DoNotSchedule<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labelSelector</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">matchLabels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">maxSkew</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologyKey</span>:<span style="color: rgb(187, 187, 187);"> </span>node<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">whenUnsatisfiable</span>:<span style="color: rgb(187, 187, 187);"> </span>DoNotSchedule<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labelSelector</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">matchLabels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>pause<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/pause:<span style="color: rgb(102, 102, 102);">3.1</span></code></pre><pre><code><div>In this case, to match the first constraint, the incoming Pod can only be placed onto "zoneB"; while in terms of the second constraint, the incoming Pod can only be placed onto "node4". Then the results of 2 constraints are ANDed, so the only viable option is to place on "node4".</div><div>Multiple constraints can lead to conflicts. Suppose you have a 3-node cluster across 2 zones:</div><pre><code>+---------------+-------+
|     zoneA     | zoneB |
+-------+-------+-------+
| node1 | node2 | node3 |
+-------+-------+-------+
|  P P  |   P   |  P P  |
+-------+-------+-------+
</code></pre><div>If you apply "two-constraints.yaml" to this cluster, you will notice "mypod" stays in&nbsp;<code>Pending</code>&nbsp;state. This is because: to satisfy the first constraint, "mypod" can only be put to "zoneB"; while in terms of the second constraint, "mypod" can only put to "node2". Then a joint result of "zoneB" and "node2" returns nothing.</div><div>To overcome this situation, you can either increase the&nbsp;<code>maxSkew</code>&nbsp;or modify one of the constraints to use&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code></div></code></pre><pre><code><span style="color: rgb(102, 102, 102);">
</span></code></pre>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Only the Pods holding the same _____ as the incoming Pod can be matching candidates</span>
</summary>
namespace
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Nodes without&nbsp;</span><code>topologySpreadConstraints[*].topologyKey</code><span style="color: rgb(34, 34, 34);">&nbsp;present will be...</span>
</summary>
*bypassed*<div>*
*</div><div>This implies that:
<div><ol><li>the Pods located on those nodes do not impact&nbsp;<code>maxSkew</code>&nbsp;calculation - in the above example, suppose "node1" does not have label "zone", then the 2 Pods will be disregarded, hence the incomingPod will be scheduled into "zoneA".</li><li>the incoming Pod has no chances to be scheduled onto this kind of nodes - in the above example, suppose a "node5" carrying label&nbsp;<code>{zone-typo: zoneC}</code>&nbsp;joins the cluster, it will be bypassed due to the absence of label key "zone".</li></ol></div></div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">If the incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span>
</summary>
bypassed
</details>

<details>
<summary>
<div>Suppose you have a 5-node cluster ranging from zoneA to zoneC:</div><pre><code>+---------------+---------------+-------+
|     zoneA     |     zoneB     | zoneC |
+-------+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 | node5 |
+-------+-------+-------+-------+-------+
|   P   |   P   |   P   |       |       |
+-------+-------+-------+-------+-------+
</code></pre><div>and you know that "zoneC" must be excluded. In this case, you can compose the yaml as below, so that "mypod" will be placed onto "zoneB" instead of "zoneC". Similarly&nbsp;<code>spec.nodeSelector</code>&nbsp;is also respected.</div>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>mypod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologySpreadConstraints</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">maxSkew</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologyKey</span>:<span style="color: rgb(187, 187, 187);"> </span>zone<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">whenUnsatisfiable</span>:<span style="color: rgb(187, 187, 187);"> </span>DoNotSchedule<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labelSelector</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">matchLabels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">foo</span>:<span style="color: rgb(187, 187, 187);"> </span>bar<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">affinity</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">nodeAffinity</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">requiredDuringSchedulingIgnoredDuringExecution</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">nodeSelectorTerms</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">matchExpressions</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">key</span>:<span style="color: rgb(187, 187, 187);"> </span>zone<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span><span style="color: rgb(170, 34, 255); font-weight: 700;">operator</span>:<span style="color: rgb(187, 187, 187);"> </span>NotIn<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span><span style="color: rgb(170, 34, 255); font-weight: 700;">values</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span>- zoneC<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>pause<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/pause:<span style="color: rgb(102, 102, 102);">3.1</span></code></pre>
</details>

<details>
<summary>
<h2>Comparison of Topology with PodAffinity/PodAntiAffinity</h2><div><div>In Kubernetes, directives related to "Affinity" control how Pods are scheduled - more packed or more scattered.</div></div><div>
</div><div><ul><li>For <font face="monospace">_____</font>, you can try to pack any number of Pods into qualifying topology domain(s)</li><li>For&nbsp;<font face="monospace">_____</font>, only one Pod can be scheduled into a single topology domain.</li></ul></div>
</summary>
PodAffinity<div>
</div><div>PodAntiAffinity
</div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">It is possible to set default topology spread constraints for a cluster.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Default topology spread constraints are applied to a Pod if, and only if:</span></div>
</summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
</details>

<details>
<summary>
<div>An example *KubeSchedulerConfiguration *configuration for cluster-level default constraints might look like...</div>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>kubescheduler.config.k8s.io/v1alpha2<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>KubeSchedulerConfiguration<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">profiles</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">pluginConfig</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>PodTopologySpread<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">args</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">defaultConstraints</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">maxSkew</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span><span style="color: rgb(170, 34, 255); font-weight: 700;">topologyKey</span>:<span style="color: rgb(187, 187, 187);"> </span>failure-domain.beta.kubernetes.io/zone<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span><span style="color: rgb(170, 34, 255); font-weight: 700;">whenUnsatisfiable</span>:<span style="color: rgb(187, 187, 187);"> </span>ScheduleAnyway</code></pre>
</details>

