# Secrets 

<details>
<summary>
<b>The resource for storing sensitive information in Kubernetes.</b>
</summary>
Secrets
</details>

<details>
<summary>
<b>Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo</b>
</summary>
Edit standard pod YAML to add volumes with a <i>volumes.secret.secretName </i>value:
<i>spec:</i><i>&nbsp; volumes:</i><i>&nbsp; - name: foo</i><i>&nbsp; &nbsp; secret:</i><i>&nbsp; &nbsp; &nbsp; secretName: mysecret2</i><i>&nbsp; containers:</i><i>&nbsp; - image: nginx</i><i>&nbsp; &nbsp; volumeMounts:</i><i>&nbsp; &nbsp; - name: foo</i><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i>
</details>

<details>
<summary>
<b>How would you improve Kubernetes security</b>
</summary>
Log everything in prod
Alert and apply new CVE fixes
Use audit&nbsp;services (Sonobuoy)

No access to nodes
No access to ETCD
Network segmentation
Resource quotas and policy rules&nbsp;
Secrets as volumes
Scan containers (Snyk, Aqua)

Non-root containers
Read-only filesystems on containers
Disallow sudo
Use kata containers&nbsp;

gVisorAppArmor (lockbox)seccomp (lockbox)SELinux
</details>

