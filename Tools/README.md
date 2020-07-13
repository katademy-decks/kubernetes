# Tools 

<details>
<summary>
<b><span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600;">You just deployed an application on Kubenetes Engine and would like to verify that its deployment is operational.&nbsp; What command could you use?</span></b>
</summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px;">kubectl get service app</span>
</details>

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
<b><span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600; background-color: rgb(242, 243, 245);">You just rolled out a new Kubenetes deployment. After the rollout completes you want to view the deployment. What is the command to list the deployments?</span></b>
</summary>
kubectl get deployments
</details>

<details>
<summary>
<b>Convert the "nginx" ClusterIP service to NodePort and find the NodePort port. Hit it using Node's IP.</b>
</summary>
<i>kubectl edit svc nginx</i>
change the <i>spec.type </i>value to NodePort
<i>spec:</i><i>&nbsp; type: NodePort</i>
Find the port and IP with
<i>kubectl get svc</i>
then hit the service with
<i>wget -O- &lt;NodeIP&gt;:&lt;Port&gt;</i>
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
<i>kubectl get pods -l app=foo -o wide</i><i>
</i>Start an interactive session to use wget:<i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh

</i><i>wget -O- &lt;PodIP&gt;:8080</i><i>exit</i>
</details>

<details>
<summary>
<b>Create a service that exposes the "foo" deployment on port 6262. Verify its existence, check the endpoints</b>
</summary>
<i>kubectl expose deploy foo --port=6262 --target-port=8080</i><i>kubectl get service foo</i><i>kubectl get endpoints foo</i>
</details>

<details>
<summary>
<b>Create a temp busybox pod and connect via wget to the "foo" service. Verify that each time there's a different hostname returned (deployment with 3 replicas).</b>
</summary>
Get the service ClusterIP
<i>kubectl get svc</i><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh</i>

Once a service is running, you can access it via the service name (DNS)
<i>wget -O- foo:6262
wget -O- &lt;ServiceClusterIP&gt;:6262</i>
</details>

<details>
<summary>
<b>Create an nginx deployment of 2 replicas, expose it via a ClusterIP service on port 80. Create a NetworkPolicy so that only pods with labels 'access: true' can access the deployment and apply it</b>
</summary>
<i>kubectl run nginx --image=nginx --replicas=2 --port=80 --expose</i>
Check the label selector the service uses for the pods with
<i>kubectl describe svc nginx</i><i>
</i>Create a NetworkPolicy YAML with <i>spec.podSelector.matchLabels </i>to assign the policy to the right pods, and <i>ingress.from.podSelector.matchLabels </i>to restrict which pods can access it.

<i>spec:</i><i>&nbsp; podSelector:</i><i>&nbsp; &nbsp; matchLabels:</i><i>&nbsp; &nbsp; &nbsp; run: nginx</i><i>&nbsp; ingress:</i><i>&nbsp; - from:</i><i>&nbsp; &nbsp; - podSelector:</i><i>&nbsp; &nbsp; &nbsp; &nbsp; matchLabels:</i><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; access: 'true'
</i>
(note we need to put quotes around true so it is accepted as a string rather than a bool)
Apply the policy with
<i>kubectl apply -f policy.yaml</i>
</details>

<details>
<summary>
<b>The command for creating a new Kubernetes Secret.</b>
</summary>
`kubectl create secret`
</details>

<details>
<summary>
<b>Create busybox pod with two containers, each one will have the image busybox and will run the 'sleep 3600' command. Make both containers mount an emptyDir at '/etc/foo'.</b>
</summary>
Best way to do this is create a YAML template (single-container pod) and duplicate the container definition (make sure to change the name of the second container).
<i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>
<i>
</i>Add the <i>spec.volumes </i>and the <i>spec.containers.volumeMounts </i>sections to the YAML (make sure to mount in both containers)

emptyDir volume looks like:
<i>spec:
&nbsp; volumes:</i><i>&nbsp; - name: myvol</i><i>&nbsp; &nbsp; emptyDir: {}
</i>
</details>

<details>
<summary>
<b>You have a two-container pod with a shared volume at '/etc/foo' on both containers.
Connect to the second busybox, write the first column of '/etc/passwd' file to '/etc/foo/passwd'. Connect to the first busybox and write '/etc/foo/passwd' file to standard output.</b>
</summary>
Connect to the second container:
<i>kubectl exec -it busybox -c busybox2 -- /bin/sh</i>/etc/passwd is colon delimited, use cut to get the first column<i>cut -f 1 -d ':' /etc/passwd &gt; /etc/foo/passwd</i><i>cat </i><i>/etc/foo/passwd</i><i>exit
</i>
Connect to the first container:
<i>kubectl exec -it busybox -c busybox -- /bin/sh</i>confirm the mounting<i>mount | grep foo</i><i>cat /etc/foo/passwd</i><i>exit</i>
</details>

<details>
<summary>
<b>Create a PersistentVolume from a file and check the PersistentVolumes that exist on the cluster</b>
</summary>
<i>kubectl create -f pv.yaml</i><i>kubectl get pv</i>
</details>

<details>
<summary>
<b>Show that the PersistentVolumeClaims and the PersistentVolumes of the cluster are working.</b>
</summary>
<i>kubectl get pvc</i><i>kubectl get pv</i>Both should show as "Bound"
</details>

<details>
<summary>
<b>Create a busybox pod with command 'sleep 3600', and mount the PersistentVolumeClaim to '/etc/foo'. Connect to the 'busybox' pod, and copy the '/etc/passwd' file to '/etc/foo'.Create a second pod which is identical with the one you just created. Connect to it and verify that '/etc/foo' contains the 'passwd' file.</b>
</summary>
Create a skeleton YAML file with:
<i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>

add <i>spec.containers.volumeMounts </i>as usual and <i>volumes.persistentVolumeClaim.claimName </i>to match the PVC created.

<i>spec:
&nbsp; containers:</i><i>&nbsp; - name: busybox</i><i>&nbsp; &nbsp; volumeMounts:</i><i>&nbsp; &nbsp; - name: myvol</i><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i><i>&nbsp; volumes:</i><i>&nbsp; - name: myvol</i><i>&nbsp; &nbsp; persistentVolumeClaim:</i><i>&nbsp; &nbsp; &nbsp; claimName: mypvc</i>

Create the pod and connect to it
<i>kubectl create -f pod.yaml
kubectl exec busybox -it -- cp /etc/passwd /etc/foo/passwd</i><i>
</i>Change the <i>metadata.name</i> in the <i>pod.yaml </i>to "busybox2" and create the second identical pod.
Connect to it and show the contents of /etc/foo
<i>kubectl exec busybox2 -- ls /etc/foo</i>
</details>

<details>
<summary>
<b>Create a busybox pod with 'sleep 3600' as arguments. Copy '/etc/passwd' from the pod to your local folder.</b>
</summary>
Use the <i>kubectl cp &lt;pod&gt;:&lt;path&gt; &lt;dest&gt; </i>command.

<i>kubectl run busybox --image=busybox --restart=Never -- sleep 3600</i>using "." as the destination to drop it into current folder
<i>kubectl cp busybox:/etc/passwd .</i><i>cat passwd</i>
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
<b>Command to update a Kubernetes deployment that was created with the `kubectl create` command.</b>
</summary>
`kubectl apply`
</details>

<details>
<summary>
<b>The command to get Pod logs in Kubernetes.</b>
</summary>
`kubectl get logs`
</details>

<details>
<summary>
<b>The command to list Kubernetes deployments.</b>
</summary>
`kubectl get deployments`
</details>

<details>
<summary>
<b>Provide CLI command to point kubectl at a cluster gft-cluster-1 in Google Kubernetes Engine (and update a kubeconfig file with appropriate credentials and endpoint information)</b>
</summary>
gcloud container clusters get-credentials gft-cluster-1

<div style="font-weight: bold;"><img src="D2ctKmECtHFyBCGJqIQgWVvZ-DLI0bcMvjwq9ut1-uxKRNvDD8GkaUkfyN1UEt6l8VKOqXydRy5jlFba6v1zmJ_35cig6DbP3BE7YGp2Dz-p0MIsci4B2hn61qhdCiAQlCZH.png">
</details>

<details>
<summary>
<b>Provide command to list all Kubernetes pods in the namespace</b>
</summary>
kubectl get pods

<b><img src="FezLZbLjz3LT7Bln0xYjl6Z10-ai2OT1U9S5LkMmhNtj-0QuEfayELPDmiiVMrzhrdywH9DUsygN-GFkm89DYnmUqp7Q306g7tdiyOkXuHWd6heoI5Ojy8EIDffXyG4NxzFJ.png"></b>
</details>

<details>
<summary>
<b>Provide command to list all Kubernetes deployments in the namespace</b>
</summary>
kubectl get deployments

<b><img src="YBEIFyh1TJpMc6vPYvSIj1qYC7tpnKnbKwBu0fC0q2uCaJ7Y_676eSkGUtFlIArUQEnv31_SpyTi-zY3-DbxXHKF82naqWuJrc9AaCYds1muVXWZkTSm755qgZ514rM8eT6c.png"></b>
</details>

<details>
<summary>
<b>Provide command to show merged kubeconfig settings.</b>
</summary>
kubectl config view

<b><img src="0oTJPvbKuWTMMeQulKyLGTNY2RLARnDCp8zV2j-gIwfOsP7bZnuDrQefu_W2rTDZLULQ8xvesq6KAxLWM8eWcTwPK2Nt-GqTy2buW2SEXiJMUXlUuwjnlyCab3c5v1GAjNow.png"></b>
</details>

<details>
<summary>
<b>What is kubectl?</b>
</summary>
CLI for running commands against Kubernetes clusters<b>
<img src="isELrh5WNHvaPK4BHA8eIJFHKBon5EWZU_8Z16n3bUKaGm2XIEHp2Pk-8pLjEsyFP41Sq-kci93MS5K4mrWQ8bmsQHc5dcY6P9cQQ_UO8rLjCw1L2i7V1QAhyFgb4uoEG_S-.png"></b>
</details>

<details>
<summary>
<b>Run cloud image on windows</b>
</summary>
* kubectl run demo --image=cloudnatived/demo:hello --port=9999 --labels app=demo
<b>*&nbsp;kubectl port-forward deploy/demo 9999:8888
*&nbsp;</b><strong>kubectl get pods --selector app=demo

</strong>Forwarding from 127.0.0.1:9999 -&gt; 8888<strong>
</strong>Now port 9999 on your local machine will be forwarded to port 8888 on the container
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
<b>How to compare with Kubernetes live with manifest configuration</b>
</summary>
kubectl diff&nbsp;(see&nbsp;“Diffing Resources”)
kubectl diff -f deployment.yaml

&gt;&gt; - replicas: 10 
&lt;&lt; + replicas: 5
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
<b>How to execute Commands on Containers</b>
</summary>
kubectl container run --image alpaine --command -- sleep 999kubectl get pods
#NAME READY STATUS RESTARTS AGE&nbsp;#alpine-7fd44fc4bf-7gl4n 1/1 Running 0 4s

kubectl exec -it alpine-7fd44fc4bf-7gl4n /bin/sh
#will run the command in the first container by default, when more than one conainer present
</details>

<details>
<summary>
<b>Running busybox Containers for Troubleshooting</b>
</summary>
kubctl run demo --image cloudnatived/demo:hello --expose --port 8888service "demo" created 
deployment.apps "demo" created

kubectl run nslookup --image=busybox:1.28 --rm -it --restart=Never \ --command -- nslookup demo&nbsp;Server: 10.79.240.10 Address 1: 10.79.240.10 kube-dns.kube-system.svc.cluster.local&nbsp;Name: demo Address 1: 10.79.242.119 demo.default.svc.cluster.local

kubectl run wget --image=busybox:1.28 --rm -it --restart=Never --command -- wget -qO- http://demo:8888
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
<b>A kubernetes context is a combination of a&nbsp;</b>
</summary>
* authenticated user* a cluster (could be more than one, but current cluster by default)* namespace

kubectl config get-contexts
</details>

<details>
<summary>
<b>Contex specfic commands</b>
</summary>
<strong>kubectl config use-context gke</strong>
<strong>kubectl config set-context myapp --cluster=gke --namespace=myapp</strong><strong>
</strong><strong>kubectl config current-context</strong><strong>
</strong><strong>
</strong><strong>kubectx docker-for-desktop</strong> 
Switched to context "docker-for-desktop".
<strong>
</strong><strong>kubectx -</strong> Switched to context "gke". 
<strong>kubectx -</strong> Switched to context "docker-for-desktop".<strong>
</strong>
</details>

<details>
<summary>
<b>kubernetes shell, ps1, log, data-stack-clic-shell</b>
</summary>
kube-ps1 -&nbsp;&nbsp;If you use the&nbsp;bash&nbsp;or&nbsp;zsh&nbsp;shells, there’s a little&nbsp;utility&nbsp;that will add the current Kubernetes context to your prompt.
kube-shell -- provides a pop-up menu of possible completions for each command
Click - A more sophisticated Kubernetes terminal experience is provided by&nbsp;Click.kubed-sh --&nbsp;&nbsp;pull and run the necessary containers to execute JavaScript, Ruby, or Python programs on your current cluster.&nbsp;
Stern -- log tool,&nbsp;Stern tails the logs from all Pods matching a regular expression (for example&nbsp;demo.*). If there are multiple containers within the Pod, Stern will show you log messages from each, prefixed by its name.&nbsp;
</details>

<details>
<summary>
<b>When to&nbsp;use Custom resource in Kubernetes?</b>
</summary>
Use a custom resource (CRD or Aggregated API) if most of the following apply:You want to use Kubernetes client libraries and CLIs to create and update the new resource.You want top-level support from kubectl (for example:&nbsp;kubectl get my-object object-name).You want to build new automation that watches for updates on the new object, and then CRUD other objects, or vice versa.You want to write automation that handles updates to the object.You want to use Kubernetes API conventions like&nbsp;.spec,&nbsp;.status, and&nbsp;.metadata.You want the object to be an abstraction over a collection of controlled resources, or a summarization of other resources.
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
(DEFAULT)
Cascade the deletion of the resources managed by this resource (e.g. Pods created by a ReplicationController).&nbsp;
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
If grace-period=0. immediately remove resources from API and bypass graceful deletion.&nbsp;
May result in inconsistency or data loss and requires confirmation.
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
<b>kubectl rollout&nbsp;</b>
</summary>
Manage the rollout of<ul><li>deployments</li><li>daemonsets</li><li>statefulsets</li></ul>
</details>

<details>
<summary>
<b>kubectl rollout history</b>
</summary>
View previous rollout revisions and configurations.
--version<span style="color: rgb(51, 51, 51); background-color: rgb(176, 196, 222);">See the details, including podTemplate of the revision specified</span>
</details>

<details>
<summary>
<b>kubectl rollout pause</b>
</summary>
Mark the provided <b>deployment</b> as paused, not to be reconciled by a controller.&nbsp;
<b>kubectl rollout resume&nbsp;</b>
</details>

<details>
<summary>
<b>kubectl rollout restart</b>
</summary>
Restart a resource.
</details>

<details>
<summary>
<b>kubectl rollout status</b>
</summary>
Show the status of the rollout.
By default 'rollout status' will watch the status of the latest rollout until it's done. (<b>--watch=true</b>)
Note that if a new rollout starts in-between, then 'rollout status' will continue watching the latest revision.&nbsp;
If you want to pin to a specific revision and abort if it is rolled over by another revision, use <b>--revision=N</b>
</details>

<details>
<summary>
<b>kubectl rollout undo [TYPE NAME]</b>
</summary>
Rollback to a previous rollout revision

<b>--to-revision=N</b>
</details>

<details>
<summary>
<b>kubectl scale</b>
</summary>
Set a new size for a Deployment, ReplicaSet, Replication Controller, or StatefulSet.
Allows one or more preconditions for the scale action.
If --current-replicas or --resource-version is specified, it is validated before the scale is attempted, and it is guaranteed that the precondition holds true when the scale is sent to the server.
--replicas=N
--timeout=NsTime to wait before giving up on a scaling (0 - don't wait)
</details>

<details>
<summary>
<b>kubectl set env</b>
</summary>
kubectl set env deployment/sample-build foo-bar

kubectl set env deployment/sample-build --list
</details>

<details>
<summary>
<b>kubectl set image</b>
</summary>
Update existing container image(s) of:
pod (po), replicationcontroller (rc), deployment (deploy), daemonset (ds), replicaset (rs)
kubectl set image deployment/nginx busybox=busybox nginx=nginx:1.9.1
</details>

<details>
<summary>
<b>kubectl logs POD [-c CONTAINER]</b>
</summary>
Print the logs of a container/resource.
--follow
--tail<table><tbody><tr><td>Lines of recent log file to display.</td></tr><tr></tr></tbody></table>
--since, --since-time<table><tbody><tr><td>Only return logs newer than a relative duration like 5s, 2m, or 3h, or after a specific date. Defaults to all logs.&nbsp;
</td></tr><tr></tr></tbody></table>
--ignore-errorsIf following, allow errors that occur to be non-fatal

--prefixPrefix logs with pod and container name
--timestampsInclude timestamps
</details>

<details>
<summary>
<b>kubectl port-forward POD LOCALPORT:REMOTEPORT</b>
</summary>
Forward one or more local ports to a pod.&nbsp;
<b>--address&nbsp;</b><table><tbody><tr><td>Localhost or IP address(es) to listen on (comma separated). 

When localhost is supplied, kubectl will try to bind on both 127.0.0.1 and ::1 and will fail if neither of these addresses are available to bind.</td></tr><tr></tr></tbody></table>
This command requires the node to have 'socat' installed.
</details>

<details>
<summary>
<b>kubectl command to view a Node's status and other details</b>
</summary>
<b>kubectl describe node &lt;node-name&gt;</b>
</details>

<details>
<summary>
<b>apiserver to kubelet connections are used for</b>
</summary>
Fetching pod logs
<b>kubectl attach</b>'ing into pods
<b>kubectl port-forward</b>'ing into pods
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Cluster managers and hosting providers should use tools which respect Pod Disruption Budgets by calling _____&nbsp;</span><span style="color: rgb(34, 34, 34);">instead of directly deleting pods or deployments</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">An example is the _____ command.</span></b>
</summary>
the Eviction API
kubectl drain
</details>

<details>
<summary>
<b>You are trying to interactively troubleshoot a container.&nbsp;
<code>kubectl exec</code>&nbsp;was insufficient because the container has crashed
The container image is <b>minimal </b>and&nbsp;<b>distroless </b>and doesn't include debugging utilities.
What can you use to troubleshoot?</b>
</summary>
Ephemeral containers
</details>

<details>
<summary>
<b>Restart a pod</b>
</summary>
kubectl&nbsp;get&nbsp;pod&nbsp;PODNAME&nbsp;-n&nbsp;NAMESPACE&nbsp;-o&nbsp;yaml&nbsp;|&nbsp;kubectl&nbsp;replace&nbsp;--force&nbsp;-f&nbsp;-
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">By default, the&nbsp;</span><code>kubectl</code><span style="color: rgb(34, 34, 34);">&nbsp;command-line tool uses parameters from the&nbsp;</span><em>current _____&nbsp;</em><span style="color: rgb(34, 34, 34);">to communicate with the cluster.</span></b>
</summary>
context
</details>

<details>
<summary>
<b>Export a running deployment to a file</b>
</summary>
kubectl get deploy nginx -o yaml --export > deployment.yaml
</details>

<details>
<summary>
<b>Example of Labels usage in commands</b>
</summary>
kubectl get pods --show-labels
kubectl get pod --selector foo=bar
&nbsp;kubectl get pods -l foo!=bar
&nbsp;kubectl get pods -l <em style="">foo notin bar</em>
</details>

<details>
<summary>
<b>kubectl get--export</b>
</summary>
Omit cluster-specific info
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
Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.&nbsp;
Allows serving static content over specified HTTP path.&nbsp;
All incoming data enters through one port and gets forwarded to the remote kubernetes API Server port, except for the path matching the static content path.
--wwwalso serve static files from a given directory
</details>

<details>
<summary>
<b>kubectl config set-credentials</b>
</summary>
Sets a user in kubeconfig
their certsauth providerenvironmentcommand
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
Adds or overwrites the labels on a resource.
</details>

<details>
<summary>
<b>kubectl replace -f FILENAME</b>
</summary>
Replace a resource by filename or stdin.
</details>

<details>
<summary>
<b>kubectl auth reconcile -f rbac-rules.yaml</b>
</summary>
Reconciles rules for&nbsp;Role, RoleBinding, ClusterRole, and ClusterRoleBinding
Missing objects/namespaces are created if required.
Superior to 'applying' RBAC resources as it causes semantically-aware merging of rules and subjects.<b>
</b><b>--remove-extra-permissions</b><b>--remove-extra-subjects</b>Removes extra perms/subjects added to roles
</details>

<details>
<summary>
<b>kubectl top pod</b>
</summary>
Display Resource usage of pods.
--containersPrint usage of containers in a pod
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
Cordons the node then evicts/deletes all pods.
Does not deleted mirror pods or DaemonSet pods (DS controller ignores unschedulable markings)
<b>--ignore-daemonsets</b>Ignore DS managed pods
<b>--force</b>Continue even if there are dangling pods
<b>--delete-local-data</b>Continue even if there are pods with <b>EmptyDir</b>&nbsp;(local data that is removed upon draining)
</details>

<details>
<summary>
<b>kubectl taint (?)</b>
</summary>
kubectl taint NODE KEY=VAL:EFFECT
<b>--overwrite</b>
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
Sets a context entry in kubeconfig
the context namethe userthe namespace
</details>

<details>
<summary>
<b>Kubernetes Master</b>
</summary>
kube-controller-manager
kube-apiserverkube-scheduler
Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

<details>
<summary>
<b>Check the status of the "hello" job</b>
</summary>
<i>kubectl get jobs</i><i>kubectl describe jobs hello</i><i>kubectl logs job/hello</i>
</details>

<details>
<summary>
<b>kubectl ___ --dry-run</b>
</summary>
print the object that would be sent, without sending it.
</details>

<details>
<summary>
<b>kubectl uncordon</b>
</summary>
Mark a node schedulable
</details>

<details>
<summary>
<b>kubectl config use-context</b>
</summary>
Sets the current context in kubeconfig
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
<b>Selectors</b>
</summary>
An expression&nbsp;that matches&nbsp;a label (or set of labels)

<strong>kubectl get pods --all-namespaces --selector app=demo</strong>
</details>

<details>
<summary>
<b>kubectl config&nbsp;set-cluster NAME</b>
</summary>
Sets a cluster entry in kubeconfig
--server
--certificate-authority
</details>

<details>
<summary>
<b>Get a pod's YAML without cluster-specific information</b>
</summary>
use the <i>--export </i>flag<i>kubectl get pod mypod -o yaml --export</i>
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
<b>Resume the paused nginx rollout and verify things start to happen</b>
</summary>
<i>kubectl rollout resume deploy nginx
kubectl rollout history deploy nginx</i>
</details>

<details>
<summary>
<b>Kubeconfig</b>
</summary>
Information about 
clusters, users, authentication
</details>

<details>
<summary>
<b>kubectl patch --patch PATCH</b>
</summary>
Update resource fields using either "json merge" or&nbsp; "strategic merge"
<b>--local</b>If true, patch will operate on the content of the file, not the server-side resource.
</details>

<details>
<summary>
<b>kubectl diff</b>
</summary>
Diff configurations specified by filename or stdin between the current online configuration, and the configuration as it would be if applied.
Output is always YAML.

<b>--server-side</b>Run apply in-cluster, not local
</details>

<details>
<summary>
<b>kubectl attach POD -c container</b>
</summary>
Attach to a container's process.
<b>--stdin</b>Pass stdin to the container
<b>--tty</b>stdin is a tty
</details>

<details>
<summary>
<b>kubectl describe</b>
</summary>
Print a detailed description of the selected resource/group of resources,&nbsp;
Includies events or controllers.&nbsp;
</details>

<details>
<summary>
<b>kubectl top node NODE_NAME</b>
</summary>
Display resource usage of nodes
</details>

<details>
<summary>
<b>kubectl cluster-info dump [--namespaces NAMESPACES]</b>
</summary>
Dumps debug cluster info and pod logs by namespace (default: kube-system)
--all-namespaces--output-directory-o
</details>

<details>
<summary>
<b>Load a configmap "cmvolume" as a volume inside a pod, on the path "/etc/lala". Check this exists on the created pod.</b>
</summary>
Edit pod YAML, need to add <i>spec.volumes </i>and <i>containers.volumeMounts </i>like for loading any volume.

<i>spec:</i><i>&nbsp; volumes:</i><i>&nbsp; - name: myvol
&nbsp; &nbsp; configMap:</i><i>&nbsp; &nbsp; &nbsp; name: cmvolume # name of configmap</i><i>&nbsp; containers:</i><i>&nbsp; - volumeMounts:</i><i>&nbsp; &nbsp; - name: myvol # matches name above</i><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/lala</i><i>
</i>to check path exists on the pod:
<i>kubectl exec -it mypod -- ls /etc/lala</i>
or spawn an interactive session
<i>kubectl exec -it mypod -- /bin/sh</i><i>cd /etc/lala</i><i>ls</i><i>cat var8</i>
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
<b>Create a busybox pod that runs 'ls /notexist'. Determine if there's an error (of course there is), see it.&nbsp;</b>
</summary>
<i>kubectl run mypod --image=busybox --restart=Never -- /bin/sh -c 'ls /notexist'</i>

show that there are errors
<i>kubectl logs mypod</i><i>kubectl describe pod mypod</i>
</details>

<details>
<summary>
<b>kubectl cluster-info</b>
</summary>
Display addresses of
MasterKubeDNSMetrics-Server
Services labelled&nbsp;<b>kubernetes.io/cluster-service=true</b>
</details>

<details>
<summary>
<b>Create a new serviceaccount called 'myuser'</b>
</summary>
<i>kubectl create sa myuser --dry-run -o yaml &gt; serviceaccount.yaml</i>or get a template with
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
<b>Create an nginx pod that uses 'myuser' as a service account</b>
</summary>
<i>kubectl run mypod --image=nginx --restart=Never --serviceaccount=myuser</i>

Or edit pod YAML to add the <i>spec.serviceAccountName </i>value

<i>spec:</i><i>&nbsp; serviceAccountName: myuser</i>
</details>

<details>
<summary>
<b>Create an nginx pod (that includes port 80) with an HTTP readinessProbe on path '/' on port 80.</b>
</summary>
Create the pod including the <i>--port </i>flag<i>kubectl run mypod --image=nginx --restart=Never --port=80 --dry-run -o yaml &gt; pod.yaml</i>

Add the <i>readinessProbe.httpGet </i>section:
<i>spec:</i><i>&nbsp; containers:</i><i>&nbsp; - image: nginx</i><i>&nbsp; &nbsp; readinessProbe:</i><i>&nbsp; &nbsp; &nbsp; httpGet:</i><i>&nbsp; &nbsp; &nbsp; &nbsp; path: /</i><i>&nbsp; &nbsp; &nbsp; &nbsp; port: 80</i>
</details>

<details>
<summary>
<b>Delete the pod "mypod" forcefully with no grace period</b>
</summary>
<i>kubectl delete pod mypod --force --grace-period=0</i>
</details>

<details>
<summary>
<b>kubectl config set</b>
</summary>
Sets a value in kubeconfig
kubectl config set clusters.my-cluster.server https://1.2.3.4
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
Create a resource from a file or from stdin.JSON and YAML formats are accepted.<h3>Usage</h3><code>$ create -f FILENAME</code>
</details>

<details>
<summary>
<b>kubectl get--field-selector</b>
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
<b>kubectl check if an action verb is allowed</b>
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

