# kubectl 

<details>
<summary>
<b>Command to list Kubernetes services.</b>
</summary>
`kubectl get svc`
</details>

<details>
<summary>
<b><span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600;">You're working with a Kubenetes configuration. You need to display merged kubeconfig settings or a specified kubeconfig file. What is the proper command?</span></b>
</summary>
kubectl config view
</details>

<details>
<summary>
<b>The command for creating a new Kubernetes Secret.</b>
</summary>
`kubectl create secret`
</details>

<details>
<summary>
<b>A `kubectl` flag that allows you to specify the JSON path of properties in JSON output.</b>
</summary>
`-o` along with the `jsonpath` value.

`kubectl get svc -o jsonpath`
</details>

<details>
<summary>
<b>Command to run commands from inside a container that is running on Kubernetes.</b>
</summary>
`kubectl exec`
</details>

<details>
<summary>
<b>style="">Provide command to show merged kubeconfig settings.</b>
</summary>
style="">kubectl config view

<b><img src="0oTJPvbKuWTMMeQulKyLGTNY2RLARnDCp8zV2j-gIwfOsP7bZnuDrQefu_W2rTDZLULQ8xvesq6KAxLWM8eWcTwPK2Nt-GqTy2buW2SEXiJMUXlUuwjnlyCab3c5v1GAjNow.png"></b>
</details>

<details>
<summary>
<b>style="">What is kubectl?</b>
</summary>
style="">CLI for running commands against Kubernetes clusters<b>
<img src="isELrh5WNHvaPK4BHA8eIJFHKBon5EWZU_8Z16n3bUKaGm2XIEHp2Pk-8pLjEsyFP41Sq-kci93MS5K4mrWQ8bmsQHc5dcY6P9cQQ_UO8rLjCw1L2i7V1QAhyFgb4uoEG_S-.png"></b>
</details>

<details>
<summary>
<b>How to outut in json, and using jsonpath</b>
</summary>
<strong>kubectl get pods -n kube-system -o json
</strong><strong>kubectl get pods -n kube-system -o json | jq '.items[].metadata.name'
</strong>
</details>

<details>
<summary>
<b>Apply manifest - best practice</b>
</summary>
Use&nbsp;kubectl diff&nbsp;to check what would change before applying any updates to your production cluster.
</details>

<details>
<summary>
<b>Attaching terminal to running container</b>
</summary>
kubectl attach demo-54f4458547-fcx2n
</details>

<details>
<summary>
<b>Busybox alias to run commands much easier...</b>
</summary>
alias bb=<em style="">kubectl run busybox --image=busybox:1.28 --rm -it --restart=Never --command --</em> 

bb nslookup demo ... 
bb wget -qO- http://demo:8888 ... 
bb sh
</details>

<details>
<summary>
<b>How to copy busybox utils to our container in DOCKERFILE, how to use it</b>
</summary>
FROM golang:1.11-alpine AS build&nbsp;>WORKDIR /src/&nbsp;>
>COPY main.go go.* /src/&nbsp;>RUN CGO_ENABLED=0&nbsp;>go build -o /bin/demo&nbsp;>
>FROM scratch COPY --from=build /bin/demo /bin/demo&nbsp;>COPY --from=busybox:1.28 /bin/busybox /bin/busybox<b>&nbsp;</b>>ENTRYPOINT ["/bin/demo"]
>
>----->use the utils from /bin/busybox><strong>kubectl exec -it POD_NAME /bin/busybox sh</strong>
</details>

<details>
<summary>
<b>A kubernetes context is a combination of a&nbsp;</b>
</summary>
>* authenticated user* a cluster (could be more than one, but current cluster by default)>* namespace
>
>kubectl config get-contexts
</details>

<details>
<summary>
<b>Contex specfic commands</b>
</summary>
<strong>kubectl config use-context gke</strong>
><strong>kubectl config set-context myapp --cluster=gke --namespace=myapp</strong><strong>
</strong>><strong>kubectl config current-context</strong><strong>
</strong>><strong>
</strong>><strong>kubectx docker-for-desktop</strong> 
Switched to context "docker-for-desktop".
<strong>
</strong><strong>kubectx -</strong> Switched to context "gke". 
<strong>kubectx -</strong> Switched to context "docker-for-desktop".<strong>
</strong>>
</details>

<details>
<summary>
<b>When to&nbsp;use Custom resource in Kubernetes?</b>
</summary>
>Use a custom resource (CRD or Aggregated API) if most of the following apply:You want to use Kubernetes client libraries and CLIs to create and update the new resource.>You want top-level support from kubectl (for example:&nbsp;kubectl get my-object object-name).>You want to build new automation that watches for updates on the new object, and then CRUD other objects, or vice versa.>You want to write automation that handles updates to the object.>You want to use Kubernetes API conventions like&nbsp;.spec,&nbsp;.status, and&nbsp;.metadata.>You want the object to be an abstraction over a collection of controlled resources, or a summarization of other resources.
</details>

<details>
<summary>
<b>How to add the values from config.yaml into the data section of the pod manifest?</b>
</summary>
>How to achieve following::

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
</strong>><strong>
</strong>>-->
>kubectl create configmap demo-config --namespace=demo --from-file=config.yaml configmap "demo-config" created
>
>kubectl get configmap/demo-config --namespace=demo --export -o yaml &gt;demo-config.yaml
>
</details>

<details>
<summary>
<b>kubectl run --command</b>
</summary>
If true and extra arguments are present, use them as the 'command' field in the container, rather than the 'args' field which is the default.
</details>

<details>
<summary>
<b>kubectl run --env</b>
</summary>
env vars to set in the container
</details>

<details>
<summary>
<b>kubectl run --expose</b>
</summary>
Create an external svc for the container
</details>

<details>
<summary>
<b>kubectl run --force</b>
</summary>
If grace-period=0. immediately remove resources from API and bypass graceful deletion.&nbsp;>
>May result in inconsistency or data loss and requires confirmation.
</details>

<details>
<summary>
<b>kubectl run --grace-period</b>
</summary>
<table><tbody><tr><td>Period of time in seconds given to the resource to terminate gracefully. 

1 for immediate shutdown. 

Can only be set to 0 when --force is true (force deletion).</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b>Example of Labels usage in commands</b>
</summary>
>kubectl get pods --show-labels>
kubectl get pod --selector foo=bar>
&nbsp;kubectl get pods -l foo!=bar>
&nbsp;kubectl get pods -l <em style="">foo notin bar</em>
</details>

<details>
<summary>
<b>kubectl get>--export</b>
</summary>
>Omit cluster-specific info
</details>

<details>
<summary>
<b>kubectl __ --show-labels</b>
</summary>
When printing, show all labels as the last column
</details>

<details>
<summary>
<b>kubectl proxy --port PORT</b>
</summary>
>Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.&nbsp;>
>Allows serving static content over specified HTTP path.&nbsp;>
>All incoming data enters through one port and gets forwarded to the remote kubernetes API Server port, except for the path matching the static content path.
>--www>also serve static files from a given directory
</details>

<details>
<summary>
<b>kubectl config set-credentials</b>
</summary>
Sets a user in kubeconfig>
>their certs>auth provider>environment>command
</details>

<details>
<summary>
<b>kubectl config view</b>
</summary>
Display kubeconfig settings
</details>

<details>
<summary>
<b>kubectl ___ --record</b>
</summary>
<table><tbody><tr><td>Record current kubectl command in the resource annotation. 

If set to false, do not record the command. 

If set to true, record the command. 

If not set, default to updating the existing annotation value only if one already exists.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b>kubectl label</b>
</summary>
>Adds or overwrites the labels on a resource.
</details>

<details>
<summary>
<b>kubectl replace -f FILENAME</b>
</summary>
>Replace a resource by filename or stdin.
</details>

<details>
<summary>
<b>kubectl auth reconcile -f rbac-rules.yaml</b>
</summary>
>Reconciles rules for&nbsp;>Role, RoleBinding, ClusterRole, and ClusterRoleBinding>
>Missing objects/namespaces are created if required.>
>Superior to 'applying' RBAC resources as it causes semantically-aware merging of rules and subjects.><b>
</b>><b>--remove-extra-permissions</b>><b>--remove-extra-subjects</b>>>Removes extra perms/subjects added to roles
</details>

<details>
<summary>
<b>kubectl config get-clusters</b>
</summary>
Displays clusters in kubeconfig
</details>

<details>
<summary>
<b>kubectl config set-context NAME</b>
</summary>
Sets a context entry in kubeconfig>
>the context name>the user>the namespace
</details>

<details>
<summary>
<b>Check the status of the "hello" job</b>
</summary>
<i>kubectl get jobs</i>><i>kubectl describe jobs hello</i>><i>kubectl logs job/hello</i>
</details>

<details>
<summary>
<b>kubectl ___ --dry-run</b>
</summary>
print the object that would be sent, without sending it.
</details>

<details>
<summary>
<b>kubectl config use-context</b>
</summary>
Sets the current context in kubeconfig
</details>

<details>
<summary>
<b>Selectors</b>
</summary>
An expression&nbsp;that matches&nbsp;a label (or set of labels)

><strong>kubectl get pods --all-namespaces --selector app=demo</strong>
</details>

<details>
<summary>
<b>kubectl config&nbsp;set-cluster NAME</b>
</summary>
Sets a cluster entry in kubeconfig>
>--server>
>--certificate-authority
</details>

<details>
<summary>
<b>Resume the paused nginx rollout and verify things start to happen</b>
</summary>
<i>kubectl rollout resume deploy nginx
kubectl rollout history deploy nginx</i>
</details>

<details>
<summary>
<b>kubectl patch --patch PATCH</b>
</summary>
>Update resource fields using either "json merge" or&nbsp; "strategic merge">
><b>--local</b>>If true, patch will operate on the content of the file, not the server-side resource.
</details>

<details>
<summary>
<b>kubectl diff</b>
</summary>
>Diff configurations specified by filename or stdin between the current online configuration, and the configuration as it would be if applied.>
>Output is always YAML.
>>
><b>--server-side</b>>Run apply in-cluster, not local
</details>

<details>
<summary>
<b>kubectl describe</b>
</summary>
>Print a detailed description of the selected resource/group of resources,&nbsp;>
>Includies events or controllers.&nbsp;
</details>

<details>
<summary>
<b>kubectl cluster-info dump [--namespaces NAMESPACES]</b>
</summary>
Dumps debug cluster info and pod logs by namespace (default: kube-system)>
>--all-namespaces>--output-directory>-o
</details>

<details>
<summary>
<b>Create a secret called mysecret with the values password=mypass</b>
</summary>
<i>kubectl create secret generic mysecret --from-literal=password=mypass</i>
</details>

<details>
<summary>
<b>Get the value of secret "mysecret2"</b>
</summary>
<i>kubectl get secret mysecret2 -o yaml --export</i>
the value will be base64 encoded, so decode it:
<i>echo &lt;value&gt; | base64 -d</i>
</details>

<details>
<summary>
<b>kubectl cluster-info</b>
</summary>
Display addresses of>
>Master>KubeDNS>Metrics-Server
>Services labelled&nbsp;<b>kubernetes.io/cluster-service=true</b>
</details>

<details>
<summary>
<b>Create a new serviceaccount called 'myuser'</b>
</summary>
<i>kubectl create sa myuser --dry-run -o yaml &gt; serviceaccount.yaml</i>>or get a template with
<i>kubectl get sa default -o yaml --export &gt; sa.yaml</i>
</details>

<details>
<summary>
<b>See all the service accounts of the cluster in all namespaces</b>
</summary>
<i>kubectl get sa --all-namespaces</i>
</details>

<details>
<summary>
<b>kubectl config set</b>
</summary>
Sets a value in kubeconfig>
>kubectl config set clusters.my-cluster.server https://1.2.3.4
</details>

<details>
<summary>
<b>kubectl plugin list</b>
</summary>
List kubectl plugins
</details>

<details>
<summary>
<b>kubectl create</b>
</summary>
>Create a resource from a file or from stdin.>JSON and YAML formats are accepted.<h3>Usage</h3>><code>$ create -f FILENAME</code>
</details>

<details>
<summary>
<b>kubectl get>--field-selector</b>
</summary>
Filter on object values rather than labels
</details>

<details>
<summary>
<b>kubectl config current-context</b>
</summary>
Prints context
</details>

<details>
<summary>
<b>>kubectl check if an action verb is allowed</b>
</summary>
kubectl auth can-i VERB [TYPE TYPE/NAME]
</details>

<details>
<summary>
<b>kubectl config delete-cluster</b>
</summary>
Delete a cluster from kubeconfig
</details>

<details>
<summary>
<b>kubectl config get-contexts</b>
</summary>
Display contexts from kubeconfig
</details>

