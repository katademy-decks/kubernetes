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

