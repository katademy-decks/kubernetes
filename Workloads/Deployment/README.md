# Deployment 

<details>
<summary>
what is rolling deployment?
</summary>
approach when you deploy your containers to production hosts one at a time, so your app keeps running.Centurion can do this
</details>

<details>
<summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600;">You just deployed an application on Kubenetes Engine and would like to verify that its deployment is operational.&nbsp; What command could you use?</span>
</summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px;">kubectl get service app</span>
</details>

<details>
<summary>
<span style="color: rgb(41, 48, 59); font-family: &quot;Open Sans&quot;, &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 15px; font-weight: 600; background-color: rgb(242, 243, 245);">You just rolled out a new Kubenetes deployment. After the rollout completes you want to view the deployment. What is the command to list the deployments?</span>

</summary>
kubectl get deployments
</details>

<details>
<summary>
Create a deployment called foo using image 'dgkanatsios/simpleapp' (a simple server that returns hostname) and 3 replicas. Label it as 'app=foo'. Declare that containers in this pod will accept traffic on port 8080 (do NOT create a service yet)
</summary>
Don't use the <i>--expose </i>flag, so we don't create a service.
Leaving out the <i>--restart </i>flag creates a deployment.
<i>kubectl run foo --image=dgkanatsios/simpleapp --labels=app=foo --port=8080 --replicas=3</i>
</details>

<details>
<summary>
Get the IPs of the "foo" deployment. Create a temp busybox pod and try hitting them on port 8080
</summary>
Getting pods with <i>-o wide</i>&nbsp;will show IPs:
<i>kubectl get pods -l app=foo -o wide</i><div><i>
</i></div><div>Start an interactive session to use wget:</div><div><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh

</i></div><div><i>wget -O- &lt;PodIP&gt;:8080</i></div><div><i>exit</i></div>
</details>

<details>
<summary>
Create a service that exposes the "foo" deployment on port 6262. Verify its existence, check the endpoints
</summary>
<i>kubectl expose deploy foo --port=6262 --target-port=8080</i><div><i>kubectl get service foo</i></div><div><i>kubectl get endpoints foo</i></div>
</details>

<details>
<summary>
Create an nginx deployment of 2 replicas, expose it via a ClusterIP service on port 80. Create a NetworkPolicy so that only pods with labels 'access: true' can access the deployment and apply it
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
Command to update a Kubernetes deployment that was created with the `kubectl create` command.
</summary>
`kubectl apply`
</details>

<details>
<summary>
The command to list Kubernetes deployments.
</summary>
`kubectl get deployments`
</details>

<details>
<summary>
<div style="">Provide command to list all Kubernetes deployments in the namespace</div>
</summary>
kubectl get deployments

*<img src="YBEIFyh1TJpMc6vPYvSIj1qYC7tpnKnbKwBu0fC0q2uCaJ7Y_676eSkGUtFlIArUQEnv31_SpyTi-zY3-DbxXHKF82naqWuJrc9AaCYds1muVXWZkTSm755qgZ514rM8eT6c.png">*

</details>

<details>
<summary>
In terms of functionality, which Kubernetes entity is more complex - Deployment or ReplicaSet?
</summary>
*Deployment*

*<img src="SE2xr9beiMR_1xUeEEqR5-Omfbt9BpnFnB7xURtkppxc_JnYNuG3zVqaszIsu6N-LTutLcvzSM68ZH9nxUBsRXikgTKQHyoB0241XQsV-CP_tv3KY-CK38WQT6Lufkcycf5T.png">*

</details>

<details>
<summary>
How to compare with Kubernetes live with manifest configuration
</summary>
kubectl diff&nbsp;(see&nbsp;“Diffing Resources”)
<div>kubectl diff -f deployment.yaml

&gt;&gt; - replicas: 10 
&lt;&lt; + replicas: 5
</div>
</details>

<details>
<summary>
Running busybox Containers for Troubleshooting

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
What is&nbsp;Deployments?
</summary>
* Supervisor program, which continually checks that the container is running, and if it ever stops, starts it again immediately.<div>* On traditional servers, you can use a tool like&nbsp;systemd,&nbsp;runit, or&nbsp;supervisord&nbsp;to do this; On Kubernetes, it is Deployment
* Kubernetes&nbsp;creates a corresponding Deployment object for each pods</div><div>&nbsp; * Deployment records some information about the program:&nbsp;</div><div>&nbsp; * Name of the container image</div><div>&nbsp; *&nbsp;The number of replicas you want to run</div><div>&nbsp; * Whatever else it needs to know to start the container.</div>
</details>

<details>
<summary>
Deployment, Controller with replicaset
</summary>
* Deployment doesn’t manage replicas directly: instead, it automatically creates an associated object called a ReplicaSet, which handles that. We’ll talk more about ReplicaSets in a moment in&nbsp;“ReplicaSets”
* Working together with the&nbsp;Deployment resource is a kind of&nbsp;Kubernetes object called a&nbsp;<em>controller</em>. Controllers watch the resources they’re responsible for, making sure they’re present and working. If a given Deployment isn’t running enough replicas, for whatever reason, the controller will create some new ones.

</details>

<details>
<summary>
kubectl rollout pause
</summary>
<div>Mark the provided *deployment* as paused, not to be reconciled by a controller.&nbsp;</div><div>
</div><div>*kubectl rollout resume&nbsp;*</div>
</details>

<details>
<summary>
kubectl scale
</summary>
<div>Set a new size for a Deployment, ReplicaSet, Replication Controller, or StatefulSet.</div><div>
</div><div>Allows one or more preconditions for the scale action.</div><div>
</div><div>If --current-replicas or --resource-version is specified, it is validated before the scale is attempted, and it is guaranteed that the precondition holds true when the scale is sent to the server.</div><div>
</div><div>--replicas=N</div><div>
</div><div>--timeout=Ns</div><div>Time to wait before giving up on a scaling (0 - don't wait)</div>
</details>

<details>
<summary>
kubectl set env
</summary>
<div>kubectl set env deployment/sample-build foo-bar
</div><div>
</div><div>kubectl set env deployment/sample-build --list</div>
</details>

<details>
<summary>
deployment.spec.replicas
</summary>
Numer of desired pods
</details>

<details>
<summary>
deployment.spec.revisionHistoryLimit
</summary>
Number of old ReplicaSets to retain for rollback
</details>

<details>
<summary>
deployment.spec.selector
</summary>
Label selector for pods<div>
</div><div>Must match pod template labels</div>
</details>

<details>
<summary>
deployment.spec.strategy
</summary>
*Recreate*<div>*
*</div><div>*RollingUpdate*</div><div>maxSurge: max number / percentage of pods that can be scheduled above the desired number of pods</div><div>
</div><div>maxUnavailable: max number of pods that can be unavailable during the update</div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span>
</summary>
*Deployment *or* Replicaset*&nbsp;<div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">a workload object that provides a set of stateless replicas.</span></div>
</details>

<details>
<summary>
Export a running deployment to a file
</summary>
kubectl get deploy nginx -o yaml --export > deployment.yaml

</details>

<details>
<summary>
Check how the nginx deployment rollout is going
</summary>
<i>kubectl rollout status deploy nginx</i>
</details>

<details>
<summary>
Check the rollout history for the nginx deployment
</summary>
<i>kubectl rollout history deploy nginx</i>
</details>

<details>
<summary>
Pause the rollout of the nginx deployment
</summary>
<i>kubectl rollout pause deploy nginx</i>
</details>

<details>
<summary>
Update the image of the nginx deployment to 1.7.9
</summary>
<i>kubectl set image deploy nginx nginx=nginx:1.7.9</i>
or
<i>kubectl edit deploy nginx&nbsp;</i>
and change the image field in YAML

Kubectl set image command is
<i>kubectl set image &lt;type&gt; &lt;name&gt; &lt;container_name&gt;=&lt;container_image&gt;</i>
</details>

