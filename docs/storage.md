<details>
	<summary>
		A _____ is just a directory with data accessible by Containers when mounted.
	</summary>
		volume
</details>

<details>
	<summary>
		A persistentVolume with no storageClassName can only be bound to PersistentVolumeClaims that request _____.
	</summary>
		no storageClassName
</details>

<details>
	<summary>
		A PersistentVolumeClaim can request a particular storage class by specifying the name of a StorageClass using the attribute _____.
	</summary>
		storageClassName
</details>

<details>
	<summary>
		Dynamic volume provisioning is enabled by creating one or more _____ objects for cluster users.
	</summary>
		StorageClass
</details>

<details>
	<summary>
		A _____ object represents a snapshot taken from a volume.
	</summary>
		VolumeSnapshotContent
</details>

<details>
	<summary>
		_____ is the unique identifier of the volume created on the storage backend and returned by the CSI driver during the volume creation. This field is required for dynamically provisioning a snapshot. It specifies the volume source of the snapshot.
	</summary>
		volumeHandle
</details>

<details>
	<summary>
		Are PersistentVolume lifecycles dependent on the Pods that use them? _____
	</summary>
		No
</details>

<details>
	<summary>
		VolumeSnapshot and _____ Objects are used to provision volume snapshots.
	</summary>
		VolumeSnapshotContent
</details>

<details>
	<summary>
		PersistentVolume and PersistentVolumeClaim Objects are used to provision _____.
	</summary>
		volumes
</details>

<details>
	<summary>
		VolumeSnapshot support is only available for _____ drivers.
	</summary>
		CSI
</details>

<details>
	<summary>
		A Pod specifies where and how to mount its volumes inside its containers in the .spec.containers[*]._____ field.
	</summary>
		volumeMounts
</details>

<details>
	<summary>
		A volume is just a directory with data accessible by _____ when mounted.
	</summary>
		Containers
</details>

<details>
	<summary>
		Snapshots may be _____ or dynamically provisioned.
	</summary>
		pre-provisioned
</details>

<details>
	<summary>
		A volume in _____ access mode can be mounted as read-write by a single node
	</summary>
		ReadWriteOnce
</details>

<details>
	<summary>
		A volume is said to be _____, when the claim has been deleted, but the resource is not yet reclaimed by the cluster.
	</summary>
		Released
</details>

<details>
	<summary>
		A _____ specifies what volumes to provide for its containers in the spec.volumes field.
	</summary>
		Pod
</details>

<details>
	<summary>
		A PersistentVolume of a particular storage class can only be bound to _____ requesting that class.
	</summary>
		PersistentVolumeClaim
</details>

<details>
	<summary>
		A PersistentVolume's _____ Policy defines what should be done with it after once released from a a PersistentVolumeClaim. By setting this policy, Volumes may either be Retained, Recycled or Deleted.
	</summary>
		reclaim
</details>

<details>
	<summary>
		A PersistentVolume's reclaim Policy defines what should be done with it after once released from a a PersistentVolumeClaim. By setting this policy, Volumes may either be _____, Recycled or Deleted.
	</summary>
		Retained
</details>

<details>
	<summary>
		PersistentVolume and _____ Objects are used to provision volumes.
	</summary>
		PersistentVolumeClaim
</details>

<details>
	<summary>
		"A deleted PersistentVolumeClaim is subject to a reclaim policy. The ""_____"" policy allows for manual reclamation of resources in the future - the PersistentVolume remains in existence and is considered ""Released"" but unavailable for another claim while the previous claimant's data remains on the volume."
	</summary>
		Retain
</details>

<details>
	<summary>
		If you delete a PersistentVolumeClaim object while a snapshot of it is being taken, its removal is postponed until the snapshot is _____ or aborted.
	</summary>
		readyToUse
</details>

<details>
	<summary>
		_____ represent resources in the cluster, and VolumeSnapshots represent requests for those resources.
	</summary>
		VolumeSnapshotContents
</details>

<details>
	<summary>
		A Pod's volumes are _____ after their Pod is deleted.
	</summary>
		deleted
</details>

<details>
	<summary>
		For volume plugins that support the _____ reclaim policy, deletion removes both the PersistentVolume object and the associated storage asset in the external cloud infrastructure. Volumes that were dynamically provisioned inherit the reclaim policy of their storageClass, which defaults to Delete. Administrators should configure the StorageClass according to users' expectations; otherwise, the PV must be edited or patched after it is created.
	</summary>
		Delete
</details>

<details>
	<summary>
		"A volume with _____ set to ""Block"" represents a raw block device without a filesystem. These volumes provide Pods with the fastest access, but the application must know how to handle a raw block device."
	</summary>
		volumeMode
</details>

<details>
	<summary>
		It is often necessary to share files between Containers in a Pod. _____ objects are designed to solve this problem.
	</summary>
		Volume
</details>

<details>
	<summary>
		VolumeSnapshotClass allows you to specify different attributes belonging to a _____.
	</summary>
		VolumeSnapshot
</details>

<details>
	<summary>
		A volume is said to be _____ when it is free and not yet bound to a claim.
	</summary>
		Available
</details>

<details>
	<summary>
		VolumeSnapshotContents represent resources in the cluster, and _____ represent requests for those resources.
	</summary>
		VolumeSnapshots
</details>

<details>
	<summary>
		_____ allows you to specify different attributes belonging to a VolumeSnapshot.
	</summary>
		VolumeSnapshotClass
</details>

<details>
	<summary>
		A Pod specifies what volumes to provide for its containers in the spec._____ field.
	</summary>
		volumes
</details>

<details>
	<summary>
		A Pod uses a PersistentVolume that has a node affinity towards certain nodes. Whcih node will the Pod be scheduled on? _____
	</summary>
		The node where the PV is available from.
</details>

<details>
	<summary>
		"A volume with volumeMode set to ""_____"" represents a raw block device without a filesystem. These volumes provide Pods with the fastest access, but the application must know how to handle a raw block device."
	</summary>
		Block
</details>

<details>
	<summary>
		A volume is said to be _____ when the volume has failed its automatic reclamation.
	</summary>
		Failed
</details>

<details>
	<summary>
		PersistentVolumes support two _____: Filesystem (default) and Block.
	</summary>
		volumeModes
</details>

<details>
	<summary>
		Can Volumes mount other volumes? _____
	</summary>
		No
</details>

<details>
	<summary>
		A volume in _____ access mode can be mounted read-only by many nodes
	</summary>
		ReadOnlyMany
</details>

<details>
	<summary>
		The Kubernetes control plane watches for new PersistentVolumeClaims, and if it has found a matching _____ it binds them.
	</summary>
		PersistentVolume
</details>

<details>
	<summary>
		In static volume provisioning, a cluster administrator creates a number of _____ which carry the details of the real storage, and are available for use by cluster users.
	</summary>
		PersistentVolumes
</details>

<details>
	<summary>
		A PersistentVolume can have its StorageClass specified by setting the _____ attribute.
	</summary>
		storageClassName
</details>

<details>
	<summary>
		In _____ volume provisioning, a cluster administrator creates a number of PersistentVolumes which carry the details of the real storage, and are available for use by cluster users.
	</summary>
		static
</details>

<details>
	<summary>
		Snapshots may be pre-provisioned or _____.
	</summary>
		dynamically provisioned
</details>

<details>
	<summary>
		A _____ Object represents a snapshot of a volume on a storage system.
	</summary>
		VolumeSnapshot
</details>

<details>
	<summary>
		PersistentVolumes have a specific storage capacity, configured via their _____ attribute.
	</summary>
		Capacity
</details>

<details>
	<summary>
		A PersistentVolume's reclaim Policy defines what should be done with it after once released from a a PersistentVolumeClaim. By setting this policy, Volumes may either be Retained, _____ or Deleted.
	</summary>
		Recycled
</details>

<details>
	<summary>
		PersistentVolumes support two volumeModes: _____ (default) and Block.
	</summary>
		Filesystem
</details>

<details>
	<summary>
		A PersistentVolumeClaim can be expanded if its storageClass has field _____ set to true. To expand it, edit the PersistentVolumeClaim object and specify a larger size. This triggers expansion of the volume that backs the underlying PersistentVolume. A new PersistentVolume is never created to satisfy the claim. Instead, an existing volume is resized.
	</summary>
		allowVolumeExpansion
</details>

<details>
	<summary>
		_____ and PersistentVolumeClaim Objects are used to provision volumes.
	</summary>
		PersistentVolume
</details>

<details>
	<summary>
		When no static PersistentVolume matches a PersistentVolumeClaim, the cluster may try to dynamically provision a volume specially for the PersistentVolumeClaim. The PersistentVolumeClaim must request a _____ with dynamic provisioning configured.
	</summary>
		storageClass
</details>

<details>
	<summary>
		A PersistentVolume may be provisioned either statically or _____.
	</summary>
		dynamically
</details>

<details>
	<summary>
		A PersistentVolumeClaim is in use by a Pod. A user deletes the PersistentVolumeClaim. Is the PersistentVolumeClaim immediately deleted? _____
	</summary>
		No - it is postponed until the PersistentVolumeClaim is no longer used by any Pods.
</details>

<details>
	<summary>
		When a Container crashes, kubelet will restart it, but its on-disk files will be lost unless stored on a _____.
	</summary>
		Volume
</details>

<details>
	<summary>
		A PersistentVolume may be provisioned either _____ or dynamically.
	</summary>
		statically
</details>

<details>
	<summary>
		Are VolumeSnapshot, VolumeSnapshotContent, and VolumeSnapshotClass part of the core Kubernetes API? _____
	</summary>
		No - they are CustomResourceDefinitions.
</details>

<details>
	<summary>
		We delete a PersistentVolume bound to a PersistentVolumeClaim. Is the PersistentVolume deleted immediately? _____
	</summary>
		No
</details>

<details>
	<summary>
		If a PersistentVolume was dynamically provisioned for a new PersistentVolumeClaim, the loop will _____ them together.
	</summary>
		bind
</details>

<details>
	<summary>
		If you delete a PersistentVolumeClaim object while a snapshot of it is being taken, its removal is postponed until the snapshot is readyToUse or _____.
	</summary>
		aborted
</details>

<details>
	<summary>
		"PersistentVolume binds are exclusive. Mounting PersistentVolumeClaims with ""Many"" modes (ROX, RWX) is only possible within one _____."
	</summary>
		namespace
</details>

<details>
	<summary>
		PersistentVolumes support two volumeModes: Filesystem (default) and _____.
	</summary>
		Block
</details>

<details>
	<summary>
		A volume with volumeMode: _____ is mounted into Pods into a directory. If the volume is backed by a block device and the device is empty, Kuberneretes creates a filesystem on the device before mounting it for the first time.
	</summary>
		Filesystem
</details>

<details>
	<summary>
		In pre-provisioned binding, a _____ will remain unbound until the requested VolumeSnapshotContent object is created.
	</summary>
		VolumeSnapshot
</details>

<details>
	<summary>
		Can Volumes have hard links to other Volumes? _____
	</summary>
		No
</details>

<details>
	<summary>
		A persistentVolume with no storageClassName can only be bound to _____ that request no storageClassName.
	</summary>
		PersistentVolumeClaims
</details>

<details>
	<summary>
		A volume has the same lifetime as the _____ that encloses it.
	</summary>
		Pod
</details>

<details>
	<summary>
		You can provision a new volume, pre-populated with data from a snapshot, by filling the _____ field in a PersistentVolumeClaim object.
	</summary>
		dataSource
</details>

<details>
	<summary>
		_____ and VolumeSnapshotContent Objects are used to provision volume snapshots.
	</summary>
		VolumeSnapshot
</details>

<details>
	<summary>
		"A deleted PersistentVolumeClaim is subject to a reclaim policy. The ""Retain"" policy allows for manual reclamation of resources in the future - the PersistentVolume remains in existence and is considered ""_____"" but unavailable for another claim while the previous claimant's data remains on the volume."
	</summary>
		Released
</details>

<details>
	<summary>
		In pre-provisioned binding, a VolumeSnapshot will remain unbound until the requested _____ object is created.
	</summary>
		VolumeSnapshotContent
</details>

<details>
	<summary>
		VolumeSnapshot and VolumeSnapshotContent Objects are used to provision _____.
	</summary>
		volume snapshots
</details>

<details>
	<summary>
		PersistentVolumes that are dynamically created by a StorageClass will have a reclaimPolicy defined, which can be either _____ or Retain
	</summary>
		Delete
</details>

<details>
	<summary>
		In _____ snapshot provisioning, a cluster administrator creates a number of VolumeSnapshotContents carrying details of the real volume snapshot on the storage system. They exist in the Kubernetes API and are available for consumption.
	</summary>
		pre-provisioned
</details>

<details>
	<summary>
		A _____ of a particular storage class can only be bound to PersistentVolumeClaim requesting that class.
	</summary>
		PersistentVolume
</details>

<details>
	<summary>
		A PersistentVolume's _____ constraints what nodes the volume can be accessed from.
	</summary>
		node affinity
</details>

<details>
	<summary>
		Once a PersistentVolumeClaim is bound, its PersistentVolume belongs to the user for as long as they need it. Users schedule Pods and access their claimed PersistentVolumes by including a persistentVolumeClaim section in a Pod's _____ field.
	</summary>
		volumes
</details>

<details>
	<summary>
		PersistentVolumes that are dynamically created by a StorageClass will have a reclaimPolicy defined, which can be either Delete or _____
	</summary>
		Retain
</details>

<details>
	<summary>
		A volume in _____ access mode can be mounted as read-write by many nodes
	</summary>
		ReadWriteMany
</details>

<details>
	<summary>
		PersistentVolumeClaims remain unbound if no matching _____ exists, and will be bound when one becomes available.
	</summary>
		volume
</details>

<details>
	<summary>
		A PersistentVolumeClaim to PersistentVolume binding is a bi-directional, one-to-one mapping represented by a _____ field.
	</summary>
		ClaimRef
</details>

<details>
	<summary>
		A PersistentVolume's reclaim Policy defines what should be done with it after once released from a a PersistentVolumeClaim. By setting this policy, Volumes may either be Retained, Recycled or _____.
	</summary>
		Deleted
</details>

<details>
	<summary>
		Can a volume be mounted using several access modes at a time? _____
	</summary>
		No
</details>

<details>
	<summary>
		Mounted directories accessible from inside containers are called _____
	</summary>
		Volumes
</details>

<details>
	<summary>
		PersistentVolume deletion is not immediate. It is postponed until _____
	</summary>
		the PersistentVolume is no longer bound to a PersistentVolumeClaim.
</details>

<details>
	<summary>
		PersistentVolumes can be bound to a PersistentVolumeClaim if they both have the same _____.
	</summary>
		StorageClassName
</details>

<details>
	<summary>
		Is a Volume preserved across Container restarts? _____
	</summary>
		Yes
</details>

<details>
	<summary>
		A _____ with no storageClassName can only be bound to PersistentVolumeClaims that request no storageClassName.
	</summary>
		persistentVolume
</details>

<details>
	<summary>
		You can request that a snapshot to be dynamically taken from a PersistentVolumeClaim by defining a _____ Object with parameters for the snapshot.
	</summary>
		VolumeSnapshotClass
</details>

<details>
	<summary>
		The Kubernetes control plane watches for new PersistentVolumeClaims, and if it has found a matching PersistentVolume it _____ them.
	</summary>
		binds
</details>

<details>
	<summary>
		Can you resize an in-use PersistentVolumeClaim? _____.
	</summary>
		Yes, via ExpandInUsePersistentVolumes
</details>

