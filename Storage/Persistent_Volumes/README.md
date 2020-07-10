# Persistent_Volumes 

<details>
<summary>
<b>Create a PersistentVolume from a file and check the PersistentVolumes that exist on the cluster</b>
</summary>
<i>kubectl create -f pv.yaml</i>><i>kubectl get pv</i>
</details>

<details>
<summary>
<b>> >&nbsp;Create a PersistentVolumeClaim for normal storage class, called mypvc, a request of 4Gi and an accessMode of ReadWriteOnce</b>
</summary>
><i>kind: PersistentVolumeClaim</i>><i>apiVersion: v1&nbsp;</i>><i>metadata:</i>><i>&nbsp; name: mypvc&nbsp;</i>><i>spec:</i>><i>&nbsp; storageClassName: normal</i>><i>&nbsp; accessModes:</i>><i>&nbsp; - ReadWriteOnce</i>><i>&nbsp; resources:</i>><i>&nbsp; &nbsp; requests:</i>><i>&nbsp; &nbsp; &nbsp; storage: 4Gi</i>

<i>kubectl create -f pvc.yaml</i>
</details>

<details>
<summary>
<b>Show that the PersistentVolumeClaims and the PersistentVolumes of the cluster are working.</b>
</summary>
<i>kubectl get pvc</i>><i>kubectl get pv</i>>Both should show as "Bound"
</details>

<details>
<summary>
<b>Create a busybox pod with command 'sleep 3600', and mount the PersistentVolumeClaim to '/etc/foo'. Connect to the 'busybox' pod, and copy the '/etc/passwd' file to '/etc/foo'.>Create a second pod which is identical with the one you just created. Connect to it and verify that '/etc/foo' contains the 'passwd' file.</b>
</summary>
Create a skeleton YAML file with:
<i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>

add <i>spec.containers.volumeMounts </i>as usual and <i>volumes.persistentVolumeClaim.claimName </i>to match the PVC created.

<i>spec:
&nbsp; containers:</i>><i>&nbsp; - name: busybox</i>><i>&nbsp; &nbsp; volumeMounts:</i>><i>&nbsp; &nbsp; - name: myvol</i>><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i>><i>&nbsp; volumes:</i>><i>&nbsp; - name: myvol</i>><i>&nbsp; &nbsp; persistentVolumeClaim:</i>><i>&nbsp; &nbsp; &nbsp; claimName: mypvc</i>

Create the pod and connect to it
<i>kubectl create -f pod.yaml
kubectl exec busybox -it -- cp /etc/passwd /etc/foo/passwd</i>><i>
</i>>Change the <i>metadata.name</i> in the <i>pod.yaml </i>to "busybox2" and create the second identical pod.
Connect to it and show the contents of /etc/foo
<i>kubectl exec busybox2 -- ls /etc/foo</i>
</details>

