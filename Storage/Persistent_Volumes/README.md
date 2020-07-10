# Persistent_Volumes 

<details>
<summary>
<b>Create a PersistentVolume from a file and check the PersistentVolumes that exist on the cluster</b>
</summary>
<i>kubectl create -f pv.yaml</i><div><i>kubectl get pv</i></div>
</details>

<details>
<summary>
<b><div></div> <div></div>&nbsp;Create a PersistentVolumeClaim for normal storage class, called mypvc, a request of 4Gi and an accessMode of ReadWriteOnce</b>
</summary>
<div><i>kind: PersistentVolumeClaim</i></div><div><i>apiVersion: v1&nbsp;</i></div><div><i>metadata:</i></div><div><i>&nbsp; name: mypvc&nbsp;</i></div><div><i>spec:</i></div><div><i>&nbsp; storageClassName: normal</i></div><div><i>&nbsp; accessModes:</i></div><div><i>&nbsp; - ReadWriteOnce</i></div><div><i>&nbsp; resources:</i></div><div><i>&nbsp; &nbsp; requests:</i></div><div><i>&nbsp; &nbsp; &nbsp; storage: 4Gi</i>

<i>kubectl create -f pvc.yaml</i></div>
</details>

<details>
<summary>
<b>Show that the PersistentVolumeClaims and the PersistentVolumes of the cluster are working.</b>
</summary>
<i>kubectl get pvc</i><div><i>kubectl get pv</i></div><div>Both should show as "Bound"</div>
</details>

<details>
<summary>
<b>Create a busybox pod with command 'sleep 3600', and mount the PersistentVolumeClaim to '/etc/foo'. Connect to the 'busybox' pod, and copy the '/etc/passwd' file to '/etc/foo'.<div>Create a second pod which is identical with the one you just created. Connect to it and verify that '/etc/foo' contains the 'passwd' file.</div></b>
</summary>
Create a skeleton YAML file with:
<i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>

add <i>spec.containers.volumeMounts </i>as usual and <i>volumes.persistentVolumeClaim.claimName </i>to match the PVC created.

<i>spec:
&nbsp; containers:</i><div><i>&nbsp; - name: busybox</i></div><div><i>&nbsp; &nbsp; volumeMounts:</i></div><div><i>&nbsp; &nbsp; - name: myvol</i></div><div><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i></div><div><i>&nbsp; volumes:</i></div><div><i>&nbsp; - name: myvol</i></div><div><i>&nbsp; &nbsp; persistentVolumeClaim:</i></div><div><i>&nbsp; &nbsp; &nbsp; claimName: mypvc</i>

Create the pod and connect to it
<i>kubectl create -f pod.yaml
kubectl exec busybox -it -- cp /etc/passwd /etc/foo/passwd</i></div><div><i>
</i></div><div>Change the <i>metadata.name</i> in the <i>pod.yaml </i>to "busybox2" and create the second identical pod.
Connect to it and show the contents of /etc/foo
<i>kubectl exec busybox2 -- ls /etc/foo</i></div>
</details>

