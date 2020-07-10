# Kubernetes 

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
<b><div style="">Provide command to show merged kubeconfig settings.</div></b>
</summary>
<div style="">kubectl config view

<b><img src="0oTJPvbKuWTMMeQulKyLGTNY2RLARnDCp8zV2j-gIwfOsP7bZnuDrQefu_W2rTDZLULQ8xvesq6KAxLWM8eWcTwPK2Nt-GqTy2buW2SEXiJMUXlUuwjnlyCab3c5v1GAjNow.png"></b>
</div>
</details>

<details>
<summary>
<b><div style="">What is kubectl?</div></b>
</summary>
<div style="">CLI for running commands against Kubernetes clusters</div><b>
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
FROM golang:1.11-alpine AS build&nbsp;<div>WORKDIR /src/&nbsp;</div><div>
</div><div>COPY main.go go.* /src/&nbsp;</div><div>RUN CGO_ENABLED=0&nbsp;</div><div>go build -o /bin/demo&nbsp;</div><div>
</div><div>FROM scratch COPY --from=build /bin/demo /bin/demo&nbsp;</div><div>COPY --from=busybox:1.28 /bin/busybox /bin/busybox<b>&nbsp;</b></div><div>ENTRYPOINT ["/bin/demo"]
</div><div>
</div><div>-----</div><div>use the utils from /bin/busybox</div><div><strong>kubectl exec -it POD_NAME /bin/busybox sh</strong>
</div>
</details>

<details>
<summary>
<b>A kubernetes context is a combination of a&nbsp;</b>
</summary>
<div>* authenticated user</div>* a cluster (could be more than one, but current cluster by default)<div>* namespace
</div><div>
</div><div>kubectl config get-contexts
</div>
</details>

<details>
<summary>
<b>Contex specfic commands</b>
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
<b>When to&nbsp;use Custom resource in Kubernetes?</b>
</summary>
<div>Use a custom resource (CRD or Aggregated API) if most of the following apply:</div>You want to use Kubernetes client libraries and CLIs to create and update the new resource.<div>You want top-level support from kubectl (for example:&nbsp;kubectl get my-object object-name).</div><div>You want to build new automation that watches for updates on the new object, and then CRUD other objects, or vice versa.</div><div>You want to write automation that handles updates to the object.</div><div>You want to use Kubernetes API conventions like&nbsp;.spec,&nbsp;.status, and&nbsp;.metadata.</div><div>You want the object to be an abstraction over a collection of controlled resources, or a summarization of other resources.
</div>
</details>

<details>
<summary>
<b>How to add the values from config.yaml into the data section of the pod manifest?</b>
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
If grace-period=0. immediately remove resources from API and bypass graceful deletion.&nbsp;<div>
</div><div>May result in inconsistency or data loss and requires confirmation.</div>
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
<div>kubectl get pods --show-labels</div><div>
</div>kubectl get pod --selector foo=bar<div>
&nbsp;kubectl get pods -l foo!=bar</div><div>
&nbsp;kubectl get pods -l <em style="">foo notin bar</em></div>
</details>

<details>
<summary>
<b>kubectl get<div>--export</div></b>
</summary>
<div>Omit cluster-specific info</div>
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
<div>Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.&nbsp;</div><div>
</div><div>Allows serving static content over specified HTTP path.&nbsp;</div><div>
</div><div>All incoming data enters through one port and gets forwarded to the remote kubernetes API Server port, except for the path matching the static content path.</div>
<div>--www</div><div>also serve static files from a given directory</div>
</details>

<details>
<summary>
<b>kubectl config set-credentials</b>
</summary>
Sets a user in kubeconfig<div>
</div><div>their certs</div><div>auth provider<div>environment</div></div><div>command</div>
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
<div>Adds or overwrites the labels on a resource.</div>
</details>

<details>
<summary>
<b>kubectl replace -f FILENAME</b>
</summary>
<div>Replace a resource by filename or stdin.</div>
</details>

<details>
<summary>
<b>kubectl auth reconcile -f rbac-rules.yaml</b>
</summary>
<div>Reconciles rules for&nbsp;</div><div>Role, RoleBinding, ClusterRole, and ClusterRoleBinding</div><div>
</div><div>Missing objects/namespaces are created if required.</div><div>
</div><div>Superior to 'applying' RBAC resources as it causes semantically-aware merging of rules and subjects.</div><div><b>
</b></div><div></div><b>--remove-extra-permissions</b><div><b>--remove-extra-subjects</b></div><div><div>Removes extra perms/subjects added to roles</div></div>
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
Sets a context entry in kubeconfig<div>
</div><div>the context name</div><div>the user</div><div>the namespace</div>
</details>

<details>
<summary>
<b>Check the status of the "hello" job</b>
</summary>
<i>kubectl get jobs</i><div><i>kubectl describe jobs hello</i></div><div><i>kubectl logs job/hello</i></div>
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

<div><strong>kubectl get pods --all-namespaces --selector app=demo</strong>
</div>
</details>

<details>
<summary>
<b>kubectl config&nbsp;set-cluster NAME</b>
</summary>
Sets a cluster entry in kubeconfig<div>
</div><div>--server</div><div>
</div><div>--certificate-authority</div>
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
<div>Update resource fields using either "json merge" or&nbsp; "strategic merge"</div><div>
</div><div><b>--local</b></div><div>If true, patch will operate on the content of the file, not the server-side resource.</div>
</details>

<details>
<summary>
<b>kubectl diff</b>
</summary>
<div>Diff configurations specified by filename or stdin between the current online configuration, and the configuration as it would be if applied.</div><div>
</div><div>Output is always YAML.
</div><div><div>
</div></div><div><b>--server-side</b></div><div>Run apply in-cluster, not local</div>
</details>

<details>
<summary>
<b>kubectl describe</b>
</summary>
<div>Print a detailed description of the selected resource/group of resources,&nbsp;</div><div>
</div><div>Includies events or controllers.&nbsp;</div>
</details>

<details>
<summary>
<b>kubectl cluster-info dump [--namespaces NAMESPACES]</b>
</summary>
Dumps debug cluster info and pod logs by namespace (default: kube-system)<div>
</div><div>--all-namespaces</div><div>--output-directory</div><div>-o</div>
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
Display addresses of<div>
</div><div>Master</div><div>KubeDNS</div><div>Metrics-Server
<div>Services labelled&nbsp;<b>kubernetes.io/cluster-service=true</b>
</div></div>
</details>

<details>
<summary>
<b>Create a new serviceaccount called 'myuser'</b>
</summary>
<i>kubectl create sa myuser --dry-run -o yaml &gt; serviceaccount.yaml</i><div>or get a template with
<i>kubectl get sa default -o yaml --export &gt; sa.yaml</i></div>
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
Sets a value in kubeconfig<div>
</div><div>kubectl config set clusters.my-cluster.server https://1.2.3.4
</div>
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
<div>Create a resource from a file or from stdin.</div><div>JSON and YAML formats are accepted.</div><h3>Usage</h3><div><code>$ create -f FILENAME</code></div>
</details>

<details>
<summary>
<b>kubectl get<div>--field-selector</div></b>
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
<b><div>kubectl check if an action verb is allowed</div></b>
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

<details>
<summary>
<b>Kubernetes Master controls...</b>
</summary>
Kubernetes nodes
</details>

<details>
<summary>
<b>The format used for Kubernetes resource files.</b>
</summary>
YAML
</details>

<details>
<summary>
<b>The name of the Kubernetes Controller that provides declarative updates for pods.</b>
</summary>
Deployments
</details>

<details>
<summary>
<b>The resource for storing sensitive information in Kubernetes.</b>
</summary>
Secrets
</details>

<details>
<summary>
<b>A Kubernetes resource that exposes deployments.</b>
</summary>
Services
</details>

<details>
<summary>
<b>Where do container images need to exist for Kubernetes to work with them?</b>
</summary>
A container registry.
</details>

<details>
<summary>
<b>Kubernetes deployments can be in what states?&nbsp;</b>
</summary>
1.&nbsp;<b>Progressing</b>, which means the deployment is in the process of performing a task&nbsp;
2.&nbsp;<b>Completed</b>, which means the rollout of containers is complete and all pods are running the latest version of containers&nbsp;
3.&nbsp;<b>Failed</b>, which indicates the deployment process encountered a problem it could not recover from&nbsp;&nbsp;

<img src="paste-b161711b323beee4f9321701871a89dbe94c759c.jpg">
<img src="paste-eb67b2c5aa380b7fa66366a34219cd767c81a081.jpg">
<img src="paste-3b99c3b118c2e59529bf12a6a554aa2c5c5bab73.jpg">
</details>

<details>
<summary>
<b>In order to add a node to a cluster, you decide to edit the managed instance group of the cluster and enable autoscaling. Is that a valid approach?</b>
</summary>
No, because you should not manually manage the MIG behind a cluster.
</details>

<details>
<summary>
<b>Which structure must be created before you can monitor a Kubernetes cluster with Stackdriver?</b>
</summary>
A workspace

<b><img src="nGFyNMS14MPw03_cnfdIJZ--s-jYpF7pLU2wkUVf9nvvzzflV3U6od1lDT-hHL85uWIqjkJwvn53Aqb2k01Mwi26NW3D0eGInXdh9D2gw9uH7Mr1yFo6jHMw6QhQuZ6YevJQ.png"></b>
</details>

<details>
<summary>
<b>What's the name of a Kubernetes entity that executes workloads?</b>
</summary>
Node

<img src="paste-2dd3a0d3b489fe0cc29ee86ddb9283470450af35.jpg">
</details>

<details>
<summary>
<b>What is a Kubernetes Service?</b>
</summary>
<div style="">It's an abstraction which defines a logical set of Pods and a policy to acces them


<img src="paste-e82468366eccc0c0dfc017a1d05d4409d382138b.jpg">
<img src="paste-41692f1c96c820c7b1799b317dbf422210327b46.jpg">
</div>
</details>

<details>
<summary>
<b>List functionalities of K8s <b>Service</b></b>
</summary>
1. It exposes Pods to external traffic
2. It provides Load balancing traffic across multiple Pods
3. It allows Pods to die and replicate without impacting the application
<img src="paste-757549a455e7be1b4e5c13d62ef77db0233367a9.jpg">
</details>

<details>
<summary>
<b>List possible ServiceTypes for Kubernetes Service</b>
</summary>
1. ClusterIP (default)
2. NodePort
3. LoadBalancer
4. ExternalName
5. Headless

6. Ingress (<b>not</b>&nbsp;technically a ServiceType - it's used to expose multiple services under the same IP adress)

<b><img src="0x26uG-Rv4DcK-uh0Vlwsbr9vrbQSXUaSlgy5O5mBgdo50hlKMi7qQ2RSPHV0aqMx4P6M4eP9XLziphq2XFto9E8Wop_CEIysF2i3NgRplcKvohnsc44dVx6af1rRM_FswBx.png"></b>
<img src="paste-6ee96b90dd90bcc12c5964bf7930e8f4afc8c2d4.jpg">
</details>

<details>
<summary>
<b>Which <b>type </b>of Service makes it only reachable from within the cluster?</b>
</summary>
<b>ClusterIP </b>(default ServiceType)

<img src="paste-5591abe579a78ac5cfdd8e894ab1f587dc262e40.jpg">
</details>

<details>
<summary>
<b><div style="">What is a Kubernetes Namespace?</div></b>
</summary>
<div style="">An abstraction used to support multiple virtual Clusters on the same physical cluster</div>
<b><img src="m9Ge4aLkFv8EIStMhDpCp5mPo755jtUpjrdCykDG1_Citr7XFC4eMUkveG2hbJ6sMhsx63Eqtz73CCubJ9Wee2U44cPhKtCz3FWOo8jCT1khDkjFMsPsnlPv5jlYEmWW4CLX.png">
</b><b><img src="MX5J-ddeKxh4Xg18FH9NJm2SfzyHLFZ1xYNqNjWWHJx9j49M43TPh49kRu6WmRLdLPesU22KYlJNImKs-jKd8rSV4-Z1XzUAfokuyLm3aYTZauIDQJSmxDIPrAQEwtWvWU5Q.png">
</b><b><img src="UudM90ng9cbOx-42AN7L81z9Lizrls57-43R28cxJicVXMolOFzGzXgW83JQlhIOiydKaxle93AHcHeqhU24gjMKXMK2s1xOKYcdbAZmz386NAQWjjutSm0ccfmmyRnAoRAT.png"></b>
</details>

<details>
<summary>
<b><div style="">What is ClusterIP in Kubernetes?</div></b>
</summary>
<div style="">Service type, which exposes the service on a cluster-internal IP address. Choosing this method makes the service reachable only from within the cluster.</div>
<b><img src="LrIJFiLam2cpkcf5myVNScFXQXKuDfEwd0xSotjkLa7jqoX8JfB7LoKGcD4iEw4qlhg24NI7Jm-3jL73NszW-cek7bmMVY2vyjjUyGTb-9hEjUO2ipOf7gaMbnekRZP6Bmr5.png">
</b><b><img src="5wuy9L_oMBJcBsPsIwmD59ILSh7-t3ZNBKfhVkLapEWie2EGwgVThhPvePn4mGV_7ZCHNX8rWU2lbtoVuUC1kP23qsXGxYg_Z1ByEveznrWNR0vuezgVZCZSL4HSvLgtMtbY.png"></b>
</details>

<details>
<summary>
<b><div style="">Describe Service type LoadBalancer&nbsp;</div></b>
</summary>
<div style="">LoadBalancer exposes the Service externally using a cloud provider’s load balancer</div>
<img src="QnnXx8MGILXDCYsLAdngTctLUdjhhzbX9PRWiUfDI2UhhBMhYiWU-0Ysi-sitiPhgLNqp6wBPXHl9AAjL76Ov6_GgikVnJojpvi1UL_2NCZ-REKjEa_5cE20ckCHOdv7zZ1x.png">
<img src="paste-b61642fa022fc52b5b490f29808fa0fa4061f4c7.jpg">
</details>

<details>
<summary>
<b><div style="">Describe Service type NodePort</div></b>
</summary>
<div style=""><div style="">NodePort exposes the Service on each Node’s IP at a static port (the NodePort). 
A ClusterIP Service, to which the NodePort Service routes, is automatically created.&nbsp;

<b><img src="rAgf9__TwBFmrVUEUQ8lTsqkCFom_JxHss_iNB8eeZYIBGOW_rbIx4fZCr2S-glINvZNXzsY5q4OrT5VsjO4YxcOIrvHQsesmXb9XUQKEa0tY0IC-gxj4xAbbH1l5hB8YPJ6.png">
</b><b><img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png"></b>
</div></div>
</details>

<details>
<summary>
<b><div style="">Which Kubernetes entity does this picture represent?</div>
<img src="paste-83b64e7181e7ef9182c3107e228e930f9a8beca3.jpg"></b>
</summary>
NodePort Service

<b><img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png"></b>
</details>

<details>
<summary>
<b><div style="">Which Kubernetes ServiceType does this picture represent?

<b><img src="8zMkWcUy-sQVvHu6EEgij-3E3MHgiG2OuGoKp6l88A2O-HQTo-OieuBw-5cjrmUAabVmjFYDkxoPxnccOBtwlR57iqlwtzW49febM9ghA480pvFdSILE7J1_zmJQi4qGyv__.png"></b>
</div></b>
</summary>
<b><div>ClusterIP</div></b>
<b><img src="3FVc5EVpg7WzzWdGMov51g7LWETGHx5-Kv0Qt1Ti0VRXgHCHFA3EV1AIknarjMZIBfULfE9-UGbwJZyXUoxu3qs-qN1dUd436c6KqZ_JkvtsfLbolO2QW27cFPyt6UbMkx7d.png">
</b><b><img src="qCzpNHNAC2mCuaACHwq4u69BN05-Hfpwk4nvK6cbVV7WoiJlq8ak4clCabIpdgv_T0kumUklOv-qEGnVXnS-Y3dOqrr_ohT6sGM-ge7p6veBNytk8JJLCMjXPnxxTTQZFdnm.png"></b>
</details>

<details>
<summary>
<b>When was container war was over?</b>
</summary>
By late 2017, the orchestration wars were over, and Kubernetes had won.&nbsp;
Ref:&nbsp;https://learning.oreilly.com/library/view/cloud-native-devops/9781492040750/ch01.html
</details>

<details>
<summary>
<b>What are all 10 tasks K8s can do</b>
</summary>
Automation
autoscaling
centralized logging
configuring networks
failover
installing security patches
load balancing
monitoring
running backup
upgrading servers<div></div>
</details>

<details>
<summary>
<b>What is kubernetes is not fit</b>
</summary>
* Database, it has state and replicas (in state)
</details>

<details>
<summary>
<b>kubernetes shell, ps1, log, data-stack-clic-shell</b>
</summary>
kube-ps1 -&nbsp;&nbsp;If you use the&nbsp;bash&nbsp;or&nbsp;zsh&nbsp;shells, there’s a little&nbsp;utility&nbsp;that will add the current Kubernetes context to your prompt.
<div>kube-shell -- provides a pop-up menu of possible completions for each command
</div><div>Click - A more sophisticated Kubernetes terminal experience is provided by&nbsp;Click.</div><div>kubed-sh --&nbsp;&nbsp;pull and run the necessary containers to execute JavaScript, Ruby, or Python programs on your current cluster.&nbsp;
</div><div>Stern -- log tool,&nbsp;Stern tails the logs from all Pods matching a regular expression (for example&nbsp;demo.*). If there are multiple containers within the Pod, Stern will show you log messages from each, prefixed by its name.&nbsp;
</div>
</details>

<details>
<summary>
<b>Resources allowed during exam</b>
</summary>
* https://kubernetes.io/docs/ and its subdomain<div>*&nbsp;https://github.com/kubernetes/</div><div>*&nbsp;https://kubernetes.io/blog/</div>
</details>

<details>
<summary>
<b>cloudnatived/demo:hello deployment spec</b>
</summary>
spec:
 &nbsp;containers:
 &nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello
 &nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;- containerPort: 8888
</details>

<details>
<summary>
<b>Image Pull Policy by kubernetes to node</b>
</summary>
* Always pull<div>* Never pull</div><div>* IfNotPresent pull (default)</div>
</details>

<details>
<summary>
<b>How to set environment variablein k8s?</b>
</summary>
containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
 &nbsp;env:
 &nbsp;- name: GREETING
 &nbsp;&nbsp;&nbsp;value: "Hello from the environment"
</details>

<details>
<summary>
<b>How to harden the security of the container?</b>
</summary>
<div>containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
<b> &nbsp;securityContext:
</b><strong>&nbsp; &nbsp;<font color="#ab1aff">readOnlyRootFilesystem: true</font></strong><b><font color="#ab1aff">
</font></b></div><div><strong>&nbsp; &nbsp;<i><font color="#ff5d83">runAsNonRoot: true</font></i></strong><b>
 &nbsp;&nbsp;&nbsp;runAsUser: 1000</b>
</div><div>&nbsp; &nbsp;# setuid&nbsp;mechanism can temporarily gain the privileges of the user that&nbsp;<em>owns</em>&nbsp;the binary<b>
</b></div><div>&nbsp; &nbsp;allowPrivilegeEscalation: false
</div><div>&nbsp; &nbsp;capabilities:&nbsp;</div><div>&nbsp; &nbsp; &nbsp;drop: ["all"]&nbsp;</div><div>&nbsp; &nbsp; &nbsp;drop: ["CHOWN", "NET_RAW", "SETPCAP"]&nbsp;</div><div>&nbsp; &nbsp; &nbsp;add: ["NET_ADMIN"]<strong>
</strong></div>
</details>

<details>
<summary>
<b>Volume - storage - emptyDir&nbsp; ephemeral</b>
</summary>
* emptyDir - This is a piece of ephemeral storage<div><div>
</div></div><div>
</div><div>apiVersion: v1
kind: Pod
...
spec:
 &nbsp;volumes:
 &nbsp;- name: cache-volume
 &nbsp;&nbsp;&nbsp;emptyDir: {}
 &nbsp;containers:
 &nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello
 &nbsp;&nbsp;&nbsp;volumeMounts:
 &nbsp;&nbsp;&nbsp;- mountPath: /cache
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: cache-volume
</div>
</details>

<details>
<summary>
<b>Container restart spec inside manifest - Restart Policies</b>
</summary>
apiVersion: v1
kind: Pod
...
spec:
 &nbsp;restartPolicy: OnFailure|Never|Always
</details>

<details>
<summary>
<b>What Are Labels?</b>
</summary>
* Labels are key/value pairs that are attached to objects, such as pods.
<div>* They don't imply semantics to the core-system</div>
</details>

<details>
<summary>
<b>If two pods required to be on same node, what to do?</b>
</summary>
If the two Pods absolutely must be colocated, put their containers in the same Pod.&nbsp;
</details>

<details>
<summary>
<b>Specify affinity that the&nbsp;server&nbsp;Pod is scheduled on the same node that is also running a Pod labeled&nbsp;cache</b>
</summary>
<div>----</div><div>spec:
</div> &nbsp;affinity:
 &nbsp;&nbsp;&nbsp;podAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;labelSelector:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: app
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["cache"]
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;topologyKey: kubernetes.io/hostname
</details>

<details>
<summary>
<b>Why not use pod affinities?</b>
</summary>
* Pod affinities restrict the scheduler’s freedom
*&nbsp;Trading off one application against another.&nbsp;
</details>

<details>
<summary>
<b>Why do you need&nbsp;Pod Controllers?</b>
</summary>
<div>If the container exits for some reason, you have to manually restart it.</div><div>
</div><div>There’s only one replica of your container and no way to load-balance traffic across multiple replicas if you ran them manually.</div><div>
</div><div>If you want highly available replicas, you have to decide which nodes to run them on, and take care of keeping the cluster balanced.</div><div>
</div><div>When you update the container, you have to take care of stopping each running image in turn, pulling the new image and restarting it.</div>
</details>

<details>
<summary>
<b>Horizontal Pod Autoscaler</b>
</summary>
A Horizontal Pod Autoscaler (HPA) watches a specified Deployment, constantly monitoring a given metric to see if it needs to scale the number of replicas up or down.
You can autoscale the Deployment based on this value: for example, you could create an HPA that targets 80% CPU utilization for the Pods. 

apiVersion: autoscaling/v2beta1
kind: HorizontalPodAutoscaler
metadata:
 &nbsp;name: demo-hpa
 &nbsp;namespace: default
spec:
 &nbsp;scaleTargetRef:
 &nbsp;&nbsp;&nbsp;apiVersion: extensions/v1beta1
 &nbsp;&nbsp;&nbsp;kind: Deployment
 &nbsp;&nbsp;&nbsp;name: demo
 &nbsp;minReplicas: 1
 &nbsp;maxReplicas: 10
 &nbsp;metrics:
 &nbsp;- type: Resource
 &nbsp;&nbsp;&nbsp;resource:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: cpu
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;targetAverageUtilization: 80
</details>

<details>
<summary>
<b>What is Custom resource in Kubernetes?</b>
</summary>
A&nbsp;<em>custom resource</em>&nbsp;is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation. It represents a customization of a particular Kubernetes installation. However, many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.
</details>

<details>
<summary>
<b>Building Your Own Kubernetes Tools, How to list all the pods in your cluster using go?</b>
</summary>
Operators and Custom Resource Definitions (CRDs)

...
podList, err := clientset.CoreV1().Pods("").List(metav1.ListOptions{})
if err != nil {
 &nbsp;&nbsp;&nbsp;log.Fatal(err)
}
fmt.Println("There are", len(podList.Items), "pods in the cluster:")
for _, i := range podList.Items {
 &nbsp;&nbsp;&nbsp;fmt.Println(i.ObjectMeta.Name)
}
...
</details>

<details>
<summary>
<b>Sample ingress routing?</b>
</summary>
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
 &nbsp;name: fanout-ingress
spec:
 &nbsp;rules:
 &nbsp;- http:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;paths:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- path: /hello
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;backend:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;serviceName: hello
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;servicePort: 80
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- path: /goodbye
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;backend:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;serviceName: goodbye
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;servicePort: 80
</details>

<details>
<summary>
<b>Ingress certificate configuration :: USING EXISTING TLS CERTIFICATES</b>
</summary>
apiVersion: v1
kind: Secret
type: kubernetes.io/tls
metadata:
 &nbsp;name: demo-tls-secret
data:
 &nbsp;tls.crt: LS0tLS1CRUdJTiBDRV...LS0tCg==
 &nbsp;tls.key: LS0tLS1CRUdJTiBSU0...LS0tCg==
</details>

<details>
<summary>
<b>Two ways to configure the pod for dynamic values (password, dns=names)</b>
</summary>
Pass values to the application via environment variables in the Pod spec. 

apiVersion: v1
kind: Pod
metadata:
 &nbsp;name: envar-demo
 &nbsp;labels:
 &nbsp;&nbsp;&nbsp;purpose: demonstrate-envars
spec:
 &nbsp;containers:
 &nbsp;- name: envar-demo-container
 &nbsp;&nbsp;&nbsp;image: gcr.io/google-samples/node-hello:1.0
 &nbsp;&nbsp;&nbsp;env:
 &nbsp;&nbsp;&nbsp;- name: DEMO_GREETING
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;value: "Hello from the environment"
 &nbsp;&nbsp;&nbsp;- name: DEMO_FAREWELL
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;value: "Such a sweet sorrow"

Store configuration data directly in Kubernetes, using the ConfigMap and Secret objects.
</details>

<details>
<summary>
<b>ConfigMaps</b>
</summary>
The ConfigMap is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod’s environment.
</details>

<details>
<summary>
<b>How to Inject configMaps into environment</b>
</summary>
deployment:
apiVersion: v1
kind: ConfigMap
metadata:
 &nbsp;name: demo-config
data:
 &nbsp;greeting: Hola
spec:
 &nbsp;containers:
 &nbsp;&nbsp;&nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello-config-env
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- containerPort: 8888
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;env:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name: GREETING
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valueFrom:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configMapKeyRef:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: demo-config
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key: greeting
</details>

<details>
<summary>
<b>How to Pass an environment variable to entrypoint? Where env varaible derived from configMaps</b>
</summary>
spec:
 &nbsp;containers:
 &nbsp;&nbsp;&nbsp;- name: demo
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello-config-args
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;args:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- "-greeting"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- "$(GREETING)"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- containerPort: 8888
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;env:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name: GREETING
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valueFrom:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configMapKeyRef:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: demo-config
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key: greeting
</details>

<details>
<summary>
<b>How to create Config Files from ConfigMaps - configmap.yaml?</b>
</summary>
<div><div>Looking at the&nbsp;volumes&nbsp;section,&nbsp;you can see that we create a Volume named&nbsp;demo-config-volume, from the existing&nbsp;demo-config&nbsp;ConfigMap.</div><div>In the container’s&nbsp;volumeMounts&nbsp;section,&nbsp;we mount this volume on the&nbsp;mountPath: /config/, select the key&nbsp;config, and write it to the path&nbsp;<em>demo.yaml</em>. The result of this will be that Kubernetes will create a file in the container at&nbsp;<em>/config/demo.yaml</em>, containing the&nbsp;demo-config&nbsp;data&nbsp;in YAML format:</div></div><div>
</div><div>
</div>--configmap.yaml

apiVersion: v1
kind: ConfigMap
metadata:
 &nbsp;name: demo-config
data:
 &nbsp;config: |
 &nbsp;&nbsp;&nbsp;greeting: Buongiorno
<div>
</div><div>--deployment.yaml

apiVersion: extensions/v1beta1
kind: Deployment
metadata:
 &nbsp;name: demo
spec:
 &nbsp;replicas: 1
 &nbsp;selector:
 &nbsp;&nbsp;&nbsp;matchLabels:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app: demo
 &nbsp;template:
 &nbsp;&nbsp;&nbsp;metadata:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;labels:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app: demo
 &nbsp;&nbsp;&nbsp;spec:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;containers:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name: &nbsp;demo
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: cloudnatived/demo:hello-config-file
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- containerPort: 8888
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;volumeMounts:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- mountPath: /config/
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: demo-config-volume
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;readOnly: true
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;volumes:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name: demo-config-volume
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;configMap:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: demo-config
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;items:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: config
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: demo.yaml
</div>
</details>

<details>
<summary>
<b>Updating Pods on a Config Change</b>
</summary>
<strong>checksum/config: {{ include (print $.Template.BasePath "/configmap.yaml") . | sha256sum }}</strong>
<div><strong>
</strong></div><div>Deployment template now includes a hash sum of the config settings, if these settings change, then so will the hash.&nbsp;</div><div>When we run&nbsp;pod-name upgrade, POD will detect that the Deployment spec has changed, and restart all the Pods.<strong>
</strong></div>
</details>

<details>
<summary>
<b>Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo</b>
</summary>
Edit standard pod YAML to add volumes with a <i>volumes.secret.secretName </i>value:<div>
</div><div><i>spec:</i></div><div><i>&nbsp; volumes:</i></div><div><i>&nbsp; - name: foo</i></div><div><i>&nbsp; &nbsp; secret:</i></div><div><i>&nbsp; &nbsp; &nbsp; secretName: mysecret2</i></div><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; volumeMounts:</i></div><div><i>&nbsp; &nbsp; - name: foo</i></div><div><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i></div>
</details>

<details>
<summary>
<b>OpenFaaS&nbsp;</b>
</summary>
Function as a service on Kubernetes
</details>

<details>
<summary>
<b>Endpoint</b>
</summary>
A k8s API object created for you when deploying a service.<div>
</div><div>Map to pods via selectors.</div>
</details>

<details>
<summary>
<b>Role</b>
</summary>
A role contains a set of permissions<div>
</div><div>Permissions are additivite (no "deny" rules)</div><div>
</div><div>Role (namespace)</div><div>ClusterRole (cluster)</div><div>
</div><div>rules:</div><div>&nbsp; &nbsp; - apiGroups: [""] # "" = core API group</div><div>&nbsp; &nbsp; &nbsp; resources: ["pods"]</div><div>&nbsp; &nbsp; &nbsp; verbs: ["get", "watch", "list"]</div>
</details>

<details>
<summary>
<b>What is a headless service?</b>
</summary>
Without a ClusterIP. Directly access pods without a proxy.
</details>

<details>
<summary>
<b>How would you improve Kubernetes security</b>
</summary>
<div>Log everything in prod</div><div>
</div><div>Alert and apply new CVE fixes</div><div>
</div><div>Use audit&nbsp;services (Sonobuoy)
</div><div>
</div><div><div>No access to nodes</div></div><div>
</div><div>No access to ETCD</div><div>
</div><div>Network segmentation</div><div>
</div><div>Resource quotas and policy rules&nbsp;</div><div>
</div><div>Secrets as volumes</div><div>
</div><div>Scan containers (Snyk, Aqua)
</div><div>
</div><div>Non-root containers</div><div>
</div><div>Read-only filesystems on containers</div><div>
</div><div>Disallow sudo</div><div>
</div><div>Use kata containers&nbsp;
</div><div>
</div><div><div>gVisor</div><div>AppArmor (lockbox)</div><div>seccomp (lockbox)</div><div>SELinux</div></div>
</details>

<details>
<summary>
<b>What is a Job? What are all the fields to control them?</b>
</summary>
A Pod ran a specific number of completions or schedules&nbsp;<div>
</div><div>with or without parallelism.<div>
<div>spec:
</div><div><div> &nbsp;completions: 1
 &nbsp;parallelism: 10
 &nbsp;template:
 &nbsp;&nbsp;&nbsp;metadata:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: queue-worker
 &nbsp;&nbsp;&nbsp;spec:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;containers:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...

spec:
 &nbsp;schedule: "*/1 * * * *"
 &nbsp;jobTemplate:
 &nbsp;&nbsp;&nbsp;spec:</div><div>&nbsp; &nbsp; &nbsp;containers:
&nbsp; &nbsp; &nbsp; ...
</div></div></div></div>
</details>

<details>
<summary>
<b>What is ingress?</b>
</summary>
An API object that manages external access to the services in a cluster, typically HTTP.

Ingress can provide load balancing, SSL termination and name-based virtual hosting.

Ingress as a load balancer that sits in front of a Service
Ingress --&gt; Service =&gt; PODs^*
</details>

<details>
<summary>
<b>What are taints and&nbsp;<strong>tolerations</strong>?</b>
</summary>
<em>Taints</em>&nbsp;allow a node to repel a set of Pods, based on certain properties of the node.
</details>

<details>
<summary>
<b>LoadBalancer Service</b>
</summary>
<div>L4</div><div>
</div><div>Creates an external IP address</div><div>
</div><div>Only knows node IPs, not pods IPs. It chooses a node to send a packet to.</div><div>
</div><div>iptables in the node tells the packet where to actually go.</div><div>
</div><div>OnlyLocal annotation removes the double-hop problem by allowing users to define their own balancing.</div>
</details>

<details>
<summary>
<b>Service</b>
</summary>
A group of endpoints (usually pods)<div>
</div><div>Provides stable Virtual IP address which automatically routes to backend pods.</div><div>
</div><div>Clients only need the Virtual IP to connect to, which doesn't change.</div>
</details>

<details>
<summary>
<b>Conditions</b>
</summary>
Latest variable observations of an object's state.

Ready, ContainerReady, lastProbeTime, reason
</font><div><span style="color: rgb(36, 41, 46);">
</span></div><div><span style="color: rgb(36, 41, 46);">Used when the details of an observation are not known apriori known or would not apply to all instances of a given Kind.&nbsp;</span></div></div>
</details>

<details>
<summary>
<b>Flat network space</b>
</summary>
Pods MUST be reachable across Nodes<div>
</div><div>via L2, L3 or overlay</div><div>
</div><div>Each node has a CIDR IP block to give its pods unique IPs.</div>
</details>

<details>
<summary>
<b>Kube DNS</b>
</summary>
<div>Autoscalable deployment with a static virtual IP.</div><div>
</div><div>Servers "A" and "SRV" records to access services and pods</div>
</details>

<details>
<summary>
<b>kube-scheduler</b>
</summary>
Schedules pods on available worker nodes.<div>
</div><div><div>Policy-rich</div><div>Topology-aware,&nbsp;</div><div>Improves impacts availability, performance, and capacity of nodes</div><div>
</div><div>Considers individual / collective resource needs, QoS requirements, hardware/software/policy/affinity constraints, data locality, inter-workload interference, deadlines.</div></div>
</details>

<details>
<summary>
<b>Restart a pod</b>
</summary>
<div><div>kubectl&nbsp;get&nbsp;pod&nbsp;PODNAME&nbsp;-n&nbsp;NAMESPACE&nbsp;-o&nbsp;yaml&nbsp;|&nbsp;kubectl&nbsp;replace&nbsp;--force&nbsp;-f&nbsp;-</div></div>
</details>

<details>
<summary>
<b>Convert the "nginx" ClusterIP service to NodePort and find the NodePort port. Hit it using Node's IP.</b>
</summary>
<i>kubectl edit svc nginx</i>
change the <i>spec.type </i>value to NodePort
<i>spec:</i><div><i>&nbsp; type: NodePort</i>
Find the port and IP with
<i>kubectl get svc</i>
then hit the service with
<i>wget -O- &lt;NodeIP&gt;:&lt;Port&gt;</i></div>
</details>

<details>
<summary>
<b><div style="">List 3 components that every Kubernetes Node has</div></b>
</summary>
<div style="">1. <b>kubelet</b>, a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
2. <b>kube-proxy</b>, a proxy that maintains network rules on nodes.</div>3.&nbsp;<div style="display: inline !important;"><b>container runtime </b>(like Docker) responsible for pulling the container image from a registry, unpacking the container, and running the application.
</div>
<img src="paste-0d78f3f9993df127ff9365555478608a03a8904f.jpg">
</details>

<details>
<summary>
<b>What is a node pool?</b>
</summary>
<b>A group of nodes within a cluster that all have the same configuration</b>

<img src="paste-3d68d8e58746cbf4aed5beb32f7857fc7601156f.jpg">
<img src="paste-75313fe7c14867e5f60723d98b3f6c0f00afb66a.jpg">
</details>

<details>
<summary>
<b>How many master nodes does a Kubernetes cluster contain (assuming no high availability features)?</b>
</summary>
1

<img src="paste-331274bc09622c2e5c6b92c3e36981ae6931f602.jpg">
</details>

<details>
<summary>
<b>To list your busiest nodes, by the number of Pods running on each:</b>
</summary>
kubectl get pods -o json --all-namespaces | 
jq '.items | group_by(.spec.nodeName) | 
map({"nodeName": .[0].spec.nodeName, "count": length}) | 
sort_by(.count) | 
reverse'
</details>

<details>
<summary>
<b>Add AntiAffinity such that Pod will&nbsp;<em>not</em>&nbsp;be scheduled on any node matching this rule.</b>
</summary>
affinity:
 &nbsp;&nbsp;&nbsp;podAntiAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;labelSelector:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: app
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["server"]
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;topologyKey: kubernetes.io/hostname
</details>

<details>
<summary>
<b>How to add/remove taint to a node?</b>
</summary>
<strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule</strong><div><strong>kubectl taint nodes docker-for-desktop dedicated=true:NoSchedule-
</strong><b>
</b>apiVersion: v1
kind: Pod
...
spec:
 &nbsp;tolerations:
 &nbsp;- key: "dedicated"
 &nbsp;&nbsp;&nbsp;operator: "Equal"
 &nbsp;&nbsp;&nbsp;value: "true"
 &nbsp;&nbsp;&nbsp;effect: "NoSchedule"<b>
</b><div><strong>
</strong></div></div>
</details>

<details>
<summary>
<b>Kubernetes runs your workload by placing containers into Pods to run on...</b>
</summary>
Nodes
</details>

<details>
<summary>
<b>Are nodes virtual machines?</b>
</summary>
Not always<div>
</div><div>They can be physical machines</div>
</details>

<details>
<summary>
<b>When a node self-registers to the control plane, which component is responsible?</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>To prevent a node from self-registering on the control-plane, you could...</b>
</summary>
<div>Pass this flag to the kubelet:</div><div><b>--register-node=false</b>
</div>
</details>

<details>
<summary>
<b>kubectl cordon NODE</b>
</summary>
Mark a node unschedulable
</details>

<details>
<summary>
<b>kubectl drain NODE</b>
</summary>
Cordons the node then evicts/deletes all pods.<div>
</div><div>Does not deleted mirror pods or DaemonSet pods (DS controller ignores unschedulable markings)</div><div>
</div><div><b>--ignore-daemonsets</b></div><div>Ignore DS managed pods</div><div>
</div><div><b>--force</b></div><div>Continue even if there are dangling pods</div><div>
</div><div><b>--delete-local-data</b></div><div>Continue even if there are pods with <b>EmptyDir</b>&nbsp;(local data that is removed upon draining)</div>
</details>

<details>
<summary>
<b>kubectl taint (?)</b>
</summary>
<div>kubectl taint NODE KEY=VAL:EFFECT</div><div>
</div><div><b>--overwrite</b></div>
</details>

<details>
<summary>
<b>todo</b>
</summary>
<div>Sent by kubelets, help determine the availability of a node.&nbsp;</div><div>
</div><div>1) updates of&nbsp;<code>NodeStatus</code>&nbsp;</div><div>2)&nbsp;<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#lease-v1-coordination-k8s-io">Lease object</a>.&nbsp;</div><div>
</div><div>Each Node has an associated Lease object in the&nbsp;<code>kube-node-lease</code>&nbsp;<a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces">namespace</a>&nbsp;which improves the performance of the node heartbeats as the cluster scales.</div>
</details>

<details>
<summary>
<b>What is Node Affinities?&nbsp;</b>
</summary>
<div>Schedule pods on selector'd nodes preferentially or not</div><div>
</div><div><b>requiredDuringSchedulingIgnoredDuringExecution</b></div><div><b>preferredDuringSchedulingIgnoredDuringExecution</b>&nbsp;</div><div>
<b>spec:
 &nbsp;affinity:
 &nbsp;&nbsp;&nbsp;nodeAffinity:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;requiredDuringSchedulingIgnoredDuringExecution:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nodeSelectorTerms:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- matchExpressions:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- key: "failure-domain.beta.kubernetes.io/zone"
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;operator: In
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values: ["us-central1-a"]</b>
</div>
</details>

<details>
<summary>
<b>Worker node components</b>
</summary>
<b>kubelet</b><div>Controls node, provides api for control plane</div><div>
</div><div><b>kube-proxy</b></div><div>Configs iptables and virtual network</div><div>
</div><div><b>Container runtime</b></div><div>Downloads and runs containers
</div>
</details>

<details>
<summary>
<b>kubectl uncordon</b>
</summary>
Mark a node schedulable
</details>

<details>
<summary>
<b>kubectl top node NODE_NAME</b>
</summary>
Display resource usage of nodes
</details>

<details>
<summary>
<b>Control plane components</b>
</summary>
<div>Kubernetes Master&nbsp;
</div><div>kubelets<div><div>etcd</div></div></div>
</details>

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

<details>
<summary>
<b>StatefulSets</b>
</summary>
*&nbsp;Ability to start and stop Pods in a specific sequence.
* Manages disk storage for their Pods, using a VolumeClaimTemplate object that automatically creates a PersistentVolumeClaim<div>* Each&nbsp;replica in a StatefulSet must be running and ready before Kubernetes starts the&nbsp;next one, and similarly when the StatefulSet is terminated, the replicas will be shut down in reverse order, waiting for each Pod to finish before moving on to the next.

</div>
</details>

<details>
<summary>
<b><div>StatefulSet is the workload API object used to manage _____</div></b>
</summary>
stateful applications
</details>

<details>
<summary>
<b>StatefulSet manages the deployment and scaling of a set of Pods,&nbsp;and provides guarantees about _____&nbsp;of these Pods</b>
</summary>
the ordering and uniqueness
</details>

<details>
<summary>
<b>Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a _____ for each of their Pods</b>
</summary>
sticky identity
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSet pods are created from the same spec, but are _____</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Each has a persistent identifier that it maintains across any rescheduling.</span></div></b>
</summary>
<span style="color: rgb(34, 34, 34);">interchangeable</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If you want to use <b>storage volumes</b> to provide persistence for your workload, you can use a _____ as part of the solution. Although individual Pods in a _____ are susceptible to failure, the persistent <b>Pod identifiers</b> make it easier to <b>match existing volumes</b> to the new Pods that replace any that have failed.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">StatefulSet&nbsp;</span>
</details>

<details>
<summary>
<b>An application requires several of the following:<div><ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul><div>Which workload object could work best?</div></div></b>
</summary>
StatefulSet
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Deleting and/or scaling a StatefulSet down will </span><i>_____</i><span style="color: rgb(34, 34, 34);">&nbsp;the volumes associated with the StatefulSet.</span></b>
</summary>
<em>not</em><span style="color: rgb(34, 34, 34);">&nbsp;delete</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSets currently require a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods. You are responsible for creating it.</span></b>
</summary>
<a href="https://kubernetes.io/docs/concepts/services-networking/service/#headless-services">Headless Service</a>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></div></b>
</summary>
<span style="color: rgb(34, 34, 34);">scale the StatefulSet down to 0 prior to deletion</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When using&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#rolling-updates">Rolling Updates</a><span style="color: rgb(34, 34, 34);">&nbsp;with the default&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#pod-management-policies">Pod Management Policy</a><span style="color: rgb(34, 34, 34);">&nbsp;(</span><code>OrderedReady</code><span style="color: rgb(34, 34, 34);">), it's possible to get into a broken state that requires _____&nbsp;to repair</span></b>
</summary>
<a href="https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#forced-rollback">manual intervention</a>
</details>

<details>
<summary>
<b>StatefulSet syntax</b>
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

<details>
<summary>
<b>what is rolling deployment?</b>
</summary>
approach when you deploy your containers to production hosts one at a time, so your app keeps running.Centurion can do this
</details>

<details>
<summary>
<b><span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600;">You just deployed an application on Kubenetes Engine and would like to verify that its deployment is operational.&nbsp; What command could you use?</span></b>
</summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px;">kubectl get service app</span>
</details>

<details>
<summary>
<b><span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600; background-color: rgb(242, 243, 245);">You just rolled out a new Kubenetes deployment. After the rollout completes you want to view the deployment. What is the command to list the deployments?</span></b>
</summary>
kubectl get deployments
</details>

<details>
<summary>
<b>Create a deployment called foo using image 'dgkanatsios/simpleapp' (a simple server that returns hostname) and 3 replicas. Label it as 'app=foo'. Declare that containers in this pod will accept traffic on port 8080 (do NOT create a service yet)</b>
</summary>
Don't use the <i>--expose </i>flag, so we don't create a service.
Leaving out the <i>--restart </i>flag creates a deployment.
<i>kubectl run foo --image=dgkanatsios/simpleapp --labels=app=foo --port=8080 --replicas=3</i>
</details>

<details>
<summary>
<b>Get the IPs of the "foo" deployment. Create a temp busybox pod and try hitting them on port 8080</b>
</summary>
Getting pods with <i>-o wide</i>&nbsp;will show IPs:
<i>kubectl get pods -l app=foo -o wide</i><div><i>
</i></div><div>Start an interactive session to use wget:</div><div><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh

</i></div><div><i>wget -O- &lt;PodIP&gt;:8080</i></div><div><i>exit</i></div>
</details>

<details>
<summary>
<b>Create a service that exposes the "foo" deployment on port 6262. Verify its existence, check the endpoints</b>
</summary>
<i>kubectl expose deploy foo --port=6262 --target-port=8080</i><div><i>kubectl get service foo</i></div><div><i>kubectl get endpoints foo</i></div>
</details>

<details>
<summary>
<b>Create an nginx deployment of 2 replicas, expose it via a ClusterIP service on port 80. Create a NetworkPolicy so that only pods with labels 'access: true' can access the deployment and apply it</b>
</summary>
<i>kubectl run nginx --image=nginx --replicas=2 --port=80 --expose</i>
Check the label selector the service uses for the pods with
<i>kubectl describe svc nginx</i><div><i>
</i><div>Create a NetworkPolicy YAML with <i>spec.podSelector.matchLabels </i>to assign the policy to the right pods, and <i>ingress.from.podSelector.matchLabels </i>to restrict which pods can access it.

<i>spec:</i></div><div><i>&nbsp; podSelector:</i></div><div><i>&nbsp; &nbsp; matchLabels:</i></div><div><i>&nbsp; &nbsp; &nbsp; run: nginx</i></div><div><i>&nbsp; ingress:</i></div><div><i>&nbsp; - from:</i></div><div><i>&nbsp; &nbsp; - podSelector:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; matchLabels:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; access: 'true'
</i>
(note we need to put quotes around true so it is accepted as a string rather than a bool)
Apply the policy with
<i>kubectl apply -f policy.yaml</i></div></div>
</details>

<details>
<summary>
<b>Command to update a Kubernetes deployment that was created with the `kubectl create` command.</b>
</summary>
`kubectl apply`
</details>

<details>
<summary>
<b>The command to list Kubernetes deployments.</b>
</summary>
`kubectl get deployments`
</details>

<details>
<summary>
<b><div style="">Provide command to list all Kubernetes deployments in the namespace</div></b>
</summary>
kubectl get deployments

<b><img src="YBEIFyh1TJpMc6vPYvSIj1qYC7tpnKnbKwBu0fC0q2uCaJ7Y_676eSkGUtFlIArUQEnv31_SpyTi-zY3-DbxXHKF82naqWuJrc9AaCYds1muVXWZkTSm755qgZ514rM8eT6c.png"></b>
</details>

<details>
<summary>
<b>In terms of functionality, which Kubernetes entity is more complex - Deployment or ReplicaSet?</b>
</summary>
<b>Deployment</b>

<b><img src="SE2xr9beiMR_1xUeEEqR5-Omfbt9BpnFnB7xURtkppxc_JnYNuG3zVqaszIsu6N-LTutLcvzSM68ZH9nxUBsRXikgTKQHyoB0241XQsV-CP_tv3KY-CK38WQT6Lufkcycf5T.png"></b>
</details>

<details>
<summary>
<b>How to compare with Kubernetes live with manifest configuration</b>
</summary>
kubectl diff&nbsp;(see&nbsp;“Diffing Resources”)
<div>kubectl diff -f deployment.yaml

&gt;&gt; - replicas: 10 
&lt;&lt; + replicas: 5
</div>
</details>

<details>
<summary>
<b>Running busybox Containers for Troubleshooting</b>
</summary>
kubctl run demo --image cloudnatived/demo:hello --expose --port 8888<div>service "demo" created 
deployment.apps "demo" created

kubectl run nslookup --image=busybox:1.28 --rm -it --restart=Never \ --command -- nslookup demo&nbsp;</div><div>Server: 10.79.240.10 Address 1: 10.79.240.10 kube-dns.kube-system.svc.cluster.local&nbsp;</div><div>Name: demo Address 1: 10.79.242.119 demo.default.svc.cluster.local</div><div>
</div><div>
<div>kubectl run wget --image=busybox:1.28 --rm -it --restart=Never --command -- wget -qO- http://demo:8888
</div></div>
</details>

<details>
<summary>
<b>What is&nbsp;Deployments?</b>
</summary>
* Supervisor program, which continually checks that the container is running, and if it ever stops, starts it again immediately.<div>* On traditional servers, you can use a tool like&nbsp;systemd,&nbsp;runit, or&nbsp;supervisord&nbsp;to do this; On Kubernetes, it is Deployment
* Kubernetes&nbsp;creates a corresponding Deployment object for each pods</div><div>&nbsp; * Deployment records some information about the program:&nbsp;</div><div>&nbsp; * Name of the container image</div><div>&nbsp; *&nbsp;The number of replicas you want to run</div><div>&nbsp; * Whatever else it needs to know to start the container.</div>
</details>

<details>
<summary>
<b>Deployment, Controller with replicaset</b>
</summary>
* Deployment doesn’t manage replicas directly: instead, it automatically creates an associated object called a ReplicaSet, which handles that. We’ll talk more about ReplicaSets in a moment in&nbsp;“ReplicaSets”
* Working together with the&nbsp;Deployment resource is a kind of&nbsp;Kubernetes object called a&nbsp;<em>controller</em>. Controllers watch the resources they’re responsible for, making sure they’re present and working. If a given Deployment isn’t running enough replicas, for whatever reason, the controller will create some new ones.
</details>

<details>
<summary>
<b>kubectl rollout pause</b>
</summary>
<div>Mark the provided <b>deployment</b> as paused, not to be reconciled by a controller.&nbsp;</div><div>
</div><div><b>kubectl rollout resume&nbsp;</b></div>
</details>

<details>
<summary>
<b>kubectl scale</b>
</summary>
<div>Set a new size for a Deployment, ReplicaSet, Replication Controller, or StatefulSet.</div><div>
</div><div>Allows one or more preconditions for the scale action.</div><div>
</div><div>If --current-replicas or --resource-version is specified, it is validated before the scale is attempted, and it is guaranteed that the precondition holds true when the scale is sent to the server.</div><div>
</div><div>--replicas=N</div><div>
</div><div>--timeout=Ns</div><div>Time to wait before giving up on a scaling (0 - don't wait)</div>
</details>

<details>
<summary>
<b>kubectl set env</b>
</summary>
<div>kubectl set env deployment/sample-build foo-bar
</div><div>
</div><div>kubectl set env deployment/sample-build --list</div>
</details>

<details>
<summary>
<b>deployment.spec.replicas</b>
</summary>
Numer of desired pods
</details>

<details>
<summary>
<b>deployment.spec.revisionHistoryLimit</b>
</summary>
Number of old ReplicaSets to retain for rollback
</details>

<details>
<summary>
<b>deployment.spec.selector</b>
</summary>
Label selector for pods<div>
</div><div>Must match pod template labels</div>
</details>

<details>
<summary>
<b>deployment.spec.strategy</b>
</summary>
<b>Recreate</b><div><b>
</b></div><div><b>RollingUpdate</b></div><div>maxSurge: max number / percentage of pods that can be scheduled above the desired number of pods</div><div>
</div><div>maxUnavailable: max number of pods that can be unavailable during the update</div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></b>
</summary>
<b>Deployment </b>or<b> Replicaset</b>&nbsp;<div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">a workload object that provides a set of stateless replicas.</span></div>
</details>

<details>
<summary>
<b>Export a running deployment to a file</b>
</summary>
kubectl get deploy nginx -o yaml --export > deployment.yaml
</details>

<details>
<summary>
<b>Check how the nginx deployment rollout is going</b>
</summary>
<i>kubectl rollout status deploy nginx</i>
</details>

<details>
<summary>
<b>Check the rollout history for the nginx deployment</b>
</summary>
<i>kubectl rollout history deploy nginx</i>
</details>

<details>
<summary>
<b>Pause the rollout of the nginx deployment</b>
</summary>
<i>kubectl rollout pause deploy nginx</i>
</details>

<details>
<summary>
<b>Update the image of the nginx deployment to 1.7.9</b>
</summary>
<i>kubectl set image deploy nginx nginx=nginx:1.7.9</i>
or
<i>kubectl edit deploy nginx&nbsp;</i>
and change the image field in YAML

Kubectl set image command is
<i>kubectl set image &lt;type&gt; &lt;name&gt; &lt;container_name&gt;=&lt;container_image&gt;</i>
</details>

<details>
<summary>
<b>The name of the Kubernetes Deployment that ensures a single instance of a pod will run on each node.</b>
</summary>
DaemonSet
</details>

<details>
<summary>
<b>What is a DaemonSet?</b>
</summary>
A Kubernetes <b>Controller </b>which ensures that all (or some) <b>Nodes run a copy of a Pod.</b>

<img src="paste-b232887ca039d4beaf429a411e14fa6b3a83a025.jpg">
<img src="paste-29aacf46a4806c2486da42a774bf5401c35eea64.jpg"><img src="paste-1542ce24313150291f3adf83860cdf110447b2b4.jpg">
</details>

<details>
<summary>
<b>To which entity is this description reffering to?

A Kubernetes&nbsp;<b>Controller&nbsp;</b>which ensures that all (or some)&nbsp;<b>Nodes run a copy of a Pod&nbsp;</b>- thus allowing for node management.</b>
</summary>
DaemonSet

<img src="paste-71933616ad20fe752807b7c64a8363b0d177838e.jpg">
</details>

<details>
<summary>
<b><div style="">Explain what DaemonSet and ReplicaSet have in common (and what are the differences)</div></b>
</summary>
They are both Kubernetes Controllers and they are both related to count of pods inside the cluster.
<div style=""><b>
ReplicaSet </b>makes sure that given amount of pods is always running in the cluster (<b>doesn't</b> matter in which worker node they are running!)</div><img src="paste-3dfda59e415fbe71f6a599a82a877ec60953f322.jpg">

<div style="display: inline !important;"><b>DaemonSet </b>makes sure that all (or selected) nodes have a replica of given pod.
In most use cases, the number of nodes will be equal with number of pods</div><img src="paste-41a44af9a7651900a5b65dbf3ba95a1f3fa4eb3e.jpg">
</details>

<details>
<summary>
<b>Is it possible to run DaemonSet pods on only some nodes?</b>
</summary>
Yes

<b><img src="Un0li2eM8tO5MluxUrOgz4f-HxqGAd7jPcOB0aYy5mQTAWdnwWsmTWB0wSmXujU2BogyAsx2jGev2j22rlmGALI4gWLo61sHMSDy5RYheY152ANPTbCgNfLUE4OPkcJWm0ZJ.png"></b>
</details>

<details>
<summary>
<b><div style="">What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</div></b>
</summary>
<div style="">These pods will be garbage collected (deleted) as well</div><b><img src="lFn2VhS56EQ5e5HzPHY0ouWasNdxi6-R2XEOtnqIpKDTocCA4l-Sg6AfbKXHH9WIS1a8EMnYYEOiGyGJFioK-9qIZIH3sduMAborO6gXiCHw1Umz7OniapkRpRZdEZfQbEXv.png"></b>
</details>

<details>
<summary>
<b><em>what is DaemonSet</em></b>
</summary>
* It runs one instance on *NODE*
* Kubernetes DaemonSets run a&nbsp;<em>daemon</em>&nbsp;container on each node in the cluster.
<div>* The term&nbsp;<em>daemon</em>&nbsp;traditionally refers to long-running background processes on a server that handle things like logging, so by analogy,&nbsp;</div>
</details>

<details>
<summary>
<b>A node's status containts four domains of information.<div>These are...</div></b>
</summary>
Addresses<div>
</div><div>Conditions</div><div>
</div><div>Capacity and Allocatable</div><div>
</div><div>Info</div>
</details>

<details>
<summary>
<b>kubectl command to view a Node's status and other details</b>
</summary>
<b>kubectl describe node &lt;node-name&gt;</b>
</details>

<details>
<summary>
<b>The usage of the "Addresses" status fields depends on...</b>
</summary>
your cloud provider or bare metal configuration
</details>

<details>
<summary>
<b>Addresses in a node's status include...</b>
</summary>
<div>ExternalIP
</div><div>
</div><div>InternalIP</div><div>
</div><div>HostName
</div>
</details>

<details>
<summary>
<b>HostName</b>
</summary>
The hostname reported by the node's kernel<div>
</div><div>Can be overridden via <b>--hostname-override</b></div>
</details>

<details>
<summary>
<b>ExternalIP</b>
</summary>
The IP address of the node available from outside the cluster
</details>

<details>
<summary>
<b>InternalIP</b>
</summary>
The IP address of the node routable only from inside the cluster
</details>

<details>
<summary>
<b>Node <b>Info</b>&nbsp;status field describes general information about a node, such as:</b>
</summary>
OS Name<div>
</div><div>kubelet, kube-proxy, docker versions</div>
</details>

<details>
<summary>
<b>Ready</b>
</summary>
<b>True</b><div>if the node is healthy and ready to accept pods</div><div><b>
</b></div><div><b>False</b></div><div>if the node us unhealthy and is not accepting pods</div><div><b>
</b></div><div><b>Unknown</b></div><div>If the node controller has not heard from the node in the last 40 seconds</div>
</details>

<details>
<summary>
<b>DiskPressure</b>
</summary>
<b>True</b><div>if the node's disk capacity is low</div>
</details>

<details>
<summary>
<b>MemoryPressure</b>
</summary>
<b>True</b><div>if the node's memory is low</div>
</details>

<details>
<summary>
<b>PIDPressure</b>
</summary>
<b>True</b>&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
<b>PIDPressure</b>
</summary>
<b>True</b>&nbsp;if there are too many processes on the node
</details>

<details>
<summary>
<b>NetworkUnavailable</b>
</summary>
<b>True</b>&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
<b>NetworkUnavailable</b>
</summary>
<b>True</b>&nbsp;if the network for the node is not correctly configured
</details>

<details>
<summary>
<b>A node is reachable by the <b>API server </b>but its&nbsp;<b>Ready</b> condition has remained&nbsp;<b>False</b> or <b>Unknown</b> for longer than the <b>kube-controller-manager</b>'s&nbsp;<b>pod-eviction-timeout</b><div>
</div><div>What happens to the Pods on the node?</div></b>
</summary>
All Pods on the node are scheduled for deletion by the node controller
</details>

<details>
<summary>
<b>Capacity</b>
</summary>
<div>Capacity fields describe the total amount of resources that a Node has</div>
</details>

<details>
<summary>
<b>Allocatable</b>
</summary>
Describes the amount of the Node's resources that are available to be consumed by Pods
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
Kubernetes control plane component that manages various aspects of nodes
</details>

<details>
<summary>
<b>The three roles of the <b>Node Controller </b>in a Node's life</b>
</summary>
<div><b>CIDR block assignment</b>
</div><div>Assigns a CIDR block to each node upon registration (if enabled)</div><div><hr></div><div><b>List of nodes</b></div><div>Synchronizes the Node Controller's internal list of nodes with the <b>cloud provider</b>'s list of available machines</div><div><hr></div><div><b>Node health monitoring</b></div><div>Manages a node's&nbsp;<b>Ready</b>&nbsp;condition depending on reachability. Evicts the node's pods if it remains unreachable</div>
</details>

<details>
<summary>
<b>Node heartbeats are sent by...</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>Node heartbeats are sent by...</b>
</summary>
kubelet
</details>

<details>
<summary>
<b>kubectl rollout&nbsp;</b>
</summary>
<div>Manage the rollout of</div><ul><li>deployments</li><li>daemonsets</li><li>statefulsets</li></ul>
</details>

<details>
<summary>
<b>kubectl rollout history</b>
</summary>
<div>View previous rollout revisions and configurations.</div><div>
</div><div>--version</div><div><span style="color: rgb(51, 51, 51); background-color: rgb(176, 196, 222);">See the details, including podTemplate of the revision specified</span>
</div>
</details>

<details>
<summary>
<b>kubectl rollout restart</b>
</summary>
<div>Restart a resource.</div>
</details>

<details>
<summary>
<b>kubectl rollout status</b>
</summary>
<div>Show the status of the rollout.</div><div>
</div><div>By default 'rollout status' will watch the status of the latest rollout until it's done. (<b>--watch=true</b>)</div><div>
</div><div>Note that if a new rollout starts in-between, then 'rollout status' will continue watching the latest revision.&nbsp;</div><div>
</div><div>If you want to pin to a specific revision and abort if it is rolled over by another revision, use <b>--revision=N</b></div>
</details>

<details>
<summary>
<b>kubectl rollout undo [TYPE NAME]</b>
</summary>
Rollback to a previous rollout revision
<div>
</div><div><b>--to-revision=N</b></div>
</details>

<details>
<summary>
<b>kubectl set image</b>
</summary>
<div>Update existing container image(s) of:</div><div>
</div><div><div>pod (po), replicationcontroller (rc), deployment (deploy), daemonset (ds), replicaset (rs)</div></div><div>
</div><div>kubectl set image deployment/nginx busybox=busybox nginx=nginx:1.9.1
</div><div>
</div><div>
</div>
</details>

<details>
<summary>
<b>Two types of node Heartbeats</b>
</summary>
1. updates of <b>NodeStatus</b><div>
2. The <b>Lease Object</b></div>
</details>

<details>
<summary>
<b>CAdvisor</b>
</summary>
A daemon in the kubelet that discovers, monitors and exports data on containers
</details>

<details>
<summary>
<b>All API usage from nodes and pods terminate at the following control plane components:</b>
</summary>
<b>apiserver</b><div><div><hr><div>no other control plane components exposes remote services</div></div></div>
</details>

<details>
<summary>
<b>Nodes should be provisioned with _____ for the cluster such that they can connect securely to the apiserver along with valid client credentials</b>
</summary>
public root certificate
</details>

<details>
<summary>
<b>Pods that wish to securely connect to the apiserver can leverage a _____ so that K8S will automatically inject the public root certificate and valid bearer token into the new pod.</b>
</summary>
service account
</details>

<details>
<summary>
<b>The <b>kubernetes </b>service (in all namespaces) is configured with _____ that is redirected via _____ to the apiserver</b>
</summary>
a virtual IP address<div>
</div><div>kube-proxy</div>
</details>

<details>
<summary>
<b>the apiserver is configured to listen for remote connections on _____ with one or more forms of _____ enabled</b>
</summary>
a secure HTTPS port<div>
</div><div>client authentication</div>
</details>

<details>
<summary>
<b><div>apiserver to kubelet connections are used for</div></b>
</summary>
Fetching pod logs<div>
</div><div><b>kubectl attach</b>'ing into pods</div><div>
</div><div><b>kubectl port-forward</b>'ing into pods</div>
</details>

<details>
<summary>
<b>apiserver to kubelet connections terminate at</b>
</summary>
the kubelet's HTTPS endpoint
</details>

<details>
<summary>
<b>Does the <b>apiserver</b> verify the <b>kubelet's</b> serving certificate by default?</b>
</summary>
No<div>-----</div><div>The connection is subject to MITM attacks by default</div>
</details>

<details>
<summary>
<b>apiserver to kubelet connection can be verified via</b>
</summary>
<div>SSH tunneling</div><div>
</div><div>OR&nbsp;</div><div>
</div><b>apiserver --kubelet-certificate-authority</b>
</details>

<details>
<summary>
<b>Are <b>apiserver</b>&nbsp;connections to <b>nodes, pods and services</b>&nbsp;authenticated or encrypted?</b>
</summary>
No :(<div>
</div><div>They can be run over HTTPS but will not validate the certificate</div>
</details>

<details>
<summary>
<b>By decoupling the interoperability logic between Kubernetes and the underlying cloud infrastructure, _____ enables cloud providers to release features at a different pace compared to the main Kubernetes project.</b>
</summary>
cloud-controller-manager
</details>

<details>
<summary>
<b>Node controller</b>
</summary>
<b>Create / destroy nodes&nbsp;</b><div>when new servers are created and destroyed in your cloud infrastructure</div><div>
</div><div><b>Annotate Nodes</b></div><div>with cloud-specific information, such as Region</div><div>
</div><div><b>Get Node information</b></div><div>Hostname, address, health</div>
</details>

<details>
<summary>
<b>Route controller</b>
</summary>
Configures addresses and routes between K8S nodes in your cloud
</details>

<details>
<summary>
<b>Service Controller</b>
</summary>
Sets up Load Balancers and other infrastructure components needed by <b>Service </b>k8s objects
</details>

<details>
<summary>
<b>cloud-controller-manager runs the following controllers:</b>
</summary>
<div>Node Controller
</div><div>Route Controller</div><div>Volume Controller</div><div>Service Controller</div>
</details>

<details>
<summary>
<b><div>What’s a <b>Pod</b></div></b>
</summary>
<div>A&nbsp;<b>Pod </b>is a group of one or more&nbsp;containers with shared storage/network, and a specification for how to run the containers.

<b><img src="m6OgY8HdeAOI59RmeT0Ue6ortvnFbTmq9hg2duJnAKD0WYGQpN1xDCWQ9_fNi3fbYYd4c0FESi-jtoTt2B4W7gsYqaYD2mrHIqt9T8OEItsIIJfKB_5cHdhvG5ULq_TOqCI1.png"></b>
</div>
</details>

<details>
<summary>
<b>Create a temp busybox pod and connect via wget to the "foo" service. Verify that each time there's a different hostname returned (deployment with 3 replicas).</b>
</summary>
<div>Get the service ClusterIP
<i>kubectl get svc</i></div><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh</i>

Once a service is running, you can access it via the service name (DNS)
<i>wget -O- foo:6262
wget -O- &lt;ServiceClusterIP&gt;:6262</i>
</details>

<details>
<summary>
<b>Create busybox pod with two containers, each one will have the image busybox and will run the 'sleep 3600' command. Make both containers mount an emptyDir at '/etc/foo'.</b>
</summary>
Best way to do this is create a YAML template (single-container pod) and duplicate the container definition (make sure to change the name of the second container).<div>
</div><div><i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>
</div><div><i>
</i></div><div>Add the <i>spec.volumes </i>and the <i>spec.containers.volumeMounts </i>sections to the YAML (make sure to mount in both containers)

emptyDir volume looks like:
<i>spec:
&nbsp; volumes:</i></div><div><i>&nbsp; - name: myvol</i></div><div><i>&nbsp; &nbsp; emptyDir: {}
</i></div>
</details>

<details>
<summary>
<b>You have a two-container pod with a shared volume at '/etc/foo' on both containers.
Connect to the second busybox, write the first column of '/etc/passwd' file to '/etc/foo/passwd'. Connect to the first busybox and write '/etc/foo/passwd' file to standard output.</b>
</summary>
Connect to the second container:
<i>kubectl exec -it busybox -c busybox2 -- /bin/sh</i><div><div>/etc/passwd is colon delimited, use cut to get the first column</div><div><i>cut -f 1 -d ':' /etc/passwd &gt; /etc/foo/passwd</i></div><div><i>cat </i><i>/etc/foo/passwd</i></div><div><div><i>exit
</i>
Connect to the first container:
<i>kubectl exec -it busybox -c busybox -- /bin/sh</i></div><div>confirm the mounting</div><div><i>mount | grep foo</i></div><div><i>cat /etc/foo/passwd</i></div><div><i>exit</i>
</div></div></div>
</details>

<details>
<summary>
<b>Create a busybox pod with 'sleep 3600' as arguments. Copy '/etc/passwd' from the pod to your local folder.</b>
</summary>
Use the <i>kubectl cp &lt;pod&gt;:&lt;path&gt; &lt;dest&gt; </i>command.

<i>kubectl run busybox --image=busybox --restart=Never -- sleep 3600</i><div>using "." as the destination to drop it into current folder
<div><i>kubectl cp busybox:/etc/passwd .</i></div><div><i>cat passwd</i></div></div>
</details>

<details>
<summary>
<b>A Kubernetes concept that represents the smallest unit of deployment.</b>
</summary>
Pod
</details>

<details>
<summary>
<b>Mounted directories that are accessible from inside containers.</b>
</summary>
Volumes
</details>

<details>
<summary>
<b>The command to get Pod logs in Kubernetes.</b>
</summary>
`kubectl get logs`
</details>

<details>
<summary>
<b><div style="">Provide command to list all Kubernetes pods in the namespace</div></b>
</summary>
kubectl get pods

<b><img src="FezLZbLjz3LT7Bln0xYjl6Z10-ai2OT1U9S5LkMmhNtj-0QuEfayELPDmiiVMrzhrdywH9DUsygN-GFkm89DYnmUqp7Q306g7tdiyOkXuHWd6heoI5Ojy8EIDffXyG4NxzFJ.png"></b>
</details>

<details>
<summary>
<b>When annoying to have to keep typing&nbsp;kubectl get pods...&nbsp;every few seconds to see if anything’s happened.</b>
</summary>
kubectl&nbsp;provides the&nbsp;--watch&nbsp;flag (-w&nbsp;for short)
kubectl get pods --watch
</details>

<details>
<summary>
<b>Can we edit live pod cofiguration?</b>
</summary>
Yes, but not recommended due to out-of-syc

<strong>kubectl edit deployments my-deployment</strong>
</details>

<details>
<summary>
<b>How to execute Commands on Containers</b>
</summary>
kubectl container run --image alpaine --command -- sleep 999<div>kubectl get pods</div><div>
</div><div>#NAME READY STATUS RESTARTS AGE&nbsp;</div><div>#alpine-7fd44fc4bf-7gl4n 1/1 Running 0 4s
</div><div>
</div><div>kubectl exec -it alpine-7fd44fc4bf-7gl4n /bin/sh</div><div>
</div><div>#will run the command in the first container by default, when more than one conainer present
</div><div>
</div>
</details>

<details>
<summary>
<b>What are PodPresets? Example of PodPresets</b>
</summary>
<div>PodPresets:<strong>
</strong></div><div>A&nbsp;Pod Preset&nbsp;is an API resource for injecting additional runtime requirements into a Pod at creation time. You use&nbsp;label selectors&nbsp;to specify the Pods to which a given Pod Preset applies.
</div><div><strong>
</strong></div><div><strong>
</strong></div><div><strong>Specific Example:</strong></div>
<div>Specific Example:

1. Database Administrator provisions a MySQL service for their cluster.
2. Database Administrator creates secrets for the cluster containing the database name, username, and password.
3. Database Administrator creates a PodPreset defining the database &nbsp;&nbsp;port as an environment variable, as well as the secrets. See Examples below for various examples.
4. Developer of an application can now label their pod with the specified Selector the Database Administrator tells them, and consume the MySQL database without needing to know any of the details from step 2 and 3.
</div>
</details>

<details>
<summary>
<b>Can PodPresets override POD settings.</b>
</summary>
<div>PodPresets can’t be used to override a Pod’s own configuration, only to fill in settings which the Pod itself doesn’t specify. A Pod can opt out of being modified by PodPresets altogether, by setting the annotation:</div>podpreset.admission.kubernetes.io/exclude: "true"
</details>

<details>
<summary>
<b>Everything about running Pod</b>
</summary>
Labels are key-value pairs that identify resources, and can be used with selectors to match a specified group of resources.

Node affinities attract or repel Pods to or from nodes with specified attributes. For example, you can specify that a Pod can only run on a node in a specified availability zone.

While hard node affinities can block a Pod from running, soft node affinities are more like suggestions to the scheduler. You can combine multiple soft affinities with different weights.

Pod affinities express a preference for Pods to be scheduled on the same node as other Pods. For example, Pods that benefit from running on the same node can express that using a Pod affinity for each other.

Pod anti-affinities repel other Pods instead of attracting. For example, an anti-affinity to replicas of the same Pod can help spread your replicas evenly across the cluster.

Taints are a way of tagging nodes with specific information; usually, about node problems or failures. By default, Pods won’t be scheduled on tainted nodes.

Tolerations allow a Pod to be scheduled on nodes with a specific taint. You can use this mechanism to run certain Pods only on dedicated nodes.

DaemonSets allow you to schedule one copy of a Pod on every node (for example, a logging agent).

StatefulSets start and stop Pod replicas in a specific numbered sequence, allowing you to address each by a predictable DNS name. This is ideal for clustered applications, such as databases.

Jobs run a Pod once (or a specified number of times) before completing. Similarly, Cronjobs run a Pod periodically at specified times.

Horizontal Pod Autoscalers watch a set of Pods, trying to optimize a given metric (such as CPU utilization). They increase or decrease the desired number of replicas to achieve the specified goal.

PodPresets can inject bits of common configuration into all selected Pods at creation time. For example, you could use a PodPreset to mount a particular Volume on all matching Pods.

Custom Resource Definitions (CRDs) allow you to create your own custom Kubernetes objects, to store any data you wish. Operators are Kubernetes client programs that can implement orchestration behavior for your specific application (for example, MySQL).

Ingress resources route requests to different services, depending on a set of rules, for example, matching parts of the request URL. They can also terminate TLS connections for your application.

Istio is a tool that provides advanced networking features for microservice applications and can be installed, like any Kubernetes application, using Helm.

Envoy provides more sophisticated load balancing features than standard cloud load balancers, as well as a service mesh facility.
</details>

<details>
<summary>
<b>kubectl run --attach</b>
</summary>
wait for the Pod to start running, and then attach to the Pod as if 'kubectl attach ...' were called.&nbsp;
</details>

<details>
<summary>
<b>kubectl run --cascade</b>
</summary>
<div>(DEFAULT)</div><div>
</div>Cascade the deletion of the resources managed by this resource (e.g. Pods created by a ReplicationController).&nbsp;
</details>

<details>
<summary>
<b>kubectl logs POD [-c CONTAINER]</b>
</summary>
Print the logs of a container/resource.<div>
</div><div>--follow</div><div>
</div><div>--tail</div><div><table><tbody><tr><td>Lines of recent log file to display.</td></tr><tr></tr></tbody></table></div><div>
</div><div>--since, --since-time</div><div><table><tbody><tr><td>Only return logs newer than a relative duration like 5s, 2m, or 3h, or after a specific date. Defaults to all logs.&nbsp;
</td></tr><tr></tr></tbody></table>
</div><div>--ignore-errors</div><div>If following, allow errors that occur to be non-fatal</div><div>
</div><div>
</div><div>--prefix</div><div>Prefix logs with pod and container name</div><div>
</div><div>--timestamps</div><div>Include timestamps</div>
</details>

<details>
<summary>
<b>kubectl port-forward POD LOCALPORT:REMOTEPORT</b>
</summary>
<div>Forward one or more local ports to a pod.&nbsp;</div><div>
</div><div><b>--address&nbsp;</b></div><div><table><tbody><tr><td>Localhost or IP address(es) to listen on (comma separated). 

When localhost is supplied, kubectl will try to bind on both 127.0.0.1 and ::1 and will fail if neither of these addresses are available to bind.</td></tr><tr></tr></tbody></table></div><div>
</div><div>This command requires the node to have 'socat' installed.</div>
</details>

<details>
<summary>
<b>containers.imagePullPolicy</b>
</summary>
Always<div>
</div><div>Never</div><div>
</div><div>IfNotPresent</div>
</details>

<details>
<summary>
<b>containers.args</b>
</summary>
Arguments to the entrypoint<div>
</div><div>Default: the image's CMD line</div><div>
</div><div><font color="#ff0000">CANNOT BE UPDATED</font></div>
</details>

<details>
<summary>
<b>containers.command</b>
</summary>
Entrypoint array<div>
</div><div>Not executed in a shell</div><div>
</div><div>Default: the image's ENTRYPOINT</div><div>
</div><div><font color="#ff0000">CANNOT BE UPDATED</font></div>
</details>

<details>
<summary>
<b>containers.env</b>
</summary>
List of env vars<div>
</div><div><font color="#ff0000">CANNOT BE UPDATED</font></div>
</details>

<details>
<summary>
<b>containers.envFrom</b>
</summary>
List of sources to populate env vars<div>
</div><div><font color="#ff0000">CANNOT BE UPDATED</font>
</div>
</details>

<details>
<summary>
<b>containers.image</b>
</summary>
container image url
</details>

<details>
<summary>
<b>containers.lifecycle</b>
</summary>
Actions to take in response to lifecycle events<div><b>
</b></div><div><b>postStart</b></div><div>Called after a container is created</div><div>
</div><div>If it fails, container restarts according to restart policy</div><div><b>
</b></div><div><b>preStop</b>
<div>Called before a container is terminated (not if it crashes/exits)</div><div>
</div><div><font color="#ff0000">CANNOT BE UPDATED</font>
</div></div>
</details>

<details>
<summary>
<b>containers.livenessProbe</b>
</summary>
Periodic probe of container liveness<div>
</div><div>Restart container if fails</div><div>
</div><div><div>httpGet: request to perform</div><div>
</div><div>failureThreshold: failures needed to mark probe failed</div><div>
</div><div>successThreshold: successes needed to mark probe succeeded</div><div>
</div><div>initialDelaySeconds: seconds before liveness probes begin</div><div>
</div><div>periodSeconds: how often to probe</div></div>
</details>

<details>
<summary>
<b>containers.name</b>
</summary>
Unique name of the container
</details>

<details>
<summary>
<b>containers.ports</b>
</summary>
Ports to expose from container<div>
</div><div>name:</div><div>
</div><div>protocol:</div><div>
</div><div>containerPort: #</div><div>
</div><div>hostIP:</div><div>
</div>
</details>

<details>
<summary>
<b>containers.readinessProbe</b>
</summary>
Periodic probe of container service readiness.<div>
</div><div>Container removed from svc endpoints if probe fails</div><div>
</div><div>httpGet: request to perform</div><div>
</div><div>failureThreshold: failures needed to mark probe failed</div><div>
</div><div>successThreshold: successes needed to mark probe succeeded</div><div>
</div><div>initialDelaySeconds: seconds before liveness probes begin</div><div>
</div><div>periodSeconds: how often to probe</div>
</details>

<details>
<summary>
<b>containers.securityContext</b>
</summary>
Container's security config<div>
</div><div>runAsUser:</div><div>
</div><div><div><div>runAsGroup:&nbsp;</div></div></div><div>
</div><div>runAsNonRoot:</div><div>
</div><div>capabilities:
</div><div>
</div><div><div>privileged:</div></div><div>
</div><div><div>procMount:</div></div><div>
</div><div><div>seLinuxOptions:</div><div>
</div></div><div>readOnlyRootFilesystem:</div><div>
</div><div>allowPrivilegeEscalation:</div>
</details>

<details>
<summary>
<b>containers.VolumeMount</b>
</summary>
Mounting of a Volume in a container<div>
</div><div>name: same as volume</div><div>
</div><div>readOnly:</div><div>
</div><div>mountPath: Path in the container where the volume is mounted
</div><div>
</div><div>subPath: Path in the volume to mount in the container</div><div>
</div><div>subPathExpr:</div>
</details>

<details>
<summary>
<b>containers.workingDir</b>
</summary>
Container's working directory
</details>

<details>
<summary>
<b>In terms of Docker constructs, a Pod is modelled as a group of Docker containers with shared _____ and shared _____</b>
</summary>
namespaces<div>
</div><div>filesystem volumes</div>
</details>

<details>
<summary>
<b>Are pods intended to survive through scheduling failures, node failures or other evictions?</b>
</summary>
No
</details>

<details>
<summary>
<b>How can any container in a pod enable privileged mode?</b>
</summary>
Using the <b>privileged</b>&nbsp;flag in the security context of the container spec.
</details>

<details>
<summary>
<b>Why would you allow a container to run in privileged mode?</b>
</summary>
to allow Linux capabilities inside the container.<div>
</div><div>-----</div><div>
</div><div>Ex.:</div><div>
</div><div>accessing devices</div><div>network stack manipulation</div><div>writing network and volume plugins</div>
</details>

<details>
<summary>
<b>A pod represents _____ processes running in your cluster.</b>
</summary>
Processes
</details>

<details>
<summary>
<b>A pod is the basic _____ unit of Kubernetes.</b>
</summary>
execution
</details>

<details>
<summary>
<b>A pod encapsulates an application's...</b>
</summary>
container
<hr>
execution options
<hr>
IP address
<hr>
storage resources
</details>

<details>
<summary>
<b>Do pods run a single container each?</b>
</summary>
Not necessarily. They can run multiple containers.
</details>

<details>
<summary>
<b>Are containers in a Pod automatically co-located and co-scheduled on the <b>same</b> physical or virtual machine in the cluster?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Can a pod's containers share resources, dependensies, communicate with each other and coordinate their lifecycle?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Example sidecar container pattern diagram</b>
</summary>
<img src="pod.svg">
</details>

<details>
<summary>
<b>Do Pods each have a unique IP address?</b>
</summary>
Yes, for each address family
</details>

<details>
<summary>
<b>kubectl top pod</b>
</summary>
<div>Display Resource usage of pods.</div><div>
</div><div>--containers</div><div>Print usage of containers in a pod</div>
</details>

<details>
<summary>
<b>Create a busybox pod (using kubectl command) that runs the command "env"</b>
</summary>
<i>kubectl run busybox
 --image=busybox 
--restart=Never 
--command -- env</i>

arguments after -- are commands
</details>

<details>
<summary>
<b>If a pod crashed and restarted, get logs about a previous instance</b>
</summary>
<i>kubectl logs mypod --previous</i>
</details>

<details>
<summary>
<b>Open a shell session in a pod</b>
</summary>
<i>kubectl exec -it mypod -- /bin/sh</i>
</details>

<details>
<summary>
<b>show all labels of pods</b>
</summary>
<i>kubectl get pods --show-labels</i>
</details>

<details>
<summary>
<b>Get a pod's YAML without cluster-specific information</b>
</summary>
use the <i>--export </i>flag<div><i>kubectl get pod mypod -o yaml --export</i></div>
</details>

<details>
<summary>
<b>Get only the pods with label app=v2</b>
</summary>
<i>kubectl get pods -l app=v2</i>
or
<i>kubectl get pods -l 'app in (v2)'</i>
</details>

<details>
<summary>
<b>kubectl attach POD -c container</b>
</summary>
Attach to a container's process.<div>
</div><div><b>--stdin</b></div><div>Pass stdin to the container</div><div>
</div><div><b>--tty</b></div><div>stdin is a tty</div>
</details>

<details>
<summary>
<b>Load a configmap "cmvolume" as a volume inside a pod, on the path "/etc/lala". Check this exists on the created pod.</b>
</summary>
Edit pod YAML, need to add <i>spec.volumes </i>and <i>containers.volumeMounts </i>like for loading any volume.

<i>spec:</i><div><i>&nbsp; volumes:</i></div><div><i>&nbsp; - name: myvol
&nbsp; &nbsp; configMap:</i></div><div><i>&nbsp; &nbsp; &nbsp; name: cmvolume # name of configmap</i></div><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - volumeMounts:</i></div><div><i>&nbsp; &nbsp; - name: myvol # matches name above</i></div><div><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/lala</i></div><div><i>
</i></div><div>to check path exists on the pod:
<i>kubectl exec -it mypod -- ls /etc/lala</i>
or spawn an interactive session
<i>kubectl exec -it mypod -- /bin/sh</i></div><div><i>cd /etc/lala</i></div><div><i>ls</i></div><div><i>cat var8</i></div>
</details>

<details>
<summary>
<b>Create an nginx pod with a liveness probe that just runs the command 'ls'. Run it, check its probe status, delete it.</b>
</summary>
Add the <i>spec.containers.livenessProbe</i>&nbsp;section to the standard pod YAML:<div>
</div><div><i>spec:</i></div><div><i>&nbsp; containers</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; livenessProbe:</i></div><div><i>&nbsp; &nbsp; &nbsp; exec:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; command:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; - ls</i></div>
</details>

<details>
<summary>
<b>Modify the liveness probe in the nginx pod so it starts after 5 seconds and probes every 10 seconds.</b>
</summary>
Add the <i>spec.containers.livenessProbe.initialDelaySeconds and .periodSeconds </i>values:

<i>spec:</i><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; livenessProbe:</i></div><div><i>&nbsp; &nbsp; &nbsp; initialDelaySeconds: 5</i></div><div><i>&nbsp; &nbsp; &nbsp; periodSeconds: 10</i></div>
</details>

<details>
<summary>
<b>Create a busybox pod that runs 'ls /notexist'. Determine if there's an error (of course there is), see it.&nbsp;</b>
</summary>
<i>kubectl run mypod --image=busybox --restart=Never -- /bin/sh -c 'ls /notexist'</i>

show that there are errors
<i>kubectl logs mypod</i><div><i>kubectl describe pod mypod</i></div>
</details>

<details>
<summary>
<b>Create a pod that mounts the variable "username" from secret "mysecret2" into an env variable called USER</b>
</summary>
edit pod YAML to add the <i>spec.containers.env.valueFrom.secretKeyRef </i>section:

<i>spec:</i><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; env:</i></div><div><i>&nbsp; &nbsp; - name: USER</i></div><div><i>&nbsp; &nbsp; &nbsp; valueFrom:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; secretKeyRef:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; name: mysecret2</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; key: username</i></div>
</details>

<details>
<summary>
<b>Create an nginx pod that uses 'myuser' as a service account</b>
</summary>
<i>kubectl run mypod --image=nginx --restart=Never --serviceaccount=myuser</i>

Or edit pod YAML to add the <i>spec.serviceAccountName </i>value

<i>spec:</i><div><i>&nbsp; serviceAccountName: myuser</i></div>
</details>

<details>
<summary>
<b>Create an nginx pod (that includes port 80) with an HTTP readinessProbe on path '/' on port 80.</b>
</summary>
Create the pod including the <i>--port </i>flag<div><i>kubectl run mypod --image=nginx --restart=Never --port=80 --dry-run -o yaml &gt; pod.yaml</i>

Add the <i>readinessProbe.httpGet </i>section:
<i>spec:</i></div><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; readinessProbe:</i></div><div><i>&nbsp; &nbsp; &nbsp; httpGet:</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; path: /</i></div><div><i>&nbsp; &nbsp; &nbsp; &nbsp; port: 80</i></div>
</details>

<details>
<summary>
<b>Delete the pod "mypod" forcefully with no grace period</b>
</summary>
<i>kubectl delete pod mypod --force --grace-period=0</i>
</details>

<details>
<summary>
<b>The <b>phase </b>of a pod is...</b>
</summary>
A high-level summary of where the pod is in its lifecycle
</details>

<details>
<summary>
<b><b>Pending</b> phase</b>
</summary>
<table><tbody><tr><td>The Pod has been accepted by the Kubernetes system, but one or more of the Container images has not been created. This includes time before being scheduled as well as time spent downloading images over the network, which could take a while.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Running</b>&nbsp;phase</b>
</summary>
<table><tbody><tr><td>The Pod has been bound to a node, and all of the Containers have been created. At least one Container is still running, or is in the process of starting or restarting.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Succeeded </b>phase</b>
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated in success, and will not be restarted.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Failed </b>phase</b>
</summary>
<table><tbody><tr><td>All Containers in the Pod have terminated, and at least one Container has terminated in failure. That is, the Container either exited with non-zero status or was terminated by the system.</td></tr><tr></tr></tbody></table>
</details>

<details>
<summary>
<b><b>Unknown </b>phase</b>
</summary>
For some reason the state of the Pod could not be obtained, typically due to an error in communicating with the host of the Pod.
</details>

<details>
<summary>
<b>List all 5 Pod <b>phases</b></b>
</summary>
Pending<div>
</div><div>Running</div><div>
</div><div>Succeeded</div><div>
</div><div>Failed</div><div>
</div><div>Unknown</div>
</details>

<details>
<summary>
<b>List all six fields in a <b>PodCondition</b></b>
</summary>
reason<div>
</div><div>status</div><div>
</div><div>message</div><div>
</div><div>type</div><div>
</div><div>lastProbeTime</div><div>
</div><div>lastTransitionTime</div>
</details>

<details>
<summary>
<b>The <b>lastProbeTime</b>&nbsp;condition field provides...</b>
</summary>
A timestamp for when the Pod condition was last probed.
</details>

<details>
<summary>
<b>The&nbsp;<b>lastTransitionTime</b>&nbsp;condition field provides...</b>
</summary>
a timestamp for when the Pod last transitioned from one status to another.
</details>

<details>
<summary>
<b>The <b>message&nbsp;</b>condition field provides...</b>
</summary>
a human-readable message indicating details about the transition from one status to another.
</details>

<details>
<summary>
<b>The <b>reason&nbsp;</b>condition field provides...</b>
</summary>
a unique, one-word reason for the condition's last transition.
</details>

<details>
<summary>
<b>The <b>status</b>&nbsp;condition field provides...</b>
</summary>
<div>One of the following:</div><div><b>
</b></div><div><b>"True"</b></div><div><b>
</b></div><div><b>"False"</b></div><div><b>
</b></div><div>"<b>Unknown"</b></div>
</details>

<details>
<summary>
<b>The <b>type</b>&nbsp;condition field provides...</b>
</summary>
One of the following:<div>
</div><div><b>PodScheduled</b></div><div>Pod has been scheduled to a node</div><div><b>
</b></div><div><b>Ready</b></div><div>Pod is able to serve requests</div><div><b>
</b></div><div><b>Initialized</b></div><div>All init containers have started successfully</div><div><b>
</b></div><div><b>ContainersReady</b></div><div>All containers in the pod are ready</div>
</details>

<details>
<summary>
<b><div>A probe can have one of three results:</div></b>
</summary>
<b>Success</b><div>The Container passed the diagnostic
<div><b>
</b></div><div><b>Failure</b></div><div>The Container failed the diagnostic</div><div><b>
</b></div><div><b>Unknown</b></div></div><div>The diagnostic failed, so no action should be taken</div>
</details>

<details>
<summary>
<b>A livenessProbe indicates whether a container is...</b>
</summary>
running
</details>

<details>
<summary>
<b>If a livenessProbe fails, the container...</b>
</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
</details>

<details>
<summary>
<b>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe<div>
</div><div>What will be the state of each probe of the container?</div></b>
</summary>
<b>Success </b>on all of them
</details>

<details>
<summary>
<b>readinessProbe indicates whether...</b>
</summary>
a container is ready to service requests.
</details>

<details>
<summary>
<b>If the readinessProbe fails, what happens?</b>
</summary>
The <b>endpoints controlller</b> removes the <b>Pod's IP address</b> from the endpoints of all <b>Services </b>that match the Pod
</details>

<details>
<summary>
<b>A container's default readiness state before the initial delay is...</b>
</summary>
Failure
</details>

<details>
<summary>
<b>startupProbe indicates whether...</b>
</summary>
the application in the container has started.
</details>

<details>
<summary>
<b>A startupProbe is provided to a container<div>
</div><div>What happens to the other probes?</div></b>
</summary>
All other probes are disabled until startupProbe succeeds.
</details>

<details>
<summary>
<b>If the startupProbe fails, the container...</b>
</summary>
is killed by the kubelet, then subjected to the container's <b>restart policy</b>.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Do you still need a livenessProbe?</span></div></b>
</summary>
Not necessarily.&nbsp;<div>
</div><div><span style="color: rgb(34, 34, 34);">The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;</span><code>restartPolicy</code><span style="color: rgb(34, 34, 34);">.</span>
</div>
</details>

<details>
<summary>
<b>A container should be killed or restarted if a probe fails. What can be done to achieve this?</b>
</summary>
1. Specify a <b>livenessProbe&nbsp;</b><div>
</div><div>2. Add a <b>restartPolicy </b>of <b>Always </b>or <b>OnFailure</b></div>
</details>

<details>
<summary>
<b>A Pod should only be sent traffic when a probe succeeds. What can achieve this?</b>
</summary>
readinessProbe
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A Container should be able to take itself down for maintenance. What can achieve this?</span></b>
</summary>
A <b>readinessProbe </b>that checks an endpoints specific to readiness that is different from the liveness probe.
</details>

<details>
<summary>
<b>The three possible states of containers are...</b>
</summary>
Waiting<div>
</div><div>Running</div><div>
</div><div>Terminated</div>
</details>

<details>
<summary>
<b>A container is <b>Waiting </b>when...</b>
</summary>
It is neither <b>Running </b>or <b>Terminated</b><div>
</div><div>A <b>Waiting </b>container still runs operations like pulling images, applying Secrets etc.</div>
</details>

<details>
<summary>
<b>How to tell why a container is in&nbsp;<b>Waiting </b>state?</b>
</summary>
Check the state's&nbsp;<b>Reason </b>field
</details>

<details>
<summary>
<b>A container is in the <b>Running </b>state when...</b>
</summary>
It is executing without issues.
</details>

<details>
<summary>
<b>Which hook is executed prior to a container entering its <b>Running </b>state?</b>
</summary>
postStart
</details>

<details>
<summary>
<b>A container is in the <b>Terminated </b>state when...</b>
</summary>
It has successfully or unsuccessfully completed execution.
</details>

<details>
<summary>
<b>How to tell why a container is in <b>Terminated </b>state?</b>
</summary>
Check the state's <b>Reason </b>and <b>Exit Code</b> fields.
</details>

<details>
<summary>
<b>Which hook is executed before a container enters Terminated state?</b>
</summary>
preStop
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Inject extra feedback or signals into PodStatus via...</span></b>
</summary>
<b>Pod readiness</b>
</details>

<details>
<summary>
<b>You can add <b>Pod readiness</b> into <b>PodStatus </b>by...</b>
</summary>
<b>readinessGates</b><div>
</div><div>Add it into PodSpec to specify a list of extra conditions for the kubelet to evaluate</div><div>
</div><div>Ex.:</div><div>
</div><div><pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span>...<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">readinessGates</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">conditionType</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"www.example.com/feature-1"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">conditions</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">type</span>:<span style="color: rgb(187, 187, 187);"> </span>Ready<span style="color: rgb(187, 187, 187);">                              </span><span style="color: rgb(0, 136, 0); font-style: italic;"># a built in PodCondition</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"False"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastProbeTime</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">null</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastTransitionTime</span>:<span style="color: rgb(187, 187, 187);"> </span>2018-01-01T00:00:00Z<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">type</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"www.example.com/feature-1"</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># an extra PodCondition</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">status</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"False"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastProbeTime</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">null</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">lastTransitionTime</span>:<span style="color: rgb(187, 187, 187);"> </span>2018-01-01T00:00:00Z<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containerStatuses</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">containerID</span>:<span style="color: rgb(187, 187, 187);"> </span>docker://abcd...<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">ready</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(170, 34, 255); font-weight: 700;">true</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span>...</code></pre></div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of...</span></b>
</summary>
<b>status.condition</b> fields for the Pod<div>
</div><div>If such a field isn't found, the status of the condition defaults to <b>"False"</b></div>
</details>

<details>
<summary>
<b><b>restartPolicy </b>possible values are...</b>
</summary>
Always<div>
</div><div>Never</div><div>
</div><div>OnFailure</div>
</details>

<details>
<summary>
<b>Default restartPolicy is...</b>
</summary>
Always
</details>

<details>
<summary>
<b>Does a Pod's <b>restartPolicy </b>apply to all its containers?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Once bound to a node, will a Pod ever rebound to another node?</b>
</summary>
No
</details>

<details>
<summary>
<b>Does<code> restartPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;only refer to restarts of the Containers by the kubelet on the same node?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Exited Containers that are restarted by the kubelet are restarted with an _____ delay capped at _____ and is reset after ten minutes of successful execution.</span></b>
</summary>
exponential back-off<div>
</div><div>5 minutes</div>
</details>

<details>
<summary>
<b>Example livenessProbe spec</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">labels</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">test</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness-http<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">args</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- /server<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/liveness<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">livenessProbe</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">httpGet</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># when "host" is not defined, "PodIP" will be used</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># host: my-host</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># when "scheme" is not defined, "HTTP" scheme will be used. Only "HTTP" and "HTTPS" are allowed</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(0, 136, 0); font-style: italic;"># scheme: HTTPS</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">path</span>:<span style="color: rgb(187, 187, 187);"> </span>/healthz<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">port</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">8080</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span><span style="color: rgb(170, 34, 255); font-weight: 700;">httpHeaders</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">        </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>X-Custom-Header<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">          </span><span style="color: rgb(170, 34, 255); font-weight: 700;">value</span>:<span style="color: rgb(187, 187, 187);"> </span>Awesome<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">initialDelaySeconds</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">15</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">      </span><span style="color: rgb(170, 34, 255); font-weight: 700;">timeoutSeconds</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(102, 102, 102);">1</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>liveness</code></pre>
</details>

<details>
<summary>
<b>A pod has one container. The container exits with <b>success</b>.<div>
</div><div>What happens depending on each possible <b>restartPolicy</b>?</div></b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li></ul>
</details>

<details>
<summary>
<b>A pod has one container. The container exits with&nbsp;<b>failure</b>.<div>
</div><div>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</div></b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b><div><div>Pod is running and has two Containers. Container 1 exits with <b>failure</b>.</div></div><div>
</div><div>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</div></b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Do not restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li></ul><div><span style="color: rgb(34, 34, 34);">If Container 1 is not running, and Container 2 exits:</span></div><div><ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul></div>
</details>

<details>
<summary>
<b><div><div><div>Pod is running and has one Container. Container runs <b>out of memory </b>(and terminates in failure)</div></div></div><div>
</div><div>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</div></b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Log failure event; Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b><div><div><div><div>Pod is running, and a disk dies.</div></div></div></div><div>
</div><div>What happens?</div></b>
</summary>
<ul><li>Kill all Containers.</li><li>Log appropriate event.</li><li>Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<b><div><div><div><div><div>Pod is running, and its node is segmented out.</div></div></div></div></div><div>
</div><div>What happens?</div></b>
</summary>
<ul><li>Node controller waits for timeout.</li><li>Node controller sets Pod&nbsp;<code>phase</code>&nbsp;to Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A PodPreset allows pod template authors to not have to explicitly provide all information for every pod.&nbsp;</span><span style="color: rgb(34, 34, 34);">PodPresets are objects for injecting&nbsp;</span><span style="color: rgb(34, 34, 34);">additional runtime requirements&nbsp;</span><span style="color: rgb(34, 34, 34);">into pods at _____</span></b>
</summary>
creation time
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You use _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to specify the Pods to which a given PodPreset applies.</span></b>
</summary>
label selectors
</details>

<details>
<summary>
<b>What applies Pod Presets to incoming pod creation requests?</b>
</summary>
PodPreset admission controller
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod creation request occurs, the system does the following:</span></b>
</summary>
<ol><li>Retrieve all&nbsp;<code>PodPresets</code>&nbsp;available for use.</li><li>Check if the label selectors of any&nbsp;<code>PodPreset</code>&nbsp;matches the labels on the pod being created.</li><li>Attempt to merge the various resources defined by the&nbsp;<code>PodPreset</code>&nbsp;into the Pod being created.</li><li>On error, throw an event documenting the merge error on the pod, and create the pod&nbsp;<em>without</em>&nbsp;any injected resources from the&nbsp;<code>PodPreset</code>.</li><li>Annotate the resulting modified Pod spec to indicate that it has been modified by a&nbsp;<code>PodPreset</code>. The annotation is of the form&nbsp;<code>podpreset.admission.kubernetes.io/podpreset-&lt;pod-preset name&gt;: "&lt;resource version&gt;"</code>.</li></ol>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">&nbsp;When a&nbsp;</span><code>PodPreset</code><span style="color: rgb(34, 34, 34);">&nbsp;is applied to one or more Pods, Kubernetes modifies the _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">PodSpec</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For changes to&nbsp;</span><code>Env</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>EnvFrom</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeMounts</code><span style="color: rgb(34, 34, 34);">, Kubernetes modifies _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The pod's individual container specs</span>
</details>

<details>
<summary>
<b>How to&nbsp;disable Pod Preset for a Specific Pod</b>
</summary>
<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">podpreset.admission.kubernetes.io/exclude: "true"</span><div><span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span></div><div>Add the above annotation in the Pod Spec<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span></div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can use&nbsp;</span><em>topology spread constraints</em><span style="color: rgb(34, 34, 34);">&nbsp;to control...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains)</span></div>
</details>

<details>
<summary>
<b><div><div>You have a 4-node cluster with the following labels:</div><pre><code>NAME    STATUS   ROLES    AGE     VERSION   LABELS
node1   Ready    &lt;none&gt;   4m26s   v1.16.0   node=node1,zone=zoneA
node2   Ready    &lt;none&gt;   3m58s   v1.16.0   node=node2,zone=zoneA
node3   Ready    &lt;none&gt;   3m17s   v1.16.0   node=node3,zone=zoneB
node4   Ready    &lt;none&gt;   2m43s   v1.16.0   node=node4,zone=zoneB</code></pre></div><div>What would the cluster logically look like?</div></b>
</summary>
<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Topology spread constraints rely on _____ to&nbsp;</span><span style="color: rgb(34, 34, 34);">identify the topology domain(s) that each Node is in.</span></b>
</summary>
node labels
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can define one or multiple _____&nbsp;</span>to instruct the kube-scheduler how to place each incoming Pod in relation to the existing Pods across your cluster.</b>
</summary>
<code>topologySpreadConstraint</code>
</details>

<details>
<summary>
<b><b>topologySpreadConstraints </b>syntax</b>
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
<b><strong>maxSkew</strong><span style="color: rgb(34, 34, 34);">&nbsp;describes...</span></b>
</summary>
the degree to which Pods may be unevenly distributed.<div>
</div><div><span style="color: rgb(34, 34, 34);">It's the maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type.</span>
</div><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">It must be greater than zero.</span><span style="color: rgb(34, 34, 34);">
</span></div>
</details>

<details>
<summary>
<b><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
</details>

<details>
<summary>
<b><div><div><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one <b>topologyKey </b>and have identical values for that label, the scheduler treats both Nodes as _____</span></div></div><div>
</div><div>
</div></b>
</summary>
<span style="color: rgb(34, 34, 34);">Being in the same topology.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">The scheduler tries to place a balanced number of Pods into each topology domain</span><span style="color: rgb(34, 34, 34);">
</span></div>
</details>

<details>
<summary>
<b><strong>whenUnsatisfiable</strong><span style="color: rgb(34, 34, 34);">&nbsp;indicates...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">How to deal with a Pod if it doesn't satisfy the spread constraint</span>
</details>

<details>
<summary>
<b><b>whenUnsatisfiable </b>possible values:</b>
</summary>
<div><b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b></div><div><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">
</span></div><div><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span></div>
</details>

<details>
<summary>
<b><div><h3>Example: One TopologySpreadConstraint</h3></div><div>Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):</div><pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre><div>If we want an incoming Pod to be evenly spread with existing Pods across zones, the spec can be given as:</div></b>
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
<b><h3>Example: Multiple TopologySpreadConstraints<a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/#example-multiple-topologyspreadconstraints"></a></h3><div>&nbsp;Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):</div><pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre><div>You can use 2 TopologySpreadConstraints to control the Pods spreading on both zone and node:</div></b>
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
<b><span style="color: rgb(34, 34, 34);">Only the Pods holding the same _____ as the incoming Pod can be matching candidates</span></b>
</summary>
namespace
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Nodes without&nbsp;</span><code>topologySpreadConstraints[*].topologyKey</code><span style="color: rgb(34, 34, 34);">&nbsp;present will be...</span></b>
</summary>
<b>bypassed</b><div><b>
</b></div><div>This implies that:
<div><ol><li>the Pods located on those nodes do not impact&nbsp;<code>maxSkew</code>&nbsp;calculation - in the above example, suppose "node1" does not have label "zone", then the 2 Pods will be disregarded, hence the incomingPod will be scheduled into "zoneA".</li><li>the incoming Pod has no chances to be scheduled onto this kind of nodes - in the above example, suppose a "node5" carrying label&nbsp;<code>{zone-typo: zoneC}</code>&nbsp;joins the cluster, it will be bypassed due to the absence of label key "zone".</li></ol></div></div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If the incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></b>
</summary>
bypassed
</details>

<details>
<summary>
<b><div>Suppose you have a 5-node cluster ranging from zoneA to zoneC:</div><pre><code>+---------------+---------------+-------+
|     zoneA     |     zoneB     | zoneC |
+-------+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 | node5 |
+-------+-------+-------+-------+-------+
|   P   |   P   |   P   |       |       |
+-------+-------+-------+-------+-------+
</code></pre><div>and you know that "zoneC" must be excluded. In this case, you can compose the yaml as below, so that "mypod" will be placed onto "zoneB" instead of "zoneC". Similarly&nbsp;<code>spec.nodeSelector</code>&nbsp;is also respected.</div></b>
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
<b><h2>Comparison of Topology with PodAffinity/PodAntiAffinity</h2><div><div>In Kubernetes, directives related to "Affinity" control how Pods are scheduled - more packed or more scattered.</div></div><div>
</div><div><ul><li>For <font face="monospace">_____</font>, you can try to pack any number of Pods into qualifying topology domain(s)</li><li>For&nbsp;<font face="monospace">_____</font>, only one Pod can be scheduled into a single topology domain.</li></ul></div></b>
</summary>
PodAffinity<div>
</div><div>PodAntiAffinity
</div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">It is possible to set default topology spread constraints for a cluster.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Default topology spread constraints are applied to a Pod if, and only if:</span></div></b>
</summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
</details>

<details>
<summary>
<b><div>An example <b>KubeSchedulerConfiguration </b>configuration for cluster-level default constraints might look like...</div></b>
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

<details>
<summary>
<b>Does deleting deployments or pods bypass Pod Disruption Budgets?</b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">Ex.:</span></div><div><span style="color: rgb(34, 34, 34);">A quorum-based application would like to ensure that the number of replicas running is never brought below the number needed for a quorum.&nbsp;</span></div><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total.</span><span style="color: rgb(34, 34, 34);">
</span></div></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Cluster managers and hosting providers should use tools which respect Pod Disruption Budgets by calling _____&nbsp;</span><span style="color: rgb(34, 34, 34);">instead of directly deleting pods or deployments</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">An example is the _____ command.</span></div></b>
</summary>
the Eviction API<div>
</div><div>kubectl drain</div>
</details>

<details>
<summary>
<b>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></b>
</summary>
replicas
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ADeployment has a&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">It is supposed to have 5 pods at any given time.&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">If its PDB allows for there to be 4 at a time, then the Eviction API will allow voluntary disruption of how many pods at a time?</span></div></b>
</summary>
<span style="color: rgb(34, 34, 34);">One</span>
</details>

<details>
<summary>
<b>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring.&nbsp;<div>
</div><div>Do involuntary disruptions count against the budget?</div></b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Do Pods which are deleted or unavailable due to a rolling upgrade to an application count against the disruption budget?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b>Are controllers (like deployment or statefulset) limited by PDBs when doing rolling updates?</b>
</summary>
<b>No</b><div>
</div><div><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec. (Learn about&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment">updating a deployment</a><span style="color: rgb(34, 34, 34);">.)</span></div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When a pod is evicted using the eviction API, is it gracefully terminated?</span></b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An ephemeral container&nbsp; runs temporarily in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish...</span></b>
</summary>
<div><b>user-initiated actions</b>&nbsp;</div><div>Such as troubleshooting and inspecting services</div>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Sometimes it's necessary to inspect the state of an existing Pod, however, for example to troubleshoot a hard-to-reproduce bug. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">in an existing Pod to _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">inspect its state and run arbitrary commands</span>
</div>
</details>

<details>
<summary>
<b>Will an ephemeral container ever be automatically restarted?</b>
</summary>
No
</details>

<details>
<summary>
<b>Do ephemeral containers have guaranteed resources?</b>
</summary>
No
</details>

<details>
<summary>
<b>Do ephemeral containers guarantee execution?</b>
</summary>
No
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Ephemeral containers are described using...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">the same&nbsp;</span><code>ContainerSpec</code><span style="color: rgb(34, 34, 34);">&nbsp;as regular containers</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">However, many fields are incompatible and disallowed</span></div>
</details>

<details>
<summary>
<b><div>You are trying to interactively troubleshoot a container.&nbsp;</div><div>
</div><div><code>kubectl exec</code>&nbsp;was insufficient because the container has crashed</div><div>
</div><div>The container image is <b>minimal </b>and&nbsp;<b>distroless </b>and doesn't include debugging utilities.</div>
<div>What can you use to troubleshoot?</div></b>
</summary>
Ephemeral containers
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.</b>
</summary>
process namespace sharing
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Ephemeral containers are created using the&nbsp;</span><code>ephemeralcontainers</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">subresource of Pod,&nbsp;</span><span style="color: rgb(34, 34, 34);">which can be demonstrated using&nbsp;</span><code>kubectl --raw.</code><div><code>
</code></div><div>First describe the ephemeral container to add as an EphemeralContainers list:<code>
</code></div></b>
</summary>
<div>{
</div><div><pre><code>    <span style="color: green; font-weight: 700;">"apiVersion"</span>: <span style="color: rgb(187, 68, 68);">"v1"</span>,
    <span style="color: green; font-weight: 700;">"kind"</span>: <span style="color: rgb(187, 68, 68);">"EphemeralContainers"</span>,
    <span style="color: green; font-weight: 700;">"metadata"</span>: {
            <span style="color: green; font-weight: 700;">"name"</span>: <span style="color: rgb(187, 68, 68);">"example-pod"</span>
    },
    <span style="color: green; font-weight: 700;">"ephemeralContainers"</span>: [{
        <span style="color: green; font-weight: 700;">"command"</span>: [
            <span style="color: rgb(187, 68, 68);">"sh"</span>
        ],
        <span style="color: green; font-weight: 700;">"image"</span>: <span style="color: rgb(187, 68, 68);">"busybox"</span>,
        <span style="color: green; font-weight: 700;">"imagePullPolicy"</span>: <span style="color: rgb(187, 68, 68);">"IfNotPresent"</span>,
        <span style="color: green; font-weight: 700;">"name"</span>: <span style="color: rgb(187, 68, 68);">"debugger"</span>,
        <span style="color: green; font-weight: 700;">"stdin"</span>: <span style="color: rgb(170, 34, 255); font-weight: 700;">true</span>,
        <span style="color: green; font-weight: 700;">"tty"</span>: <span style="color: rgb(170, 34, 255); font-weight: 700;">true</span>,
        <span style="color: green; font-weight: 700;">"terminationMessagePolicy"</span>: <span style="color: rgb(187, 68, 68);">"File"</span>
    }]
}</code></pre></div>
</details>

<details>
<summary>
<b>Kubernetes replication controller ensures</b>
</summary>
a specific number of pod replicas are running at any one time across nodes
</details>

<details>
<summary>
<b><div style="">What will happen to ReplicaSet pods inside a node when that node gets deleted?</div></b>
</summary>
These pods will be replaced on another node(s)

<img src="paste-69330a78781544cb8771f0f33692134d36fa2003.jpg">
</details>

<details>
<summary>
<b>kube-controller-manager</b>
</summary>
Daemon controlling core K8S control loops<div>
</div><div>Node controller</div><div>Replication controller</div><div>Service account controller</div><div>Endpoints controller
<div>Garbage collector (can be disabled)
</div><div>
</div><div>HPA
</div><div>Leader election</div><div><div>Reconcilliation interval</div></div><div><div>Feature gates</div></div><div><div>Cluster CIDR</div><div>Pod CIDR</div></div></div>
</details>

<details>
<summary>
<b>List processes running on every Kubernetes Master</b>
</summary>
1. kube-apiserver
2. kube-controller-manager
3. kube-scheduler

<img src="paste-d842301571ce981466b41d198776a3b6b0df20e8.jpg">
</details>

<details>
<summary>
<b>Kubernetes Master</b>
</summary>
<div><div>kube-controller-manager
kube-apiserver<div>kube-scheduler</div></div><div>
</div>Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

