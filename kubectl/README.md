# kubectl 

<details>
<summary>
Command to list Kubernetes services.
</summary>
`kubectl get svc`
</details>

<details>
<summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600;">You're working with a Kubenetes configuration. You need to display merged kubeconfig settings or a specified kubeconfig file. What is the proper command?</span>
</summary>
kubectl config view
</details>

<details>
<summary>
The command for creating a new Kubernetes Secret.
</summary>
`kubectl create secret`
</details>

<details>
<summary>
A `kubectl` flag that allows you to specify the JSON path of properties in JSON output.
</summary>
`-o` along with the `jsonpath` value.

`kubectl get svc -o jsonpath`
</details>

<details>
<summary>
Command to run commands from inside a container that is running on Kubernetes.
</summary>
`kubectl exec`
</details>

<details>
<summary>
<div style="">Provide command to show merged kubeconfig settings.</div>
</summary>
<div style="">kubectl config view

*<img src="0oTJPvbKuWTMMeQulKyLGTNY2RLARnDCp8zV2j-gIwfOsP7bZnuDrQefu_W2rTDZLULQ8xvesq6KAxLWM8eWcTwPK2Nt-GqTy2buW2SEXiJMUXlUuwjnlyCab3c5v1GAjNow.png">*
</div>
</details>

<details>
<summary>
<div style="">What is kubectl?</div>
</summary>
<div style="">CLI for running commands against Kubernetes clusters</div>*
<img src="isELrh5WNHvaPK4BHA8eIJFHKBon5EWZU_8Z16n3bUKaGm2XIEHp2Pk-8pLjEsyFP41Sq-kci93MS5K4mrWQ8bmsQHc5dcY6P9cQQ_UO8rLjCw1L2i7V1QAhyFgb4uoEG_S-.png">*
</details>

<details>
<summary>
How to outut in json, and using jsonpath
</summary>
<strong>kubectl get pods -n kube-system -o json
</strong><strong>kubectl get pods -n kube-system -o json | jq '.items[].metadata.name'
</strong>

</details>

<details>
<summary>
Apply manifest - best practice
</summary>
Use&nbsp;kubectl diff&nbsp;to check what would change before applying any updates to your production cluster.

</details>

<details>
<summary>
Attaching terminal to running container
</summary>
kubectl attach demo-54f4458547-fcx2n

</details>

<details>
<summary>
Busybox alias to run commands much easier...
</summary>
alias bb=<em style="">kubectl run busybox --image=busybox:1.28 --rm -it --restart=Never --command --</em> 

bb nslookup demo ... 
bb wget -qO- http://demo:8888 ... 
bb sh

</details>

<details>
<summary>
How to copy busybox utils to our container in DOCKERFILE, how to use it
</summary>
FROM golang:1.11-alpine AS build&nbsp;<div>WORKDIR /src/&nbsp;</div><div>
</div><div>COPY main.go go.* /src/&nbsp;</div><div>RUN CGO_ENABLED=0&nbsp;</div><div>go build -o /bin/demo&nbsp;</div><div>
</div><div>FROM scratch COPY --from=build /bin/demo /bin/demo&nbsp;</div><div>COPY --from=busybox:1.28 /bin/busybox /bin/busybox*&nbsp;*</div><div>ENTRYPOINT ["/bin/demo"]
</div><div>
</div><div>-----</div><div>use the utils from /bin/busybox</div><div><strong>kubectl exec -it POD_NAME /bin/busybox sh</strong>
</div>
</details>

<details>
<summary>
A kubernetes context is a combination of a&nbsp;

</summary>
<div>* authenticated user</div>* a cluster (could be more than one, but current cluster by default)<div>* namespace
</div><div>
</div><div>kubectl config get-contexts
</div>
</details>

<details>
<summary>
Contex specfic commands
</summary>
<strong>kubectl config use-context gke</strong>
<div><strong>kubectl config set-context myapp --cluster=gke --namespace=myapp</strong><strong>
</strong></div><div><strong>kubectl config current-context</strong><strong>
</strong></div><div><strong>
</strong></div><div><strong>kubectx docker-for-desktop</strong> 
Switched to context "docker-for-desktop".
<strong>
</strong><strong>kubectx -</strong> Switched to context "gke". 
<strong>kubectx -</strong> Switched to context "docker-for-desktop".<strong>
</strong></div><div>
</div>
</details>

<details>
<summary>
When to&nbsp;use Custom resource in Kubernetes?

</summary>
<div>Use a custom resource (CRD or Aggregated API) if most of the following apply:</div>You want to use Kubernetes client libraries and CLIs to create and update the new resource.<div>You want top-level support from kubectl (for example:&nbsp;kubectl get my-object object-name).</div><div>You want to build new automation that watches for updates on the new object, and then CRUD other objects, or vice versa.</div><div>You want to write automation that handles updates to the object.</div><div>You want to use Kubernetes API conventions like&nbsp;.spec,&nbsp;.status, and&nbsp;.metadata.</div><div>You want the object to be an abstraction over a collection of controlled resources, or a summarization of other resources.
</div>
</details>

<details>
<summary>
How to add the values from config.yaml into the data section of the pod manifest?

</summary>
<div>How to achieve following::

apiVersion: v1
data:
&nbsp;config.yaml: |
&nbsp;&nbsp;&nbsp;autoSaveInterval: 60
&nbsp;&nbsp;&nbsp;batchSize: 128
&nbsp;&nbsp;&nbsp;protocols:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- http
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- https
kind: ConfigMap
metadata:
&nbsp;name: demo-config
&nbsp;namespace: demo<strong>
</strong></div><div><strong>
</strong></div><div>--</div><div>
</div><div>kubectl create configmap demo-config --namespace=demo --from-file=config.yaml configmap "demo-config" created
</div><div>
</div><div>kubectl get configmap/demo-config --namespace=demo --export -o yaml &gt;demo-config.yaml
</div><div>
</div>

</details>

<details>
<summary>
kubectl run --command
</summary>
If true and extra arguments are present, use them as the 'command' field in the container, rather than the 'args' field which is the default.
</details>

<details>
<summary>
kubectl run --env
</summary>
env vars to set in the container
</details>

<details>
<summary>
kubectl run --expose
</summary>
Create an external svc for the container
</details>

<details>
<summary>
kubectl run --force
</summary>
If grace-period=0. immediately remove resources from API and bypass graceful deletion.&nbsp;<div>
</div><div>May result in inconsistency or data loss and requires confirmation.</div>
</details>

<details>
<summary>
kubectl run --grace-period
</summary>
<table><tbody><tr><td>Period of time in seconds given to the resource to terminate gracefully. 

1 for immediate shutdown. 

Can only be set to 0 when --force is true (force deletion).</td></tr><tr></tr></tbody></table>

</details>

<details>
<summary>
Example of Labels usage in commands
</summary>
<div>kubectl get pods --show-labels</div><div>
</div>kubectl get pod --selector foo=bar<div>
&nbsp;kubectl get pods -l foo!=bar</div><div>
&nbsp;kubectl get pods -l <em style="">foo notin bar</em></div>
</details>

<details>
<summary>
kubectl get<div>--export</div>
</summary>
<div>Omit cluster-specific info</div>
</details>

<details>
<summary>
kubectl __ --show-labels
</summary>
When printing, show all labels as the last column
</details>

<details>
<summary>
kubectl proxy --port PORT
</summary>
<div>Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.&nbsp;</div><div>
</div><div>Allows serving static content over specified HTTP path.&nbsp;</div><div>
</div><div>All incoming data enters through one port and gets forwarded to the remote kubernetes API Server port, except for the path matching the static content path.</div>
<div>--www</div><div>also serve static files from a given directory</div>
</details>

<details>
<summary>
kubectl config set-credentials
</summary>
Sets a user in kubeconfig<div>
</div><div>their certs</div><div>auth provider<div>environment</div></div><div>command</div>
</details>

<details>
<summary>
kubectl config view
</summary>
Display kubeconfig settings
</details>

<details>
<summary>
kubectl ___ --record
</summary>
<table><tbody><tr><td>Record current kubectl command in the resource annotation. 

If set to false, do not record the command. 

If set to true, record the command. 

If not set, default to updating the existing annotation value only if one already exists.</td></tr><tr></tr></tbody></table>

</details>

<details>
<summary>
kubectl label
</summary>
<div>Adds or overwrites the labels on a resource.</div>
</details>

<details>
<summary>
kubectl replace -f FILENAME
</summary>
<div>Replace a resource by filename or stdin.</div>
</details>

<details>
<summary>
kubectl auth reconcile -f rbac-rules.yaml
</summary>
<div>Reconciles rules for&nbsp;</div><div>Role, RoleBinding, ClusterRole, and ClusterRoleBinding</div><div>
</div><div>Missing objects/namespaces are created if required.</div><div>
</div><div>Superior to 'applying' RBAC resources as it causes semantically-aware merging of rules and subjects.</div><div>*
*</div><div></div>*--remove-extra-permissions*<div>*--remove-extra-subjects*</div><div><div>Removes extra perms/subjects added to roles</div></div>
</details>

<details>
<summary>
kubectl config get-clusters
</summary>
Displays clusters in kubeconfig
</details>

<details>
<summary>
kubectl config set-context NAME
</summary>
Sets a context entry in kubeconfig<div>
</div><div>the context name</div><div>the user</div><div>the namespace</div>
</details>

<details>
<summary>
Check the status of the "hello" job
</summary>
<i>kubectl get jobs</i><div><i>kubectl describe jobs hello</i></div><div><i>kubectl logs job/hello</i></div>
</details>

<details>
<summary>
kubectl ___ --dry-run
</summary>
print the object that would be sent, without sending it.
</details>

<details>
<summary>
kubectl config use-context
</summary>
Sets the current context in kubeconfig
</details>

<details>
<summary>
Selectors
</summary>
An expression&nbsp;that matches&nbsp;a label (or set of labels)

<div><strong>kubectl get pods --all-namespaces --selector app=demo</strong>
</div>
</details>

<details>
<summary>
kubectl config&nbsp;set-cluster NAME
</summary>
Sets a cluster entry in kubeconfig<div>
</div><div>--server</div><div>
</div><div>--certificate-authority</div>
</details>

<details>
<summary>
Resume the paused nginx rollout and verify things start to happen
</summary>
<i>kubectl rollout resume deploy nginx
kubectl rollout history deploy nginx</i>
</details>

<details>
<summary>
kubectl patch --patch PATCH
</summary>
<div>Update resource fields using either "json merge" or&nbsp; "strategic merge"</div><div>
</div><div>*--local*</div><div>If true, patch will operate on the content of the file, not the server-side resource.</div>
</details>

<details>
<summary>
kubectl diff
</summary>
<div>Diff configurations specified by filename or stdin between the current online configuration, and the configuration as it would be if applied.</div><div>
</div><div>Output is always YAML.
</div><div><div>
</div></div><div>*--server-side*</div><div>Run apply in-cluster, not local</div>
</details>

<details>
<summary>
kubectl describe
</summary>
<div>Print a detailed description of the selected resource/group of resources,&nbsp;</div><div>
</div><div>Includies events or controllers.&nbsp;</div>
</details>

<details>
<summary>
kubectl cluster-info dump [--namespaces NAMESPACES]
</summary>
Dumps debug cluster info and pod logs by namespace (default: kube-system)<div>
</div><div>--all-namespaces</div><div>--output-directory</div><div>-o</div>
</details>

<details>
<summary>
Create a secret called mysecret with the values password=mypass
</summary>
<i>kubectl create secret generic mysecret --from-literal=password=mypass</i>
</details>

<details>
<summary>
Get the value of secret "mysecret2"
</summary>
<i>kubectl get secret mysecret2 -o yaml --export</i>
the value will be base64 encoded, so decode it:
<i>echo &lt;value&gt; | base64 -d</i>
</details>

<details>
<summary>
kubectl cluster-info
</summary>
Display addresses of<div>
</div><div>Master</div><div>KubeDNS</div><div>Metrics-Server
<div>Services labelled&nbsp;*kubernetes.io/cluster-service=true*
</div></div>
</details>

<details>
<summary>
Create a new serviceaccount called 'myuser'
</summary>
<i>kubectl create sa myuser --dry-run -o yaml &gt; serviceaccount.yaml</i><div>or get a template with
<i>kubectl get sa default -o yaml --export &gt; sa.yaml</i></div>
</details>

<details>
<summary>
See all the service accounts of the cluster in all namespaces
</summary>
<i>kubectl get sa --all-namespaces</i>
</details>

<details>
<summary>
kubectl config set
</summary>
Sets a value in kubeconfig<div>
</div><div>kubectl config set clusters.my-cluster.server https://1.2.3.4
</div>
</details>

<details>
<summary>
kubectl plugin list
</summary>
List kubectl plugins
</details>

<details>
<summary>
kubectl create
</summary>
<div>Create a resource from a file or from stdin.</div><div>JSON and YAML formats are accepted.</div><h3>Usage</h3><div><code>$ create -f FILENAME</code></div>
</details>

<details>
<summary>
kubectl get<div>--field-selector</div>
</summary>
Filter on object values rather than labels

</details>

<details>
<summary>
kubectl config current-context
</summary>
Prints context
</details>

<details>
<summary>
<div>kubectl check if an action verb is allowed</div>
</summary>
kubectl auth can-i VERB [TYPE TYPE/NAME]
</details>

<details>
<summary>
kubectl config delete-cluster
</summary>
Delete a cluster from kubeconfig
</details>

<details>
<summary>
kubectl config get-contexts
</summary>
Display contexts from kubeconfig
</details>

