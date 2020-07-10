# StatefulSet 

<details>
<summary>
StatefulSets

</summary>
*&nbsp;Ability to start and stop Pods in a specific sequence.
* Manages disk storage for their Pods, using a VolumeClaimTemplate object that automatically creates a PersistentVolumeClaim<div>* Each&nbsp;replica in a StatefulSet must be running and ready before Kubernetes starts the&nbsp;next one, and similarly when the StatefulSet is terminated, the replicas will be shut down in reverse order, waiting for each Pod to finish before moving on to the next.

</div>
</details>

<details>
<summary>
<div>StatefulSet is the workload API object used to manage _____</div>
</summary>
stateful applications
</details>

<details>
<summary>
StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about _____&nbsp;of these Pods

</summary>
the ordering and uniqueness
</details>

<details>
<summary>
Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods
</summary>
sticky identity
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">StatefulSet pods are created from the same spec, but are _____</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Each has a persistent identifier that it maintains across any rescheduling.</span></div>
</summary>
<span style="color: rgb(34, 34, 34);">interchangeable</span>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">If you want to use *storage volumes* to provide persistence for your workload, you can use a _____ as part of the solution. Although individual Pods in a _____ are susceptible to failure, the persistent *Pod identifiers* make it easier to *match existing volumes* to the new Pods that replace any that have failed.</span>
</summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
</details>

<details>
<summary>
An application requires several of the following:<div><ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul><div>Which workload object could work best?</div></div>
</summary>
StatefulSet
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Deleting and/or scaling a StatefulSet down will </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;the volumes associated with the StatefulSet.</span>
</summary>
<em>not</em><span style="color: rgb(34, 34, 34);">&nbsp;delete</span>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">StatefulSets currently require a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods. You are responsible for creating it.</span>
</summary>
<a href="https://kubernetes.io/docs/concepts/services-networking/service/#headless-services">Headless Service</a>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></div>
</summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">When using&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#rolling-updates">Rolling Updates</a><span style="color: rgb(34, 34, 34);">&nbsp;with the default&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#pod-management-policies">Pod Management Policy</a><span style="color: rgb(34, 34, 34);">&nbsp;(</span><code>OrderedReady</code><span style="color: rgb(34, 34, 34);">), it's possible to get into a broken state that requires _____&nbsp;to repair</span>
</summary>
<a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#forced-rollback">manual intervention</a>
</details>

<details>
<summary>
StatefulSet syntax
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>apps/v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>StatefulSet<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>web<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">selector</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">matchLabels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">app</span>:<span style="color: rgb(187, 187, 187);"> </span>nginx<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(0, 136, 0); font-style: italic;"># has to match .spec.template.metadata.labels</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">serviceName</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"nginx"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">replicas</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">3</span><span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(0, 136, 0); font-style: italic;"># by default is 1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">template</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">app</span>:<span style="color: rgb(187, 187, 187);"> </span>nginx<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(0, 136, 0); font-style: italic;"># has to match .spec.selector.matchLabels</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">terminationGracePeriodSeconds</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">10</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>nginx<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/nginx-slim:<span style="color: rgb(102, 102, 102);">0.8</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">ports</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">containerPort</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">80</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>web<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeMounts</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>www<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">mountPath</span>:<span style="color: rgb(187, 187, 187);"> </span>/usr/share/nginx/html<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeClaimTemplates</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>www<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);"> </span>[<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"ReadWriteOnce"</span><span style="color: rgb(187, 187, 187);"> </span>]<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storageClassName</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"my-storage-class"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">resources</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">requests</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>1Gi</code></pre>
</details>

