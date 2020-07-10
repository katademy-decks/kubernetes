# Kubernetes_Concepts 

<details>
<summary>
Kubernetes Master controls...
</summary>
Kubernetes nodes
</details>

<details>
<summary>
The format used for Kubernetes resource files.
</summary>
YAML
</details>

<details>
<summary>
The name of the Kubernetes Controller that provides declarative updates for pods.
</summary>
Deployments
</details>

<details>
<summary>
The resource for storing sensitive information in Kubernetes.
</summary>
Secrets
</details>

<details>
<summary>
A Kubernetes resource that exposes deployments.
</summary>
Services
</details>

<details>
<summary>
Where do container images need to exist for Kubernetes to work with them?
</summary>
A container registry.
</details>

<details>
<summary>
Kubernetes deployments can be in what states?&nbsp;

</summary>
1.&nbsp;*Progressing*, which means the deployment is in the process of performing a task&nbsp;
2.&nbsp;*Completed*, which means the rollout of containers is complete and all pods are running the latest version of containers&nbsp;
3.&nbsp;*Failed*, which indicates the deployment process encountered a problem it could not recover from&nbsp;&nbsp;

<img src="paste-b161711b323beee4f9321701871a89dbe94c759c.jpg">
<img src="paste-eb67b2c5aa380b7fa66366a34219cd767c81a081.jpg">
<img src="paste-3b99c3b118c2e59529bf12a6a554aa2c5c5bab73.jpg">

</details>

<details>
<summary>
In order to add a node to a cluster, you decide to edit the managed instance group of the cluster and enable autoscaling. Is that a valid approach?

</summary>
No, because you should not manually manage the MIG behind a cluster.
</details>

<details>
<summary>
Which structure must be created before you can monitor a Kubernetes cluster with Stackdriver?

</summary>
A workspace

*<img src="nGFyNMS14MPw03_cnfdIJZ--s-jYpF7pLU2wkUVf9nvvzzflV3U6od1lDT-hHL85uWIqjkJwvn53Aqb2k01Mwi26NW3D0eGInXdh9D2gw9uH7Mr1yFo6jHMw6QhQuZ6YevJQ.png">*

</details>

<details>
<summary>
What's the name of a Kubernetes entity that executes workloads?

</summary>
Node

<img src="paste-2dd3a0d3b489fe0cc29ee86ddb9283470450af35.jpg">

</details>

<details>
<summary>
What is a Kubernetes Service?

</summary>
<div style="">It's an abstraction which defines a logical set of Pods and a policy to acces them


<img src="paste-e82468366eccc0c0dfc017a1d05d4409d382138b.jpg">
<img src="paste-41692f1c96c820c7b1799b317dbf422210327b46.jpg">
</div>
</details>

<details>
<summary>
List functionalities of K8s *Service*
</summary>
1. It exposes Pods to external traffic
2. It provides Load balancing traffic across multiple Pods
3. It allows Pods to die and replicate without impacting the application
<img src="paste-757549a455e7be1b4e5c13d62ef77db0233367a9.jpg">

</details>

<details>
<summary>
List possible ServiceTypes for Kubernetes Service
</summary>
1. ClusterIP (default)
2. NodePort
3. LoadBalancer
4. ExternalName
5. Headless

6. Ingress (*not*&nbsp;technically a ServiceType - it's used to expose multiple services under the same IP adress)

*<img src="0x26uG-Rv4DcK-uh0Vlwsbr9vrbQSXUaSlgy5O5mBgdo50hlKMi7qQ2RSPHV0aqMx4P6M4eP9XLziphq2XFto9E8Wop_CEIysF2i3NgRplcKvohnsc44dVx6af1rRM_FswBx.png">*
<img src="paste-6ee96b90dd90bcc12c5964bf7930e8f4afc8c2d4.jpg">
</details>

<details>
<summary>
Which *type *of Service makes it only reachable from within the cluster?
</summary>
*ClusterIP *(default ServiceType)

<img src="paste-5591abe579a78ac5cfdd8e894ab1f587dc262e40.jpg">

</details>

<details>
<summary>
<div style="">What is a Kubernetes Namespace?</div>
</summary>
<div style="">An abstraction used to support multiple virtual Clusters on the same physical cluster</div>
*<img src="m9Ge4aLkFv8EIStMhDpCp5mPo755jtUpjrdCykDG1_Citr7XFC4eMUkveG2hbJ6sMhsx63Eqtz73CCubJ9Wee2U44cPhKtCz3FWOo8jCT1khDkjFMsPsnlPv5jlYEmWW4CLX.png">
**<img src="MX5J-ddeKxh4Xg18FH9NJm2SfzyHLFZ1xYNqNjWWHJx9j49M43TPh49kRu6WmRLdLPesU22KYlJNImKs-jKd8rSV4-Z1XzUAfokuyLm3aYTZauIDQJSmxDIPrAQEwtWvWU5Q.png">
**<img src="UudM90ng9cbOx-42AN7L81z9Lizrls57-43R28cxJicVXMolOFzGzXgW83JQlhIOiydKaxle93AHcHeqhU24gjMKXMK2s1xOKYcdbAZmz386NAQWjjutSm0ccfmmyRnAoRAT.png">*

</details>

<details>
<summary>
<div style="">What is ClusterIP in Kubernetes?</div>
</summary>
<div style="">Service type, which exposes the service on a cluster-internal IP address. Choosing this method makes the service reachable only from within the cluster.</div>
*<img src="LrIJFiLam2cpkcf5myVNScFXQXKuDfEwd0xSotjkLa7jqoX8JfB7LoKGcD4iEw4qlhg24NI7Jm-3jL73NszW-cek7bmMVY2vyjjUyGTb-9hEjUO2ipOf7gaMbnekRZP6Bmr5.png">
**<img src="5wuy9L_oMBJcBsPsIwmD59ILSh7-t3ZNBKfhVkLapEWie2EGwgVThhPvePn4mGV_7ZCHNX8rWU2lbtoVuUC1kP23qsXGxYg_Z1ByEveznrWNR0vuezgVZCZSL4HSvLgtMtbY.png">*

</details>

<details>
<summary>
<div style="">Describe Service type LoadBalancer&nbsp;</div>
</summary>
<div style="">LoadBalancer exposes the Service externally using a cloud provider’s load balancer</div>
<img src="QnnXx8MGILXDCYsLAdngTctLUdjhhzbX9PRWiUfDI2UhhBMhYiWU-0Ysi-sitiPhgLNqp6wBPXHl9AAjL76Ov6_GgikVnJojpvi1UL_2NCZ-REKjEa_5cE20ckCHOdv7zZ1x.png">
<img src="paste-b61642fa022fc52b5b490f29808fa0fa4061f4c7.jpg">

</details>

<details>
<summary>
<div style="">Describe Service type NodePort</div>
</summary>
<div style=""><div style="">NodePort exposes the Service on each Node’s IP at a static port (the NodePort). 
A ClusterIP Service, to which the NodePort Service routes, is automatically created.&nbsp;

*<img src="rAgf9__TwBFmrVUEUQ8lTsqkCFom_JxHss_iNB8eeZYIBGOW_rbIx4fZCr2S-glINvZNXzsY5q4OrT5VsjO4YxcOIrvHQsesmXb9XUQKEa0tY0IC-gxj4xAbbH1l5hB8YPJ6.png">
**<img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png">*
</div></div>
</details>

<details>
<summary>
<div style="">Which Kubernetes entity does this picture represent?</div>
<img src="paste-83b64e7181e7ef9182c3107e228e930f9a8beca3.jpg">

</summary>
NodePort Service

*<img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png">*

</details>

<details>
<summary>
<div style="">Which Kubernetes ServiceType does this picture represent?

*<img src="8zMkWcUy-sQVvHu6EEgij-3E3MHgiG2OuGoKp6l88A2O-HQTo-OieuBw-5cjrmUAabVmjFYDkxoPxnccOBtwlR57iqlwtzW49febM9ghA480pvFdSILE7J1_zmJQi4qGyv__.png">*
</div>
</summary>
*<div>ClusterIP</div>*
*<img src="3FVc5EVpg7WzzWdGMov51g7LWETGHx5-Kv0Qt1Ti0VRXgHCHFA3EV1AIknarjMZIBfULfE9-UGbwJZyXUoxu3qs-qN1dUd436c6KqZ_JkvtsfLbolO2QW27cFPyt6UbMkx7d.png">
**<img src="qCzpNHNAC2mCuaACHwq4u69BN05-Hfpwk4nvK6cbVV7WoiJlq8ak4clCabIpdgv_T0kumUklOv-qEGnVXnS-Y3dOqrr_ohT6sGM-ge7p6veBNytk8JJLCMjXPnxxTTQZFdnm.png">*

</details>

<details>
<summary>
When was container war was over?
</summary>
By late 2017, the orchestration wars were over, and Kubernetes had won.&nbsp;
Ref:&nbsp;https://learning.oreilly.com/library/view/cloud-native-devops/9781492040750/ch01.html
</details>

<details>
<summary>
What are all 10 tasks K8s can do
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
What is kubernetes is not fit
</summary>
* Database, it has state and replicas (in state)
</details>

<details>
<summary>
kubernetes shell, ps1, log, data-stack-clic-shell
</summary>
kube-ps1 -&nbsp;&nbsp;If you use the&nbsp;bash&nbsp;or&nbsp;zsh&nbsp;shells, there’s a little&nbsp;utility&nbsp;that will add the current Kubernetes context to your prompt.
<div>kube-shell -- provides a pop-up menu of possible completions for each command
</div><div>Click - A more sophisticated Kubernetes terminal experience is provided by&nbsp;Click.</div><div>kubed-sh --&nbsp;&nbsp;pull and run the necessary containers to execute JavaScript, Ruby, or Python programs on your current cluster.&nbsp;
</div><div>Stern -- log tool,&nbsp;Stern tails the logs from all Pods matching a regular expression (for example&nbsp;demo.*). If there are multiple containers within the Pod, Stern will show you log messages from each, prefixed by its name.&nbsp;
</div>
</details>

<details>
<summary>
Resources allowed during exam

</summary>
* https://kubernetes.io/docs/ and its subdomain<div>*&nbsp;https://github.com/kubernetes/</div><div>*&nbsp;https://kubernetes.io/blog/</div>
</details>

<details>
<summary>
cloudnatived/demo:hello deployment spec
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
Image Pull Policy by kubernetes to node

</summary>
* Always pull<div>* Never pull</div><div>* IfNotPresent pull (default)</div>
</details>

<details>
<summary>
How to set environment variablein k8s?
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
How to harden the security of the container?

</summary>
<div>containers:
- name: demo
 &nbsp;image: cloudnatived/demo:hello
* &nbsp;securityContext:
*<strong>&nbsp; &nbsp;<font color="#ab1aff">readOnlyRootFilesystem: true</font></strong>*<font color="#ab1aff">
</font>*</div><div><strong>&nbsp; &nbsp;<i><font color="#ff5d83">runAsNonRoot: true</font></i></strong>*
 &nbsp;&nbsp;&nbsp;runAsUser: 1000*
</div><div>&nbsp; &nbsp;# setuid&nbsp;mechanism can temporarily gain the privileges of the user that&nbsp;<em>owns</em>&nbsp;the binary*
*</div><div>&nbsp; &nbsp;allowPrivilegeEscalation: false
</div><div>&nbsp; &nbsp;capabilities:&nbsp;</div><div>&nbsp; &nbsp; &nbsp;drop: ["all"]&nbsp;</div><div>&nbsp; &nbsp; &nbsp;drop: ["CHOWN", "NET_RAW", "SETPCAP"]&nbsp;</div><div>&nbsp; &nbsp; &nbsp;add: ["NET_ADMIN"]<strong>
</strong></div>
</details>

<details>
<summary>
Volume - storage - emptyDir&nbsp; ephemeral
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
Container restart spec inside manifest - Restart Policies
</summary>
apiVersion: v1
kind: Pod
...
spec:
 &nbsp;restartPolicy: OnFailure|Never|Always

</details>

<details>
<summary>
What Are Labels?

</summary>
* Labels are key/value pairs that are attached to objects, such as pods.
<div>* They don't imply semantics to the core-system</div>
</details>

<details>
<summary>
If two pods required to be on same node, what to do?
</summary>
If the two Pods absolutely must be colocated, put their containers in the same Pod.&nbsp;

</details>

<details>
<summary>
Specify affinity that the&nbsp;server&nbsp;Pod is scheduled on the same node that is also running a Pod labeled&nbsp;cache

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
Why not use pod affinities?
</summary>
* Pod affinities restrict the scheduler’s freedom
*&nbsp;Trading off one application against another.&nbsp;

</details>

<details>
<summary>
Why do you need&nbsp;Pod Controllers?
</summary>
<div>If the container exits for some reason, you have to manually restart it.</div><div>
</div><div>There’s only one replica of your container and no way to load-balance traffic across multiple replicas if you ran them manually.</div><div>
</div><div>If you want highly available replicas, you have to decide which nodes to run them on, and take care of keeping the cluster balanced.</div><div>
</div><div>When you update the container, you have to take care of stopping each running image in turn, pulling the new image and restarting it.</div>
</details>

<details>
<summary>
Horizontal Pod Autoscaler

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
What is Custom resource in Kubernetes?
</summary>
A&nbsp;<em>custom resource</em>&nbsp;is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation. It represents a customization of a particular Kubernetes installation. However, many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.

</details>

<details>
<summary>
Building Your Own Kubernetes Tools, How to list all the pods in your cluster using go?

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
Sample ingress routing?

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
Ingress certificate configuration :: USING EXISTING TLS CERTIFICATES

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
Two ways to configure the pod for dynamic values (password, dns=names)
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
ConfigMaps

</summary>
The ConfigMap is the primary object for storing configuration data in Kubernetes. 
You can supply that data to an application either by creating a file in the Pod, or by injecting it into the Pod’s environment.

</details>

<details>
<summary>
How to Inject configMaps into environment

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
How to Pass an environment variable to entrypoint? Where env varaible derived from configMaps

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
How to create Config Files from ConfigMaps - configmap.yaml?
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
Updating Pods on a Config Change

</summary>
<strong>checksum/config: {{ include (print $.Template.BasePath "/configmap.yaml") . | sha256sum }}</strong>
<div><strong>
</strong></div><div>Deployment template now includes a hash sum of the config settings, if these settings change, then so will the hash.&nbsp;</div><div>When we run&nbsp;pod-name upgrade, POD will detect that the Deployment spec has changed, and restart all the Pods.<strong>
</strong></div>
</details>

<details>
<summary>
Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo
</summary>
Edit standard pod YAML to add volumes with a <i>volumes.secret.secretName </i>value:<div>
</div><div><i>spec:</i></div><div><i>&nbsp; volumes:</i></div><div><i>&nbsp; - name: foo</i></div><div><i>&nbsp; &nbsp; secret:</i></div><div><i>&nbsp; &nbsp; &nbsp; secretName: mysecret2</i></div><div><i>&nbsp; containers:</i></div><div><i>&nbsp; - image: nginx</i></div><div><i>&nbsp; &nbsp; volumeMounts:</i></div><div><i>&nbsp; &nbsp; - name: foo</i></div><div><i>&nbsp; &nbsp; &nbsp; mountPath: /etc/foo</i></div>
</details>

<details>
<summary>
OpenFaaS&nbsp;

</summary>
Function as a service on Kubernetes
</details>

<details>
<summary>
Endpoint
</summary>
A k8s API object created for you when deploying a service.<div>
</div><div>Map to pods via selectors.</div>
</details>

<details>
<summary>
Role
</summary>
A role contains a set of permissions<div>
</div><div>Permissions are additivite (no "deny" rules)</div><div>
</div><div>Role (namespace)</div><div>ClusterRole (cluster)</div><div>
</div><div>rules:</div><div>&nbsp; &nbsp; - apiGroups: [""] # "" = core API group</div><div>&nbsp; &nbsp; &nbsp; resources: ["pods"]</div><div>&nbsp; &nbsp; &nbsp; verbs: ["get", "watch", "list"]</div>
</details>

<details>
<summary>
What is a headless service?
</summary>
Without a ClusterIP. Directly access pods without a proxy.
</details>

<details>
<summary>
How would you improve Kubernetes security
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
What is a Job? What are all the fields to control them?
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
What is ingress?
</summary>
An API object that manages external access to the services in a cluster, typically HTTP.

Ingress can provide load balancing, SSL termination and name-based virtual hosting.

Ingress as a load balancer that sits in front of a Service
Ingress --&gt; Service =&gt; PODs^*

</details>

<details>
<summary>
What are taints and&nbsp;<strong>tolerations</strong>?
</summary>
<em>Taints</em>&nbsp;allow a node to repel a set of Pods, based on certain properties of the node.

</details>

<details>
<summary>
LoadBalancer Service
</summary>
<div>L4</div><div>
</div><div>Creates an external IP address</div><div>
</div><div>Only knows node IPs, not pods IPs. It chooses a node to send a packet to.</div><div>
</div><div>iptables in the node tells the packet where to actually go.</div><div>
</div><div>OnlyLocal annotation removes the double-hop problem by allowing users to define their own balancing.</div>
</details>

<details>
<summary>
Service
</summary>
A group of endpoints (usually pods)<div>
</div><div>Provides stable Virtual IP address which automatically routes to backend pods.</div><div>
</div><div>Clients only need the Virtual IP to connect to, which doesn't change.</div>
</details>

<details>
<summary>
Conditions
</summary>
Latest variable observations of an object's state.

Ready, ContainerReady, lastProbeTime, reason
</font><div><span style="color: rgb(36, 41, 46);">
</span></div><div><span style="color: rgb(36, 41, 46);">Used when the details of an observation are not known apriori known or would not apply to all instances of a given Kind.&nbsp;</span></div></div>
</details>

<details>
<summary>
Flat network space
</summary>
Pods MUST be reachable across Nodes<div>
</div><div>via L2, L3 or overlay</div><div>
</div><div>Each node has a CIDR IP block to give its pods unique IPs.</div>
</details>

<details>
<summary>
Kube DNS
</summary>
<div>Autoscalable deployment with a static virtual IP.</div><div>
</div><div>Servers "A" and "SRV" records to access services and pods</div>
</details>

<details>
<summary>
kube-scheduler
</summary>
Schedules pods on available worker nodes.<div>
</div><div><div>Policy-rich</div><div>Topology-aware,&nbsp;</div><div>Improves impacts availability, performance, and capacity of nodes</div><div>
</div><div>Considers individual / collective resource needs, QoS requirements, hardware/software/policy/affinity constraints, data locality, inter-workload interference, deadlines.</div></div>
</details>

