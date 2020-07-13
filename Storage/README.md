# Storage 

<details>
<summary>
<b>Mounted directories that are accessible from inside containers.</b>
</summary>
Volumes
</details>

<details>
<summary>
<b>containers.VolumeMount</b>
</summary>
Mounting of a Volume in a container
name: same as volume
readOnly:
mountPath: Path in the container where the volume is mounted

subPath: Path in the volume to mount in the container
subPathExpr:
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">On-disk files in a Container are ephemeral, which presents some problems for non-trivial applications when running in Containers. First, when a Container crashes, kubelet will restart it, but the files will be lost - the Container starts with a clean state. Second, when running Containers together in a&nbsp;</span><code>Pod</code><span style="color: rgb(34, 34, 34);">&nbsp;it is often necessary to share files between those Containers. The Kubernetes&nbsp;_____&nbsp;</span><span style="color: rgb(34, 34, 34);">abstraction solves both of these problems.</span></b>
</summary>
Volume&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A Kubernetes volume has an explicit lifetime - the same as _____</span></b>
</summary>
The Pod that encloses it
</details>

<details>
<summary>
<b>Is a Volume preserved across Container restarts?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Is a Volume preserved after its Pod's deletion?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Is a volume just a directory with data, accessible to the Containers in its enclosing Pod?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">To use a volume, a Pod specifies what volumes to provide for the Pod in the _____ field,&nbsp;</span><span style="color: rgb(34, 34, 34);">and where to mount those into Containers in the&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field.</span></b>
</summary>
.spec.volumes
<code>.spec.containers[*].volumeMounts</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Can Volumes mount into other volumes?</span></b>
</summary>
No
</details>

<details>
<summary>
<b>Can Volumes have hard links to other Volumes?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A process in a container sees a filesystem view composed from their Docker _____ and _____. The Docker image&nbsp;</span><span style="color: rgb(34, 34, 34);">is at the root of the filesystem hierarchy, and any volumes are mounted at the specified paths within the image.&nbsp;</span></b>
</summary>
image
volumes
</details>

<details>
<summary>
<b>configmap volume syntax&nbsp;
The&nbsp;<a href="https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/"><code>configMap</code></a>&nbsp;resource provides a way to inject configuration data into Pods. The data stored in a&nbsp;<code>ConfigMap</code>&nbsp;object can be referenced in a volume of type&nbsp;<code>configMap</code>&nbsp;and then consumed by containerized applications running in a Pod.When referencing a&nbsp;<code>configMap</code>&nbsp;object, you can simply provide its name in the volume to reference it. You can also customize the path to use for a specific entry in the ConfigMap. For example, to mount the&nbsp;<code>log-config</code>&nbsp;ConfigMap onto a Pod called&nbsp;<code>configmap-pod</code>, you might use the YAML below:</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>configmap-pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>test<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>busybox<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeMounts</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>config-vol<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">mountPath</span>:<span style="color: rgb(187, 187, 187);"> </span>/etc/config<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>config-vol<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">configMap</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>log-config<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">items</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">key</span>:<span style="color: rgb(187, 187, 187);"> </span>log_level<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">            </span><span style="color: rgb(170, 34, 255); font-weight: 700;">path</span>:<span style="color: rgb(187, 187, 187);"> </span>log_level</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Managing storage is a distinct problem from managing compute instances. The PersistentVolume subsystem provides an API for users and administrators that abstracts details of how storage is provided from how it is consumed. To do this, we introduce two new API resources: _____ and _____.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PersistentVolume&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">PersistentVolumeClaim</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using&nbsp;Storage Classes.</span><span style="color: rgb(34, 34, 34);">&nbsp;It is a resource in the cluster just like a node is a cluster resource.&nbsp;</span></b>
</summary>
PersistentVolume&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Do PersistentVolumes have a lifecycle dependent on the Pods that use the PV?</span></b>
</summary>
No
</details>

<details>
<summary>
<b>A <i>_____&nbsp;</i>is a request for storage by a user.&nbsp;</b>
</summary>
PersistentVolumeClaim&nbsp;
</details>

<details>
<summary>
<b>There are two ways PVs may be provisioned:</b>
</summary>
statically or dynamically.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In _____ provisioning, a cluster administrator creates a number of PVs. They carry the details of the real storage, which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption.</span></b>
</summary>
static
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When none of the static PVs the administrator created match a user's PersistentVolumeClaim, the cluster may try to _____ provision a volume specially for the PVC. This provisioning is based on StorageClasses: the PVC must request a storage class</span><span style="color: rgb(34, 34, 34);">&nbsp;and the administrator must have created and configured that class for dynamic provisioning to occur.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">dynamically</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A control loop in the master watches for new PVCs, finds a matching PV (if possible), and _____ them. If a PV was dynamically provisioned for a new PVC, the loop will always _____ that PV to the PVC. Otherwise, the user will always get at least what they asked for, but the volume may be in excess of what was requested.&nbsp;</span></b>
</summary>
binds
</details>

<details>
<summary>
<b>A PVC to PV binding is a one-to-one mapping, using a <b>ClaimRef </b>which is a bi-directional binding between the PersistentVolume and the PersistentVolumeClaim. Once bound, PersistentVolumeClaim binds are _____, regardless of how they were bound.&nbsp;</b>
</summary>
exclusive
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Claims will remain _____ indefinitely if a matching volume does not exist. Claims will be bound as matching volumes become available. For example, a cluster provisioned with many 50Gi PVs would not match a PVC requesting 100Gi. The PVC can be bound when a 100Gi PV is added to the cluster.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">unbound</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____ use claims as volumes.</span></b>
</summary>
Pods
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Once a user has a claim and that claim is bound, the bound PV belongs to the user for as long as they need it. Users schedule Pods and access their claimed PVs by including a </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">section in a Pod's&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">block.</span></b>
</summary>
<code>persistentVolumeClaim</code><code>
</code><code><code>volumes</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If a user deletes a PVC in active use by a Pod, the PVC is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">PVC removal is postponed until _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the PVC is no longer actively used by any Pods.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an admin deletes a PV that is bound to a PVC, the PV is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">&nbsp;PV removal is postponed until...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the PV is no longer bound to a PVC.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can see that a PV or a PVC is protected when its status is </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">and the&nbsp;</span><code>Finalizers</code><span style="color: rgb(34, 34, 34);">&nbsp;list includes&nbsp;<font face="monospace">_____</font></span></b>
</summary>
<code>Terminating</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><code>kubernetes.io/pvc-protection</code><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a user is done with their volume, they can delete the PVC objects from the API that allows reclamation of the resource. The reclaim policy for a PersistentVolume tells the cluster what to do with the volume after it has been released of its claim. Currently, volumes can either be _____, _____, _____.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Retained, Recycled, Deleted.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">reclaim policy allows for manual reclamation of the resource. When the PersistentVolumeClaim is deleted, the PersistentVolume still exists and the volume is considered "released". But it is not yet available for another claim because the previous claimant's data remains on the volume.</span></b>
</summary>
<code>Retain</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For volume plugins that support the </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">reclaim policy, deletion removes both the PersistentVolume object from Kubernetes, as well as the associated storage asset in the external cloud infrastructure. Volumes that were dynamically provisioned inherit the&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy">reclaim policy of their StorageClass</a><span style="color: rgb(34, 34, 34);">, which defaults to&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">. The administrator should configure the StorageClass according to users' expectations; otherwise, the PV must be edited or patched after it is created.</span></b>
</summary>
<code>Delete</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can only expand a PVC if its storage class's </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field is set to true.&nbsp;</span>To request a larger volume for a PVC, edit the PVC object and specify a larger size. This triggers expansion of the volume that backs the underlying PersistentVolume. A new PersistentVolume is never created to satisfy the claim. Instead, an existing volume is resized.</b>
</summary>
<code>allowVolumeExpansion</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b>Can you resize an in-use PVC?</b>
</summary>
Yes - since Kubernetes 1.15.&nbsp;<span style="color: rgb(136, 136, 136);">The&nbsp;</span><code>ExpandInUsePersistentVolumes</code>&nbsp;feature must be enabled.
</details>

<details>
<summary>
<b>PersistentVolume syntax</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolume<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>pv0003<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">capacity</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>5Gi<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeMode</span>:<span style="color: rgb(187, 187, 187);"> </span>Filesystem<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- ReadWriteOnce<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">persistentVolumeReclaimPolicy</span>:<span style="color: rgb(187, 187, 187);"> </span>Recycle<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storageClassName</span>:<span style="color: rgb(187, 187, 187);"> </span>slow<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">mountOptions</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- hard<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- nfsvers=<span style="color: rgb(102, 102, 102);">4.1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">nfs</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">path</span>:<span style="color: rgb(187, 187, 187);"> </span>/tmp<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">server</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">172.17.0.2</span></code></pre>
</details>

<details>
<summary>
<b>Generally, a PV will have a specific storage capacity. This is set using the PV's <font face="monospace">_____&nbsp;</font>attribute. See the Kubernetes&nbsp;<a href="https://git.k8s.io/community/contributors/design-proposals/scheduling/resources.md">Resource Model</a>&nbsp;to understand the units expected by&nbsp;<font face="monospace">_____</font>.</b>
</summary>
<code>capacity</code>&nbsp;
</details>

<details>
<summary>
<b>Kubernetes supports two&nbsp;<code>volumeModes</code>&nbsp;of PersistentVolumes:&nbsp;</b>
</summary>
<code>Filesystem</code>&nbsp;and&nbsp;<code>Block</code>.
</details>

<details>
<summary>
<b><code>volumeMode</code>&nbsp;is an optional API parameter.&nbsp;<font face="monospace">_____&nbsp;</font>is the default mode used when&nbsp;<code>volumeMode</code>&nbsp;parameter is omitted.</b>
</summary>
<code>Filesystem</code>&nbsp;
</details>

<details>
<summary>
<b>A volume with <font face="monospace">_____</font>&nbsp;is&nbsp;<em>mounted</em>&nbsp;into Pods into a directory. If the volume is backed by a block device and the device is empty, Kuberneretes creates a filesystem on the device before mounting it for the first time.</b>
</summary>
volumeMode: Filesystem
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can set the value of&nbsp;</span><code>volumeMode</code><span style="color: rgb(34, 34, 34);">&nbsp;to&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">to use a volume as a raw block device. Such volume is presented into a Pod as a block device, without any filesystem on it. This mode is useful to provide a Pod the fastest possible way to access a volume, without any filesystem layer between the Pod and the volume. On the other hand, the application running in the Pod must know how to handle a raw block device.</span></b>
</summary>
<code>Block</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ReadWriteOnce&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted as read-write by a single node</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ReadOnlyMany&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted read-only by many nodes</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ReadWriteMany&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the volume can be mounted as read-write by many nodes</span>
</details>

<details>
<summary>
<b>In the CLI, the access modes are abbreviated to:<ul><li>RWO - ReadWriteOnce</li><li>ROX - ReadOnlyMany</li><li>RWX - ReadWriteMany</li></ul></b>
</summary>
todo
</details>

<details>
<summary>
<b>Can a volume can only be mounted using more than one access mode at a time?&nbsp;</b>
</summary>
No - even if it supports many.&nbsp;
For example, a GCEPersistentDisk can be mounted as ReadWriteOnce by a single node or ReadOnlyMany by many nodes, but not at the same time.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A PV can have a class, which is specified by setting the </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">attribute to the name of a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/storage-classes/">StorageClass</a><span style="color: rgb(34, 34, 34);">. A PV of a particular class can only be bound to PVCs requesting that class. A PV with no&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">has no class and can only be bound to PVCs that request no particular class.</span></b>
</summary>
<code>storageClassName</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A PV can specify _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to define constraints that limit what nodes this volume can be accessed from. Pods that use a PV will only be scheduled to nodes that are selected by _____.</span></b>
</summary>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.18/#volumenodeaffinity-v1-core">node affinity</a>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A volume will be in one of the following phases:</span><ul><li>_____ -- a free resource that is not yet bound to a claim</li><li>_____&nbsp;-- the volume is bound to a claim</li><li>_____&nbsp;-- the claim has been deleted, but the resource is not yet reclaimed by the cluster</li><li>_____&nbsp;-- the volume has failed its automatic reclamation</li></ul></b>
</summary>
Available, Bound, Released, Failed
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A claim can request a particular class by specifying the name of a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/storage-classes/">StorageClass</a><span style="color: rgb(34, 34, 34);">&nbsp;using the attribute&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">. Only PVs of the requested class, ones with the same&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">as the PVC, can be bound to the PVC.</span></b>
</summary>
storageClassName
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">PersistentVolumes binds are exclusive, and since PersistentVolumeClaims are namespaced objects, mounting claims with "Many" modes (</span><code>ROX</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>RWX</code><span style="color: rgb(34, 34, 34);">) is only possible within _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">one namespace</span>
</details>

<details>
<summary>
<b>PersistentVolume using a Raw Block Volume</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolume<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>block-pv<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">capacity</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>10Gi<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- ReadWriteOnce<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeMode</span>:<span style="color: rgb(187, 187, 187);"> </span>Block<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">persistentVolumeReclaimPolicy</span>:<span style="color: rgb(187, 187, 187);"> </span>Retain<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">fc</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">targetWWNs</span>:<span style="color: rgb(187, 187, 187);"> </span>[<span style="color: rgb(187, 68, 68);">"50060e801049cfd1"</span>]<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lun</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">0</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">readOnly</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">false</span></code></pre>
</details>

<details>
<summary>
<b>PersistentVolumeClaim requesting a Raw Block Volume</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolumeClaim<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>block-pvc<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- ReadWriteOnce<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeMode</span>:<span style="color: rgb(187, 187, 187);"> </span>Block<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">resources</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">requests</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>10Gi</code></pre>
</details>

<details>
<summary>
<b>Pod specification adding Raw Block Device path in container</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>pod-with-block-volume<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>fc-container<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>fedora:<span style="color: rgb(102, 102, 102);">26</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">command</span>:<span style="color: rgb(187, 187, 187);"> </span>[<span style="color: rgb(187, 68, 68);">"/bin/sh"</span>,<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"-c"</span>]<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">args</span>:<span style="color: rgb(187, 187, 187);"> </span>[<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"tail -f /dev/null"</span><span style="color: rgb(187, 187, 187);"> </span>]<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeDevices</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>data<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">devicePath</span>:<span style="color: rgb(187, 187, 187);"> </span>/dev/xvda<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>data<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">persistentVolumeClaim</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">claimName</span>:<span style="color: rgb(187, 187, 187);"> </span>block-pvc</code></pre>
</details>

<details>
<summary>
<b>Create a PersistentVolumeClaim from a Volume Snapshot</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolumeClaim<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>restore-pvc<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storageClassName</span>:<span style="color: rgb(187, 187, 187);"> </span>csi-hostpath-sc<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">dataSource</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>new-snapshot-test<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>VolumeSnapshot<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">apiGroup</span>:<span style="color: rgb(187, 187, 187);"> </span>snapshot.storage.k8s.io<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- ReadWriteOnce<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">resources</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">requests</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>10Gi</code></pre>
</details>

<details>
<summary>
<b>Create PersistentVolumeClaim from an existing PVC</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolumeClaim<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>cloned-pvc<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storageClassName</span>:<span style="color: rgb(187, 187, 187);"> </span>my-csi-plugin<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">dataSource</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>existing-src-pvc-name<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>PersistentVolumeClaim<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">accessModes</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- ReadWriteOnce<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">resources</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">requests</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">storage</span>:<span style="color: rgb(187, 187, 187);"> </span>10Gi</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In Kubernetes, a </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">represents a snapshot of a volume on a storage system.</span></b>
</summary>
<em>VolumeSnapshot</em>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Similar to how API resources&nbsp;</span><code>PersistentVolume</code><span style="color: rgb(34, 34, 34);">&nbsp;and&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">&nbsp;are used to provision volumes for users and administrators,&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">and&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">API resources are provided to create volume snapshots for users and administrators.</span></b>
</summary>
VolumeSnapshot&nbsp;<code>
</code><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b>A <font face="monospace">_____&nbsp;</font>is a snapshot taken from a volume in the cluster that has been provisioned by an administrator. It is a resource in the cluster just like a PersistentVolume is a cluster resource.</b>
</summary>
<code>VolumeSnapshotContent</code>&nbsp;
</details>

<details>
<summary>
<b>A <font face="monospace">_____&nbsp;</font>is a request for snapshot of a volume by a user. It is similar to a PersistentVolumeClaim.</b>
</summary>
<code>VolumeSnapshot</code>&nbsp;
</details>

<details>
<summary>
<b><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">allows you to specify different attributes belonging to a&nbsp;</span><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">. These attributes may differ among snapshots taken from the same volume on the storage system and therefore cannot be expressed by using the same&nbsp;</span><code>StorageClass</code><span style="color: rgb(34, 34, 34);">&nbsp;of a&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">.</span></b>
</summary>
<code>VolumeSnapshotClass</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Are&nbsp;</span><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeSnapshotClass</code><span style="color: rgb(34, 34, 34);">&nbsp;part of the core API?&nbsp;</span></b>
</summary>
No - they are CustomResourceDefinitions.
</details>

<details>
<summary>
<b><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">&nbsp;support is only available for _____ drivers.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">CSI&nbsp;</span>
</details>

<details>
<summary>
<b>The CRDs and snapshot controller installations are the responsibility of _____</b>
</summary>
the Kubernetes distribution
</details>

<details>
<summary>
<b>In volume snapshots,<font face="monospace"> _____&nbsp;</font><span style="color: rgb(34, 34, 34);">are resources in the cluster.&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">are requests for those resources.&nbsp;</span></b>
</summary>
<code>VolumeSnapshotContents</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><code>VolumeSnapshots</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b>There are two ways snapshots may be provisioned:&nbsp;</b>
</summary>
pre-provisioned or dynamically provisioned.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A cluster administrator creates a number of&nbsp;</span><code>VolumeSnapshotContents</code><span style="color: rgb(34, 34, 34);">. They carry the details of the real volume snapshot on the storage system which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption. This is the description of _____ snapshot provisioning.</span></b>
</summary>
pre-provisioned
</details>

<details>
<summary>
<b>Instead of using a pre-existing snapshot, you can request that a snapshot to be _____ taken from a PersistentVolumeClaim. The&nbsp;<a href="https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/">VolumeSnapshotClass</a>&nbsp;specifies storage provider-specific parameters to use when taking a snapshot.</b>
</summary>
dynamically
</details>

<details>
<summary>
<b>The snapshot controller handles the binding of a&nbsp;<code>VolumeSnapshot</code>&nbsp;object with an appropriate&nbsp;<code>VolumeSnapshotContent</code>&nbsp;object, in both pre-provisioned and dynamically provisioned scenarios. The binding is a _____ mapping.&nbsp;
In the case of pre-provisioned binding, the VolumeSnapshot will remain unbound until the requested VolumeSnapshotContent object is created.</b>
</summary>
one-to-one
</details>

<details>
<summary>
<b>While a snapshot is being taken of a PersistentVolumeClaim, that PersistentVolumeClaim is in-use. If you delete a PersistentVolumeClaim API object in active use as a snapshot source, the PersistentVolumeClaim object is not removed immediately. Instead, removal of the PersistentVolumeClaim object is postponed until the snapshot is _____</b>
</summary>
readyToUse or aborted.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">VolumeSnapshot syntax</span></b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>snapshot.storage.k8s.io/v1beta1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>VolumeSnapshot<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>new-snapshot-test<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeSnapshotClassName</span>:<span style="color: rgb(187, 187, 187);"> </span>csi-hostpath-snapclass<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">source</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">persistentVolumeClaimName</span>:<span style="color: rgb(187, 187, 187);"> </span>pvc-test</code></pre>
</details>

<details>
<summary>
<b><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">&nbsp; syntax</span></b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>snapshot.storage.k8s.io/v1beta1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>VolumeSnapshotContent<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>snapcontent-72d9a349-aacd-42d2-a240-d775650d2455<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">deletionPolicy</span>:<span style="color: rgb(187, 187, 187);"> </span>Delete<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">driver</span>:<span style="color: rgb(187, 187, 187);"> </span>hostpath.csi.k8s.io<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">source</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeHandle</span>:<span style="color: rgb(187, 187, 187);"> </span>ee0cfb94-f8d4<span style="color: rgb(102, 102, 102);">-11e9</span>-b2d8-0242ac110002<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeSnapshotClassName</span>:<span style="color: rgb(187, 187, 187);"> </span>csi-hostpath-snapclass<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeSnapshotRef</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>new-snapshot-test<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">namespace</span>:<span style="color: rgb(187, 187, 187);"> </span>default<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">uid</span>:<span style="color: rgb(187, 187, 187);"> </span>72d9a349-aacd-42d2-a240-d775650d2455</code></pre>
</details>

<details>
<summary>
<b><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">is the unique identifier of the volume created on the storage backend and returned by the CSI driver during the volume creation. This field is required for dynamically provisioning a snapshot. It specifies the volume source of the snapshot.</span></b>
</summary>
<code>volumeHandle</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can provision a new volume, pre-populated with data from a snapshot, by using the </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">field in the&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">&nbsp;object.</span></b>
</summary>
<em>dataSource</em><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</details>

<details>
<summary>
<b>StorageClass syntax</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>storage.k8s.io/v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>StorageClass<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>standard<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">provisioner</span>:<span style="color: rgb(187, 187, 187);"> </span>kubernetes.io/aws-ebs<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">parameters</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">type</span>:<span style="color: rgb(187, 187, 187);"> </span>gp2<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">reclaimPolicy</span>:<span style="color: rgb(187, 187, 187);"> </span>Retain<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">allowVolumeExpansion</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">true</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">mountOptions</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- debug<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">volumeBindingMode</span>:<span style="color: rgb(187, 187, 187);"> </span>Immediate</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">PersistentVolumes that are dynamically created by a StorageClass will have the reclaim policy specified in the&nbsp;</span><code>reclaimPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;field of the class, which can be...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">&nbsp;</span><code>Delete</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>Retain</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">To enable dynamic volume provisioning, a cluster administrator needs to pre-create one or more _____ objects for users.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">StorageClass</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Users request dynamically provisioned storage by including a _____ in their&nbsp;</span><code>PersistentVolumeClaim</code></b>
</summary>
<span style="color: rgb(34, 34, 34);">.spec.storageClassName</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An administrator can mark a specific&nbsp;</span><code>StorageClass</code><span style="color: rgb(34, 34, 34);">&nbsp;as default by adding the&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;annotation to it.</span></b>
</summary>
storageclass.kubernetes.io/is-default-class
</details>

<details>
<summary>
<b>Can you attach as many volumes as you want to a node?</b>
</summary>
No - depends on the cloud provider's permitted limit.
</details>

