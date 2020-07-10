# Workloads 

<details>
<summary>
<b>StatefulSets</b>
</summary>
*&nbsp;Ability to start and stop Pods in a specific sequence.
* Manages disk storage for their Pods, using a VolumeClaimTemplate object that automatically creates a PersistentVolumeClaim>* Each&nbsp;replica in a StatefulSet must be running and ready before Kubernetes starts the&nbsp;next one, and similarly when the StatefulSet is terminated, the replicas will be shut down in reverse order, waiting for each Pod to finish before moving on to the next.
</details>

<details>
<summary>
<b>>StatefulSet is the workload API object used to manage _____</b>
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
<b><span style="color: rgb(34, 34, 34);">StatefulSet pods are created from the same spec, but are _____</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">Each has a persistent identifier that it maintains across any rescheduling.</span></b>
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
<b>An application requires several of the following:><ul><li>Stable, unique network identifiers.</li><li>Stable, persistent storage.</li><li>Ordered, graceful deployment and scaling.</li><li>Ordered, automated rolling updates.</li></ul>>Which workload object could work best?</b>
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
<b><span style="color: rgb(34, 34, 34);">StatefulSets do not provide any guarantees on the termination of pods when a StatefulSet is deleted.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">To achieve ordered and graceful termination of the pods in the StatefulSet, it is possible to...</span></b>
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
<i>kubectl get pods -l app=foo -o wide</i>><i>
</i>>Start an interactive session to use wget:><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh

</i>><i>wget -O- &lt;PodIP&gt;:8080</i>><i>exit</i>
</details>

<details>
<summary>
<b>Create a service that exposes the "foo" deployment on port 6262. Verify its existence, check the endpoints</b>
</summary>
<i>kubectl expose deploy foo --port=6262 --target-port=8080</i>><i>kubectl get service foo</i>><i>kubectl get endpoints foo</i>
</details>

<details>
<summary>
<b>Create an nginx deployment of 2 replicas, expose it via a ClusterIP service on port 80. Create a NetworkPolicy so that only pods with labels 'access: true' can access the deployment and apply it</b>
</summary>
<i>kubectl run nginx --image=nginx --replicas=2 --port=80 --expose</i>
Check the label selector the service uses for the pods with
<i>kubectl describe svc nginx</i>><i>
</i>>Create a NetworkPolicy YAML with <i>spec.podSelector.matchLabels </i>to assign the policy to the right pods, and <i>ingress.from.podSelector.matchLabels </i>to restrict which pods can access it.

<i>spec:</i>><i>&nbsp; podSelector:</i>><i>&nbsp; &nbsp; matchLabels:</i>><i>&nbsp; &nbsp; &nbsp; run: nginx</i>><i>&nbsp; ingress:</i>><i>&nbsp; - from:</i>><i>&nbsp; &nbsp; - podSelector:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; matchLabels:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; access: 'true'
</i>
(note we need to put quotes around true so it is accepted as a string rather than a bool)
Apply the policy with
<i>kubectl apply -f policy.yaml</i>
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
<b>style="">Provide command to list all Kubernetes deployments in the namespace</b>
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
>kubectl diff -f deployment.yaml

&gt;&gt; - replicas: 10 
&lt;&lt; + replicas: 5
</details>

<details>
<summary>
<b>Running busybox Containers for Troubleshooting</b>
</summary>
kubctl run demo --image cloudnatived/demo:hello --expose --port 8888>service "demo" created 
deployment.apps "demo" created

kubectl run nslookup --image=busybox:1.28 --rm -it --restart=Never \ --command -- nslookup demo&nbsp;>Server: 10.79.240.10 Address 1: 10.79.240.10 kube-dns.kube-system.svc.cluster.local&nbsp;>Name: demo Address 1: 10.79.242.119 demo.default.svc.cluster.local>
>
>kubectl run wget --image=busybox:1.28 --rm -it --restart=Never --command -- wget -qO- http://demo:8888
</details>

<details>
<summary>
<b>What is&nbsp;Deployments?</b>
</summary>
* Supervisor program, which continually checks that the container is running, and if it ever stops, starts it again immediately.>* On traditional servers, you can use a tool like&nbsp;systemd,&nbsp;runit, or&nbsp;supervisord&nbsp;to do this; On Kubernetes, it is Deployment
* Kubernetes&nbsp;creates a corresponding Deployment object for each pods>&nbsp; * Deployment records some information about the program:&nbsp;>&nbsp; * Name of the container image>&nbsp; *&nbsp;The number of replicas you want to run>&nbsp; * Whatever else it needs to know to start the container.
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
>Mark the provided <b>deployment</b> as paused, not to be reconciled by a controller.&nbsp;>
><b>kubectl rollout resume&nbsp;</b>
</details>

<details>
<summary>
<b>kubectl scale</b>
</summary>
>Set a new size for a Deployment, ReplicaSet, Replication Controller, or StatefulSet.>
>Allows one or more preconditions for the scale action.>
>If --current-replicas or --resource-version is specified, it is validated before the scale is attempted, and it is guaranteed that the precondition holds true when the scale is sent to the server.>
>--replicas=N>
>--timeout=Ns>Time to wait before giving up on a scaling (0 - don't wait)
</details>

<details>
<summary>
<b>kubectl set env</b>
</summary>
>kubectl set env deployment/sample-build foo-bar
>
>kubectl set env deployment/sample-build --list
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
Label selector for pods>
>Must match pod template labels
</details>

<details>
<summary>
<b>deployment.spec.strategy</b>
</summary>
<b>Recreate</b>><b>
</b>><b>RollingUpdate</b>>maxSurge: max number / percentage of pods that can be scheduled above the desired number of pods>
>maxUnavailable: max number of pods that can be unavailable during the update
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If an application doesn't require any stable identifiers or ordered deployment, deletion, or scaling, you should deploy your application using...</span></b>
</summary>
<b>Deployment </b>or<b> Replicaset</b>&nbsp;><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">a workload object that provides a set of stateless replicas.</span>
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
<b>style="">Explain what DaemonSet and ReplicaSet have in common (and what are the differences)</b>
</summary>
They are both Kubernetes Controllers and they are both related to count of pods inside the cluster.
 style=""><b>
ReplicaSet </b>makes sure that given amount of pods is always running in the cluster (<b>doesn't</b> matter in which worker node they are running!)<img src="paste-3dfda59e415fbe71f6a599a82a877ec60953f322.jpg">

 style="display: inline !important;"><b>DaemonSet </b>makes sure that all (or selected) nodes have a replica of given pod.
In most use cases, the number of nodes will be equal with number of pods<img src="paste-41a44af9a7651900a5b65dbf3ba95a1f3fa4eb3e.jpg">
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
<b>style="">What will happen (by default) to DaemonSet pods inside a node when that node gets deleted?</b>
</summary>
style="">These pods will be garbage collected (deleted) as well<b><img src="lFn2VhS56EQ5e5HzPHY0ouWasNdxi6-R2XEOtnqIpKDTocCA4l-Sg6AfbKXHH9WIS1a8EMnYYEOiGyGJFioK-9qIZIH3sduMAborO6gXiCHw1Umz7OniapkRpRZdEZfQbEXv.png"></b>
</details>

<details>
<summary>
<b><em>what is DaemonSet</em></b>
</summary>
* It runs one instance on *NODE*
* Kubernetes DaemonSets run a&nbsp;<em>daemon</em>&nbsp;container on each node in the cluster.
>* The term&nbsp;<em>daemon</em>&nbsp;traditionally refers to long-running background processes on a server that handle things like logging, so by analogy,&nbsp;
</details>

<details>
<summary>
<b>kubectl rollout&nbsp;</b>
</summary>
>Manage the rollout of<ul><li>deployments</li><li>daemonsets</li><li>statefulsets</li></ul>
</details>

<details>
<summary>
<b>kubectl rollout history</b>
</summary>
>View previous rollout revisions and configurations.>
>--version><span style="color: rgb(51, 51, 51); background-color: rgb(176, 196, 222);">See the details, including podTemplate of the revision specified</span>
</details>

<details>
<summary>
<b>kubectl rollout restart</b>
</summary>
>Restart a resource.
</details>

<details>
<summary>
<b>kubectl rollout status</b>
</summary>
>Show the status of the rollout.>
>By default 'rollout status' will watch the status of the latest rollout until it's done. (<b>--watch=true</b>)>
>Note that if a new rollout starts in-between, then 'rollout status' will continue watching the latest revision.&nbsp;>
>If you want to pin to a specific revision and abort if it is rolled over by another revision, use <b>--revision=N</b>
</details>

<details>
<summary>
<b>kubectl rollout undo [TYPE NAME]</b>
</summary>
Rollback to a previous rollout revision
>
><b>--to-revision=N</b>
</details>

<details>
<summary>
<b>kubectl set image</b>
</summary>
>Update existing container image(s) of:>
>>pod (po), replicationcontroller (rc), deployment (deploy), daemonset (ds), replicaset (rs)>
>kubectl set image deployment/nginx busybox=busybox nginx=nginx:1.9.1
>
>
</details>

<details>
<summary>
<b>>What’s a <b>Pod</b></b>
</summary>
>A&nbsp;<b>Pod </b>is a group of one or more&nbsp;containers with shared storage/network, and a specification for how to run the containers.

<b><img src="m6OgY8HdeAOI59RmeT0Ue6ortvnFbTmq9hg2duJnAKD0WYGQpN1xDCWQ9_fNi3fbYYd4c0FESi-jtoTt2B4W7gsYqaYD2mrHIqt9T8OEItsIIJfKB_5cHdhvG5ULq_TOqCI1.png"></b>
</details>

<details>
<summary>
<b>Create a temp busybox pod and connect via wget to the "foo" service. Verify that each time there's a different hostname returned (deployment with 3 replicas).</b>
</summary>
>Get the service ClusterIP
<i>kubectl get svc</i><i>kubectl run temppod --image=busybox --restart=Never --rm -it -- sh</i>

Once a service is running, you can access it via the service name (DNS)
<i>wget -O- foo:6262
wget -O- &lt;ServiceClusterIP&gt;:6262</i>
</details>

<details>
<summary>
<b>Create busybox pod with two containers, each one will have the image busybox and will run the 'sleep 3600' command. Make both containers mount an emptyDir at '/etc/foo'.</b>
</summary>
Best way to do this is create a YAML template (single-container pod) and duplicate the container definition (make sure to change the name of the second container).>
><i>kubectl run busybox --image=busybox --restart=Never -o yaml --dry-run -- /bin/sh -c 'sleep 3600' &gt; pod.yaml</i>
><i>
</i>>Add the <i>spec.volumes </i>and the <i>spec.containers.volumeMounts </i>sections to the YAML (make sure to mount in both containers)

emptyDir volume looks like:
<i>spec:
&nbsp; volumes:</i>><i>&nbsp; - name: myvol</i>><i>&nbsp; &nbsp; emptyDir: {}
</i>
</details>

<details>
<summary>
<b>You have a two-container pod with a shared volume at '/etc/foo' on both containers.
Connect to the second busybox, write the first column of '/etc/passwd' file to '/etc/foo/passwd'. Connect to the first busybox and write '/etc/foo/passwd' file to standard output.</b>
</summary>
Connect to the second container:
<i>kubectl exec -it busybox -c busybox2 -- /bin/sh</i>>>/etc/passwd is colon delimited, use cut to get the first column><i>cut -f 1 -d ':' /etc/passwd &gt; /etc/foo/passwd</i>><i>cat </i><i>/etc/foo/passwd</i>>><i>exit
</i>
Connect to the first container:
<i>kubectl exec -it busybox -c busybox -- /bin/sh</i>>confirm the mounting><i>mount | grep foo</i>><i>cat /etc/foo/passwd</i>><i>exit</i>
</details>

<details>
<summary>
<b>Create a busybox pod with 'sleep 3600' as arguments. Copy '/etc/passwd' from the pod to your local folder.</b>
</summary>
Use the <i>kubectl cp &lt;pod&gt;:&lt;path&gt; &lt;dest&gt; </i>command.

<i>kubectl run busybox --image=busybox --restart=Never -- sleep 3600</i>>using "." as the destination to drop it into current folder
><i>kubectl cp busybox:/etc/passwd .</i>><i>cat passwd</i>
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
<b>style="">Provide command to list all Kubernetes pods in the namespace</b>
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
kubectl container run --image alpaine --command -- sleep 999>kubectl get pods>
>#NAME READY STATUS RESTARTS AGE&nbsp;>#alpine-7fd44fc4bf-7gl4n 1/1 Running 0 4s
>
>kubectl exec -it alpine-7fd44fc4bf-7gl4n /bin/sh>
>#will run the command in the first container by default, when more than one conainer present
>
</details>

<details>
<summary>
<b>What are PodPresets? Example of PodPresets</b>
</summary>
>PodPresets:<strong>
</strong>>A&nbsp;Pod Preset&nbsp;is an API resource for injecting additional runtime requirements into a Pod at creation time. You use&nbsp;label selectors&nbsp;to specify the Pods to which a given Pod Preset applies.
><strong>
</strong>><strong>
</strong>><strong>Specific Example:</strong>
>Specific Example:

1. Database Administrator provisions a MySQL service for their cluster.
2. Database Administrator creates secrets for the cluster containing the database name, username, and password.
3. Database Administrator creates a PodPreset defining the database &nbsp;&nbsp;port as an environment variable, as well as the secrets. See Examples below for various examples.
4. Developer of an application can now label their pod with the specified Selector the Database Administrator tells them, and consume the MySQL database without needing to know any of the details from step 2 and 3.
</details>

<details>
<summary>
<b>Can PodPresets override POD settings.</b>
</summary>
>PodPresets can’t be used to override a Pod’s own configuration, only to fill in settings which the Pod itself doesn’t specify. A Pod can opt out of being modified by PodPresets altogether, by setting the annotation:podpreset.admission.kubernetes.io/exclude: "true"
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
>(DEFAULT)>
Cascade the deletion of the resources managed by this resource (e.g. Pods created by a ReplicationController).&nbsp;
</details>

<details>
<summary>
<b>kubectl logs POD [-c CONTAINER]</b>
</summary>
Print the logs of a container/resource.>
>--follow>
>--tail><table><tbody><tr><td>Lines of recent log file to display.</td></tr><tr></tr></tbody></table>>
>--since, --since-time><table><tbody><tr><td>Only return logs newer than a relative duration like 5s, 2m, or 3h, or after a specific date. Defaults to all logs.&nbsp;
</td></tr><tr></tr></tbody></table>
>--ignore-errors>If following, allow errors that occur to be non-fatal>
>
>--prefix>Prefix logs with pod and container name>
>--timestamps>Include timestamps
</details>

<details>
<summary>
<b>kubectl port-forward POD LOCALPORT:REMOTEPORT</b>
</summary>
>Forward one or more local ports to a pod.&nbsp;>
><b>--address&nbsp;</b>><table><tbody><tr><td>Localhost or IP address(es) to listen on (comma separated). 

When localhost is supplied, kubectl will try to bind on both 127.0.0.1 and ::1 and will fail if neither of these addresses are available to bind.</td></tr><tr></tr></tbody></table>>
>This command requires the node to have 'socat' installed.
</details>

<details>
<summary>
<b>containers.imagePullPolicy</b>
</summary>
Always>
>Never>
>IfNotPresent
</details>

<details>
<summary>
<b>containers.args</b>
</summary>
Arguments to the entrypoint>
>Default: the image's CMD line>
><font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.command</b>
</summary>
Entrypoint array>
>Not executed in a shell>
>Default: the image's ENTRYPOINT>
><font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.env</b>
</summary>
List of env vars>
><font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.envFrom</b>
</summary>
List of sources to populate env vars>
><font color="#ff0000">CANNOT BE UPDATED</font>
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
Actions to take in response to lifecycle events><b>
</b>><b>postStart</b>>Called after a container is created>
>If it fails, container restarts according to restart policy><b>
</b>><b>preStop</b>
>Called before a container is terminated (not if it crashes/exits)>
><font color="#ff0000">CANNOT BE UPDATED</font>
</details>

<details>
<summary>
<b>containers.livenessProbe</b>
</summary>
Periodic probe of container liveness>
>Restart container if fails>
>>httpGet: request to perform>
>failureThreshold: failures needed to mark probe failed>
>successThreshold: successes needed to mark probe succeeded>
>initialDelaySeconds: seconds before liveness probes begin>
>periodSeconds: how often to probe
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
Ports to expose from container>
>name:>
>protocol:>
>containerPort: #>
>hostIP:>
</details>

<details>
<summary>
<b>containers.readinessProbe</b>
</summary>
Periodic probe of container service readiness.>
>Container removed from svc endpoints if probe fails>
>httpGet: request to perform>
>failureThreshold: failures needed to mark probe failed>
>successThreshold: successes needed to mark probe succeeded>
>initialDelaySeconds: seconds before liveness probes begin>
>periodSeconds: how often to probe
</details>

<details>
<summary>
<b>containers.securityContext</b>
</summary>
Container's security config>
>runAsUser:>
>>>runAsGroup:&nbsp;>
>runAsNonRoot:>
>capabilities:
>
>>privileged:>
>>procMount:>
>>seLinuxOptions:>
>readOnlyRootFilesystem:>
>allowPrivilegeEscalation:
</details>

<details>
<summary>
<b>containers.VolumeMount</b>
</summary>
Mounting of a Volume in a container>
>name: same as volume>
>readOnly:>
>mountPath: Path in the container where the volume is mounted
>
>subPath: Path in the volume to mount in the container>
>subPathExpr:
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
namespaces>
>filesystem volumes
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
to allow Linux capabilities inside the container.>
>----->
>Ex.:>
>accessing devices>network stack manipulation>writing network and volume plugins
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
>Display Resource usage of pods.>
>--containers>Print usage of containers in a pod
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
use the <i>--export </i>flag><i>kubectl get pod mypod -o yaml --export</i>
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
Attach to a container's process.>
><b>--stdin</b>>Pass stdin to the container>
><b>--tty</b>>stdin is a tty
</details>

<details>
<summary>
<b>Load a configmap "cmvolume" as a volume inside a pod, on the path "/etc/lala". Check this exists on the created pod.</b>
</summary>
Edit pod YAML, need to add <i>spec.volumes </i>and <i>containers.volumeMounts </i>like for loading any volume.

<i>spec:</i>><i>&nbsp; volumes:</i>><i>&nbsp; - name: myvol
&nbsp; &nbsp; configMap:</i>><i>&nbsp; &nbsp; &nbsp; name: cmvolume # name of configmap</i>><i>&nbsp; containers:</i>><i>&nbsp; - volumeMounts:</i>><i>&nbsp; &nbsp; - name: myvol # matches name above</i>><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/lala</i>><i>
</i>>to check path exists on the pod:
<i>kubectl exec -it mypod -- ls /etc/lala</i>
or spawn an interactive session
<i>kubectl exec -it mypod -- /bin/sh</i>><i>cd /etc/lala</i>><i>ls</i>><i>cat var8</i>
</details>

<details>
<summary>
<b>Create an nginx pod with a liveness probe that just runs the command 'ls'. Run it, check its probe status, delete it.</b>
</summary>
Add the <i>spec.containers.livenessProbe</i>&nbsp;section to the standard pod YAML:>
><i>spec:</i>><i>&nbsp; containers</i>><i>&nbsp; - image: nginx</i>><i>&nbsp; &nbsp; livenessProbe:</i>><i>&nbsp; &nbsp; &nbsp; exec:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; command:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; - ls</i>
</details>

<details>
<summary>
<b>Modify the liveness probe in the nginx pod so it starts after 5 seconds and probes every 10 seconds.</b>
</summary>
Add the <i>spec.containers.livenessProbe.initialDelaySeconds and .periodSeconds </i>values:

<i>spec:</i>><i>&nbsp; containers:</i>><i>&nbsp; - image: nginx</i>><i>&nbsp; &nbsp; livenessProbe:</i>><i>&nbsp; &nbsp; &nbsp; initialDelaySeconds: 5</i>><i>&nbsp; &nbsp; &nbsp; periodSeconds: 10</i>
</details>

<details>
<summary>
<b>Create a busybox pod that runs 'ls /notexist'. Determine if there's an error (of course there is), see it.&nbsp;</b>
</summary>
<i>kubectl run mypod --image=busybox --restart=Never -- /bin/sh -c 'ls /notexist'</i>

show that there are errors
<i>kubectl logs mypod</i>><i>kubectl describe pod mypod</i>
</details>

<details>
<summary>
<b>Create a pod that mounts the variable "username" from secret "mysecret2" into an env variable called USER</b>
</summary>
edit pod YAML to add the <i>spec.containers.env.valueFrom.secretKeyRef </i>section:

<i>spec:</i>><i>&nbsp; containers:</i>><i>&nbsp; - image: nginx</i>><i>&nbsp; &nbsp; env:</i>><i>&nbsp; &nbsp; - name: USER</i>><i>&nbsp; &nbsp; &nbsp; valueFrom:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; secretKeyRef:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; name: mysecret2</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; key: username</i>
</details>

<details>
<summary>
<b>Create an nginx pod that uses 'myuser' as a service account</b>
</summary>
<i>kubectl run mypod --image=nginx --restart=Never --serviceaccount=myuser</i>

Or edit pod YAML to add the <i>spec.serviceAccountName </i>value

<i>spec:</i>><i>&nbsp; serviceAccountName: myuser</i>
</details>

<details>
<summary>
<b>Create an nginx pod (that includes port 80) with an HTTP readinessProbe on path '/' on port 80.</b>
</summary>
Create the pod including the <i>--port </i>flag><i>kubectl run mypod --image=nginx --restart=Never --port=80 --dry-run -o yaml &gt; pod.yaml</i>

Add the <i>readinessProbe.httpGet </i>section:
<i>spec:</i>><i>&nbsp; containers:</i>><i>&nbsp; - image: nginx</i>><i>&nbsp; &nbsp; readinessProbe:</i>><i>&nbsp; &nbsp; &nbsp; httpGet:</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; path: /</i>><i>&nbsp; &nbsp; &nbsp; &nbsp; port: 80</i>
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
Pending>
>Running>
>Succeeded>
>Failed>
>Unknown
</details>

<details>
<summary>
<b>List all six fields in a <b>PodCondition</b></b>
</summary>
reason>
>status>
>message>
>type>
>lastProbeTime>
>lastTransitionTime
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
>One of the following:><b>
</b>><b>"True"</b>><b>
</b>><b>"False"</b>><b>
</b>>"<b>Unknown"</b>
</details>

<details>
<summary>
<b>The <b>type</b>&nbsp;condition field provides...</b>
</summary>
One of the following:>
><b>PodScheduled</b>>Pod has been scheduled to a node><b>
</b>><b>Ready</b>>Pod is able to serve requests><b>
</b>><b>Initialized</b>>All init containers have started successfully><b>
</b>><b>ContainersReady</b>>All containers in the pod are ready
</details>

<details>
<summary>
<b>>A probe can have one of three results:</b>
</summary>
<b>Success</b>>The Container passed the diagnostic
><b>
</b>><b>Failure</b>>The Container failed the diagnostic><b>
</b>><b>Unknown</b>>The diagnostic failed, so no action should be taken
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
<b>A container does not provide a livenessProbe, a readinessProbe nor a startupProbe>
>What will be the state of each probe of the container?</b>
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
<b>A startupProbe is provided to a container>
>What happens to the other probes?</b>
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
<b><span style="color: rgb(34, 34, 34);">A process in your Container is able to crash on its own whenever it encounters an issue or becomes unhealthy.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">Do you still need a livenessProbe?</span></b>
</summary>
Not necessarily.&nbsp;>
><span style="color: rgb(34, 34, 34);">The kubelet will automatically perform the correct action in accordance with the Pod's&nbsp;</span><code>restartPolicy</code><span style="color: rgb(34, 34, 34);">.</span>
</details>

<details>
<summary>
<b>A container should be killed or restarted if a probe fails. What can be done to achieve this?</b>
</summary>
1. Specify a <b>livenessProbe&nbsp;</b>>
>2. Add a <b>restartPolicy </b>of <b>Always </b>or <b>OnFailure</b>
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
Waiting>
>Running>
>Terminated
</details>

<details>
<summary>
<b>A container is <b>Waiting </b>when...</b>
</summary>
It is neither <b>Running </b>or <b>Terminated</b>>
>A <b>Waiting </b>container still runs operations like pulling images, applying Secrets etc.
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
<b>readinessGates</b>>
>Add it into PodSpec to specify a list of extra conditions for the kubelet to evaluate>
>Ex.:>
><pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
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
</span><span style="color: rgb(187, 187, 187);"></span>...</code></pre>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Readiness gates are determined by the current state of...</span></b>
</summary>
<b>status.condition</b> fields for the Pod>
>If such a field isn't found, the status of the condition defaults to <b>"False"</b>
</details>

<details>
<summary>
<b><b>restartPolicy </b>possible values are...</b>
</summary>
Always>
>Never>
>OnFailure
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
exponential back-off>
>5 minutes
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
<b>A pod has one container. The container exits with <b>success</b>.>
>What happens depending on each possible <b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Succeeded.</li></ul>
</details>

<details>
<summary>
<b>A pod has one container. The container exits with&nbsp;<b>failure</b>.>
>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>>>Pod is running and has two Containers. Container 1 exits with <b>failure</b>.>
>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Do not restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li></ul>><span style="color: rgb(34, 34, 34);">If Container 1 is not running, and Container 2 exits:</span>><ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>>>>Pod is running and has one Container. Container runs <b>out of memory </b>(and terminates in failure)>
>What happens depending on each possible&nbsp;<b>restartPolicy</b>?</b>
</summary>
<ul><li>Always: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>OnFailure: Restart Container; Pod&nbsp;<code>phase</code>&nbsp;stays Running.</li><li>Never: Log failure event; Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li></ul>
</details>

<details>
<summary>
<b>>>>>Pod is running, and a disk dies.>
>What happens?</b>
</summary>
<ul><li>Kill all Containers.</li><li>Log appropriate event.</li><li>Pod&nbsp;<code>phase</code>&nbsp;becomes Failed.</li><li>If running under a controller, Pod is recreated elsewhere.</li></ul>
</details>

<details>
<summary>
<b>>>>>>Pod is running, and its node is segmented out.>
>What happens?</b>
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
<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">podpreset.admission.kubernetes.io/exclude: "true"</span>><span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span>>Add the above annotation in the Pod Spec<span style="color: rgb(34, 34, 34); background-color: rgba(0, 0, 0, 0.05);">
</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can use&nbsp;</span><em>topology spread constraints</em><span style="color: rgb(34, 34, 34);">&nbsp;to control...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">how Pods</span><span style="color: rgb(34, 34, 34);">&nbsp;are spread across your cluster among failure-domains.&nbsp;</span>><span style="color: rgb(34, 34, 34);">(regions, zones, nodes or user-defined domains)</span>
</details>

<details>
<summary>
<b>>>You have a 4-node cluster with the following labels:<pre><code>NAME    STATUS   ROLES    AGE     VERSION   LABELS
node1   Ready    &lt;none&gt;   4m26s   v1.16.0   node=node1,zone=zoneA
node2   Ready    &lt;none&gt;   3m58s   v1.16.0   node=node2,zone=zoneA
node3   Ready    &lt;none&gt;   3m17s   v1.16.0   node=node3,zone=zoneB
node4   Ready    &lt;none&gt;   2m43s   v1.16.0   node=node4,zone=zoneB</code></pre>>What would the cluster logically look like?</b>
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
the degree to which Pods may be unevenly distributed.>
><span style="color: rgb(34, 34, 34);">It's the maximum permitted difference between the number of matching Pods in any two topology domains of a given topology type.</span>
><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">It must be greater than zero.</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b><strong>topologyKey</strong><span style="color: rgb(34, 34, 34);">&nbsp;is...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The key of node labels.&nbsp;</span>
</details>

<details>
<summary>
<b>>><span style="color: rgb(34, 34, 34);">If two Nodes are labelled with one <b>topologyKey </b>and have identical values for that label, the scheduler treats both Nodes as _____</span>>
></b>
</summary>
<span style="color: rgb(34, 34, 34);">Being in the same topology.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">The scheduler tries to place a balanced number of Pods into each topology domain</span><span style="color: rgb(34, 34, 34);">
</span>
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
><b><code>DoNotSchedule</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span></b>><span style="color: rgb(34, 34, 34);">tells the scheduler not to schedule it.</span><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">
</span>><b><code>ScheduleAnyway</code><span style="color: rgb(34, 34, 34);">&nbsp;</span></b><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">tells the scheduler to still schedule it while prioritizing nodes that minimize the skew</span>
</details>

<details>
<summary>
<b>><h3>Example: One TopologySpreadConstraint</h3>>Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre>>If we want an incoming Pod to be evenly spread with existing Pods across zones, the spec can be given as:</b>
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
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/pause:<span style="color: rgb(102, 102, 102);">3.1</span></code></pre><pre><code>><code>topologyKey: zone</code>&nbsp;implies the even distribution will only be applied to the nodes which have label pair "zone:&lt;any value&gt;" present.&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;tells the scheduler to let it stay pending if the incoming Pod can’t satisfy the constraint.>If the scheduler placed this incoming Pod into "zoneA", the Pods distribution would become [3, 1], hence the actual skew is 2 (3 - 1) - which violates&nbsp;<code>maxSkew: 1</code>. In this example, the incoming Pod can only be placed onto "zoneB":<pre><code>+---------------+---------------+      +---------------+---------------+
|     zoneA     |     zoneB     |      |     zoneA     |     zoneB     |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |  OR  | node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
|   P   |   P   |   P   |   P   |      |   P   |   P   |  P P  |       |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
</code></pre>>You can tweak the Pod spec to meet various kinds of requirements:<ul><li>Change&nbsp;<code>maxSkew</code>&nbsp;to a bigger value like "2" so that the incoming Pod can be placed onto "zoneA" as well.</li><li>Change&nbsp;<code>topologyKey</code>&nbsp;to "node" so as to distribute the Pods evenly across nodes instead of zones. In the above example, if&nbsp;<code>maxSkew</code>&nbsp;remains "1", the incoming Pod can only be placed onto "node4".</li><li>Change&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;to&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code>&nbsp;to ensure the incoming Pod to be always schedulable (suppose other scheduling APIs are satisfied). However, it’s preferred to be placed onto the topology domain which has fewer matching Pods. (Be aware that this preferability is jointly normalized with other internal scheduling priorities like resource usage ratio, etc.)<code>topologyKey: zone</code><span style="font-family: Arial;">&nbsp;</span><span style="font-family: Arial;">implies the even distribution will only be applied to the nodes which have label pair "zone:&lt;any value&gt;" present.</span><span style="font-family: Arial;">&nbsp;</span><code>whenUnsatisfiable: DoNotSchedule</code><span style="font-family: Arial;">&nbsp;</span><span style="font-family: Arial;">tells the scheduler to let it stay pending if the incoming Pod can’t satisfy the constraint.</span>>If the scheduler placed this incoming Pod into "zoneA", the Pods distribution would become [3, 1], hence the actual skew is 2 (3 - 1) - which violates&nbsp;<code>maxSkew: 1</code>. In this example, the incoming Pod can only be placed onto "zoneB":<pre><code>+---------------+---------------+      +---------------+---------------+
|     zoneA     |     zoneB     |      |     zoneA     |     zoneB     |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |  OR  | node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
|   P   |   P   |   P   |   P   |      |   P   |   P   |  P P  |       |
+-------+-------+-------+-------+      +-------+-------+-------+-------+
</code></pre>>You can tweak the Pod spec to meet various kinds of requirements:<ul><li>Change&nbsp;<code>maxSkew</code>&nbsp;to a bigger value like "2" so that the incoming Pod can be placed onto "zoneA" as well.</li><li>Change&nbsp;<code>topologyKey</code>&nbsp;to "node" so as to distribute the Pods evenly across nodes instead of zones. In the above example, if&nbsp;<code>maxSkew</code>&nbsp;remains "1", the incoming Pod can only be placed onto "node4".</li><li>Change&nbsp;<code>whenUnsatisfiable: DoNotSchedule</code>&nbsp;to&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code>&nbsp;to ensure the incoming Pod to be always schedulable (suppose other scheduling APIs are satisfied). However, it’s preferred to be placed onto the topology domain which has fewer matching Pods. (Be aware that this preferability is jointly normalized with other internal scheduling priorities like resource usage ratio, etc.)</li></ul></li></ul></code></pre><pre><code><span style="color: rgb(102, 102, 102);">
</span></code></pre>
</details>

<details>
<summary>
<b><h3>Example: Multiple TopologySpreadConstraints<a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/#example-multiple-topologyspreadconstraints"></a></h3>>&nbsp;Suppose you have a 4-node cluster where 3 Pods labeled&nbsp;<code>foo:bar</code>&nbsp;are located in node1, node2 and node3 respectively (<code>P</code>&nbsp;represents Pod):<pre><code>+---------------+---------------+
|     zoneA     |     zoneB     |
+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 |
+-------+-------+-------+-------+
|   P   |   P   |   P   |       |
+-------+-------+-------+-------+
</code></pre>>You can use 2 TopologySpreadConstraints to control the Pods spreading on both zone and node:</b>
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
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>k8s.gcr.io/pause:<span style="color: rgb(102, 102, 102);">3.1</span></code></pre><pre><code>>In this case, to match the first constraint, the incoming Pod can only be placed onto "zoneB"; while in terms of the second constraint, the incoming Pod can only be placed onto "node4". Then the results of 2 constraints are ANDed, so the only viable option is to place on "node4".>Multiple constraints can lead to conflicts. Suppose you have a 3-node cluster across 2 zones:<pre><code>+---------------+-------+
|     zoneA     | zoneB |
+-------+-------+-------+
| node1 | node2 | node3 |
+-------+-------+-------+
|  P P  |   P   |  P P  |
+-------+-------+-------+
</code></pre>>If you apply "two-constraints.yaml" to this cluster, you will notice "mypod" stays in&nbsp;<code>Pending</code>&nbsp;state. This is because: to satisfy the first constraint, "mypod" can only be put to "zoneB"; while in terms of the second constraint, "mypod" can only put to "node2". Then a joint result of "zoneB" and "node2" returns nothing.>To overcome this situation, you can either increase the&nbsp;<code>maxSkew</code>&nbsp;or modify one of the constraints to use&nbsp;<code>whenUnsatisfiable: ScheduleAnyway</code></code></pre><pre><code><span style="color: rgb(102, 102, 102);">
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
<b>bypassed</b>><b>
</b>>This implies that:
><ol><li>the Pods located on those nodes do not impact&nbsp;<code>maxSkew</code>&nbsp;calculation - in the above example, suppose "node1" does not have label "zone", then the 2 Pods will be disregarded, hence the incomingPod will be scheduled into "zoneA".</li><li>the incoming Pod has no chances to be scheduled onto this kind of nodes - in the above example, suppose a "node5" carrying label&nbsp;<code>{zone-typo: zoneC}</code>&nbsp;joins the cluster, it will be bypassed due to the absence of label key "zone".</li></ol>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If the incoming Pod has&nbsp;</span><code>spec.nodeSelector</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>spec.affinity.nodeAffinity</code><span style="color: rgb(34, 34, 34);">&nbsp;defined, nodes not matching them will be...</span></b>
</summary>
bypassed
</details>

<details>
<summary>
<b>>Suppose you have a 5-node cluster ranging from zoneA to zoneC:<pre><code>+---------------+---------------+-------+
|     zoneA     |     zoneB     | zoneC |
+-------+-------+-------+-------+-------+
| node1 | node2 | node3 | node4 | node5 |
+-------+-------+-------+-------+-------+
|   P   |   P   |   P   |       |       |
+-------+-------+-------+-------+-------+
</code></pre>>and you know that "zoneC" must be excluded. In this case, you can compose the yaml as below, so that "mypod" will be placed onto "zoneB" instead of "zoneC". Similarly&nbsp;<code>spec.nodeSelector</code>&nbsp;is also respected.</b>
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
<b><h2>Comparison of Topology with PodAffinity/PodAntiAffinity</h2>>>In Kubernetes, directives related to "Affinity" control how Pods are scheduled - more packed or more scattered.>
><ul><li>For <font face="monospace">_____</font>, you can try to pack any number of Pods into qualifying topology domain(s)</li><li>For&nbsp;<font face="monospace">_____</font>, only one Pod can be scheduled into a single topology domain.</li></ul></b>
</summary>
PodAffinity>
>PodAntiAffinity
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">It is possible to set default topology spread constraints for a cluster.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">Default topology spread constraints are applied to a Pod if, and only if:</span></b>
</summary>
<ul><li>It doesn't define any constraints in its&nbsp;<code>.spec.topologySpreadConstraints</code>.</li><li>It belongs to a service, replication controller, replica set or stateful set.</li></ul>
</details>

<details>
<summary>
<b>>An example <b>KubeSchedulerConfiguration </b>configuration for cluster-level default constraints might look like...</b>
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
<b><span style="color: rgb(34, 34, 34);">A _____ limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions.</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">Ex.:</span>><span style="color: rgb(34, 34, 34);">A quorum-based application would like to ensure that the number of replicas running is never brought below the number needed for a quorum.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">A web front end might want to ensure that the number of replicas serving load never falls below a certain percentage of the total.</span><span style="color: rgb(34, 34, 34);">
</span></b>
</summary>
PodDisruptionBudget
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Cluster managers and hosting providers should use tools which respect Pod Disruption Budgets by calling _____&nbsp;</span><span style="color: rgb(34, 34, 34);">instead of directly deleting pods or deployments</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">An example is the _____ command.</span></b>
</summary>
the Eviction API>
>kubectl drain
</details>

<details>
<summary>
<b>A PodDisruptionBudget&nbsp;<span style="color: rgb(34, 34, 34);">specifies the number of _____ that an application can tolerate having, relative to how many it is intended to have.</span></b>
</summary>
replicas
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">ADeployment has a&nbsp;</span><code>.spec.replicas: 5.&nbsp;</code><span style="color: rgb(34, 34, 34);">It is supposed to have 5 pods at any given time.&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">If its PDB allows for there to be 4 at a time, then the Eviction API will allow voluntary disruption of how many pods at a time?</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">One</span>
</details>

<details>
<summary>
<b>PodDisruptionBudgets cannot prevent involuntary disruptions from occurring.&nbsp;>
>Do involuntary disruptions count against the budget?</b>
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
<b>No</b>>
><span style="color: rgb(34, 34, 34);">The handling of failures during application updates is configured in the controller spec. (Learn about&nbsp;</span><a href="https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment">updating a deployment</a><span style="color: rgb(34, 34, 34);">.)</span>
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
><b>user-initiated actions</b>&nbsp;>Such as troubleshooting and inspecting services
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Sometimes it's necessary to inspect the state of an existing Pod, however, for example to troubleshoot a hard-to-reproduce bug. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">in an existing Pod to _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container&nbsp;</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">inspect its state and run arbitrary commands</span>
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
<span style="color: rgb(34, 34, 34);">the same&nbsp;</span><code>ContainerSpec</code><span style="color: rgb(34, 34, 34);">&nbsp;as regular containers</span>><span style="color: rgb(34, 34, 34);">
</span>><span style="color: rgb(34, 34, 34);">However, many fields are incompatible and disallowed</span>
</details>

<details>
<summary>
<b>>You are trying to interactively troubleshoot a container.&nbsp;>
><code>kubectl exec</code>&nbsp;was insufficient because the container has crashed>
>The container image is <b>minimal </b>and&nbsp;<b>distroless </b>and doesn't include debugging utilities.
>What can you use to troubleshoot?</b>
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
<b><span style="color: rgb(34, 34, 34);">Ephemeral containers are created using the&nbsp;</span><code>ephemeralcontainers</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">subresource of Pod,&nbsp;</span><span style="color: rgb(34, 34, 34);">which can be demonstrated using&nbsp;</span><code>kubectl --raw.</code>><code>
</code>>First describe the ephemeral container to add as an EphemeralContainers list:<code>
</code></b>
</summary>
>{
><pre><code>    <span style="color: green; font-weight: 700;">"apiVersion"</span>: <span style="color: rgb(187, 68, 68);">"v1"</span>,
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
}</code></pre>
</details>

<details>
<summary>
<b>Kubernetes replication controller ensures</b>
</summary>
a specific number of pod replicas are running at any one time across nodes
</details>

<details>
<summary>
<b>style="">What will happen to ReplicaSet pods inside a node when that node gets deleted?</b>
</summary>
These pods will be replaced on another node(s)

<img src="paste-69330a78781544cb8771f0f33692134d36fa2003.jpg">
</details>

