# Network 

<details>
<summary>
<b>A Kubernetes resource that exposes deployments.</b>
</summary>
Services
</details>

<details>
<summary>
<b>What is a Kubernetes Service?</b>
</summary>
It's an abstraction which defines a logical set of Pods and a policy to acces them


<img src="paste-e82468366eccc0c0dfc017a1d05d4409d382138b.jpg">
<img src="paste-41692f1c96c820c7b1799b317dbf422210327b46.jpg">
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
<b>What is ClusterIP in Kubernetes?</b>
</summary>
Service type, which exposes the service on a cluster-internal IP address. Choosing this method makes the service reachable only from within the cluster.
<b><img src="LrIJFiLam2cpkcf5myVNScFXQXKuDfEwd0xSotjkLa7jqoX8JfB7LoKGcD4iEw4qlhg24NI7Jm-3jL73NszW-cek7bmMVY2vyjjUyGTb-9hEjUO2ipOf7gaMbnekRZP6Bmr5.png">
</b><b><img src="5wuy9L_oMBJcBsPsIwmD59ILSh7-t3ZNBKfhVkLapEWie2EGwgVThhPvePn4mGV_7ZCHNX8rWU2lbtoVuUC1kP23qsXGxYg_Z1ByEveznrWNR0vuezgVZCZSL4HSvLgtMtbY.png"></b>
</details>

<details>
<summary>
<b>Describe Service type LoadBalancer&nbsp;</b>
</summary>
LoadBalancer exposes the Service externally using a cloud provider’s load balancer
<img src="QnnXx8MGILXDCYsLAdngTctLUdjhhzbX9PRWiUfDI2UhhBMhYiWU-0Ysi-sitiPhgLNqp6wBPXHl9AAjL76Ov6_GgikVnJojpvi1UL_2NCZ-REKjEa_5cE20ckCHOdv7zZ1x.png">
<img src="paste-b61642fa022fc52b5b490f29808fa0fa4061f4c7.jpg">
</details>

<details>
<summary>
<b>Describe Service type NodePort</b>
</summary>
NodePort exposes the Service on each Node’s IP at a static port (the NodePort). 
A ClusterIP Service, to which the NodePort Service routes, is automatically created.&nbsp;

<b><img src="rAgf9__TwBFmrVUEUQ8lTsqkCFom_JxHss_iNB8eeZYIBGOW_rbIx4fZCr2S-glINvZNXzsY5q4OrT5VsjO4YxcOIrvHQsesmXb9XUQKEa0tY0IC-gxj4xAbbH1l5hB8YPJ6.png">
</b><b><img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png"></b>
</details>

<details>
<summary>
<b>Which Kubernetes entity does this picture represent?
<img src="paste-83b64e7181e7ef9182c3107e228e930f9a8beca3.jpg"></b>
</summary>
NodePort Service

<b><img src="wK72ivZjNj6rt3AnkJgElc45Z12JhbUL1HkUIlM3XZdoGosqFZedTSbPMhHqrRbJzHcR3Sy0jAwk90lhARxQnIckVKPZF_0g80AUSfA-2pPDvpUA2pl7ur7z6baDnlIEXP6s.png"></b>
</details>

<details>
<summary>
<b>Which Kubernetes ServiceType does this picture represent?

<b><img src="8zMkWcUy-sQVvHu6EEgij-3E3MHgiG2OuGoKp6l88A2O-HQTo-OieuBw-5cjrmUAabVmjFYDkxoPxnccOBtwlR57iqlwtzW49febM9ghA480pvFdSILE7J1_zmJQi4qGyv__.png"></b></b>
</summary>
<b>ClusterIP</b>
<b><img src="3FVc5EVpg7WzzWdGMov51g7LWETGHx5-Kv0Qt1Ti0VRXgHCHFA3EV1AIknarjMZIBfULfE9-UGbwJZyXUoxu3qs-qN1dUd436c6KqZ_JkvtsfLbolO2QW27cFPyt6UbMkx7d.png">
</b><b><img src="qCzpNHNAC2mCuaACHwq4u69BN05-Hfpwk4nvK6cbVV7WoiJlq8ak4clCabIpdgv_T0kumUklOv-qEGnVXnS-Y3dOqrr_ohT6sGM-ge7p6veBNytk8JJLCMjXPnxxTTQZFdnm.png"></b>
</details>

<details>
<summary>
<b>A _____ is an abstract way to expose an application running on a set of Pods.</b>
</summary>
service
</details>

<details>
<summary>
<b>Each Pod gets its own IP address, however in a Deployment, the set of Pods running in one moment in time could be different from the set of Pods running that application a moment later.
This leads to a problem: if some set of Pods (call them “backends”) provides functionality to other Pods (call them “frontends”) inside your cluster, how do the frontends find out and keep track of which IP address to connect to, so that the frontend can use the backend part of the workload?</b>
</summary>
services
</details>

<details>
<summary>
<b>A <b>Service </b>can map any incoming port to a targetPort. By default and for convenience, the <b>targetPort </b>is set to the same value as the _____ field.</b>
</summary>
port
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____ are an API resource that can provide a more scalable alternative to Endpoints. Although conceptually quite similar to Endpoints, they allow for distributing network endpoints across multiple resources.</span></b>
</summary>
EndpointSlices
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">By default, an EndpointSlice is considered "full" once it reaches _____ endpoints, at which point additional EndpointSlices will be created to store any additional endpoints.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">100</span>
</details>

<details>
<summary>
<b>The _____ field provides a way to specify an application protocol to be used for each Service port.</b>
</summary>
AppProtocol
</details>

<details>
<summary>
<b>Every node in a Kubernetes cluster runs a _____, responsible for implementing a form of virtual IP for Services of type other than ExternalName.</b>
</summary>
kube-proxy
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For some Services, you need to expose more than one port. Kubernetes lets you configure multiple port definitions on a Service object. When using multiple ports for a Service, you must give all of your ports _____ so that these are unambiguous.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">names</span>
</details>

<details>
<summary>
<b>You can specify your own cluster IP address as part of a Service creation request. To do this, set the _____ field -&nbsp;for example, if you already have an existing DNS entry that you wish to reuse, or legacy systems that are configured for a specific IP address and difficult to re-configure.</b>
</summary>
.spec.clusterIP
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Kubernetes supports 2 primary modes of finding a Service. These are...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">DNS and environment variables.</span>
</details>

<details>
<summary>
<b>Can you set up a DNS service for your Kubernetes cluster?</b>
</summary>
Yes, and you almost always should. For example: CoreDNS
</details>

<details>
<summary>
<b>The _____ is the only way to access ExternalName Services.</b>
</summary>
Kubernetes&nbsp;DNS server
</details>

<details>
<summary>
<b>Sometimes you don't need load-balancing and a single Service IP. In this case, you can create _____</b>
</summary>
headless services
</details>

<details>
<summary>
<b>Headless services are created by explicitly specifying _____ in the Service's _____ field.</b>
</summary>
"None"
.spec.clusterIP
</details>

<details>
<summary>
<b>For _____ services, a cluster IP is not allocated, kube-proxy does not handle these Services, and there is no load balancing or proxying done by the platform for them.</b>
</summary>
headless
</details>

<details>
<summary>
<b>The _____ service type&nbsp;<span style="color: rgb(34, 34, 34);">exposes a Service on a cluster-internal IP. Choosing it makes the Service only reachable from within the cluster.&nbsp;</span></b>
</summary>
ClusterIP
</details>

<details>
<summary>
<b>The _____ service type exposes a Service on each Node's IP at a static port.</b>
</summary>
NodePort
</details>

<details>
<summary>
<b>The _____ service type&nbsp;exposes the Service externally using a cloud provider's load balancer.</b>
</summary>
LoadBalancer
</details>

<details>
<summary>
<b>The _____ service type&nbsp;maps the Service to the contents of the _____ field (e.g. foo.bar.example.com), by returning a CNAME record.</b>
</summary>
ExternalName
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In order to allow you to choose a port number for your Services, we must ensure that no two Services can collide. Kubernetes does that by allocating each Service its own _____</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">IP address.</span>
</details>

<details>
<summary>
<b>To ensure each Service receives a unique IP, an internal allocator atomically updates a global allocation map in _____ prior to creating each Service. The map object must exist in the registry for Services to get IP address assignments, otherwise creations will fail with a message indicating an IP address could not be allocated.&nbsp;
In the control plane, a background controller is responsible for creating that map (needed to support migrating from older versions of Kubernetes that used in-memory locking). Kubernetes also uses controllers to check for invalid assignments (eg due to administrator intervention) and for cleaning up allocated IP addresses that are no longer used by any Services.</b>
</summary>
etcd
</details>

<details>
<summary>
<b>_____ enables a service to route traffic based upon the Node topology of the cluster.&nbsp;<span style="color: rgb(34, 34, 34);">For example, a service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone.</span></b>
</summary>
Service Topology
</details>

<details>
<summary>
<b>If your cluster has Service Topology enabled, you can control Service traffic routing by specifying the _____&nbsp;field on the Service spec. This field is a preference-order list of Node labels which will be used to sort endpoints when accessing this Service. Traffic will be directed to a Node whose value for the first label matches the originating Node's value for that label. If there is no backend for the Service on a matching Node, then the second label will be considered, and so forth, until no labels remain.</b>
</summary>
topologyKeys&nbsp;
</details>

<details>
<summary>
<b>EndpointSlices support three address types:</b>
</summary>
IPv4, IPv6, FQDN (Fully Qualified Domain Name)
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Each endpoint within an EndpointSlice can contain relevant topology information. This is used to indicate where an endpoint is, containing information about the corresponding Node, zone, and region. When the values are available, the following Topology labels will be set by the EndpointSlice controller:</span></b>
</summary>
<ul><li>kubernetes.io/hostname&nbsp;- The name of the Node this endpoint is on.</li><li>topology.kubernetes.io/zone&nbsp;- The zone this endpoint is in.</li><li>topology.kubernetes.io/region&nbsp;- The region this endpoint is in.</li></ul>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">By default, EndpointSlices are limited to a size of 100 endpoints each. You can configure this with the </span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;kube-controller-manager&nbsp;</span><span style="color: rgb(34, 34, 34);">flag up to a maximum of 1000.</span></b>
</summary>
--max-endpoints-per-slice
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____ exposes HTTP and HTTPS routes from outside the cluster to services</span><span style="color: rgb(34, 34, 34);">&nbsp;within the cluster. Traffic routing is controlled by rules defined on the _____ resource.</span></b>
</summary>
Ingress
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.</span></b>
</summary>
Ingress controller
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An _____ may be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL / TLS, and offer name based virtual hosting.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Ingress</span>
</details>

<details>
<summary>
<b>An Ingress with no rules sends all traffic to a single _____, which is typically a configuration option of the Ingress Controller&nbsp;and is not specified in your Ingress resources. If none of the hosts or paths match the HTTP request in the Ingress objects, the traffic is routed to it.</b>
</summary>
default backend
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In some cases, multiple paths within an Ingress will match a request. In those cases precedence will be given first to the _____. If two paths are still equally matched, precedence will be given to paths with an _____ path type over _____ path type.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">longest matching path</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">exact</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">prefix</span><span style="color: rgb(34, 34, 34);">
</span>
</details>

<details>
<summary>
<b>Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should specify a class, a reference to an _____ resource that contains additional configuration including the name of the controller that should implement the class.</b>
</summary>
IngressClass&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can secure an Ingress by specifying a</span><span style="color: rgb(34, 34, 34);">&nbsp;Secret&nbsp;</span><span style="color: rgb(34, 34, 34);">that contains a TLS _____. Currently the Ingress only supports a single TLS port, 443, and assumes TLS _____.&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">private key and certificate</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">termination</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An Ingress TLS secret must contain keys named&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;that contain the certificate and private key to use for TLS.</span></b>
</summary>
<code>tls.crt</code><span style="color: rgb(34, 34, 34);">&nbsp;and&nbsp;</span><code>tls.key</code>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Even though health checks are not exposed directly through the Ingress, there exist parallel concepts in Kubernetes such as _____</span><span style="color: rgb(34, 34, 34);">&nbsp;that allow you to achieve the same end result.&nbsp;</span></b>
</summary>
readinessProbes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You may deploy any number of Ingress controllers</span><span style="color: rgb(34, 34, 34);">&nbsp;within a cluster. When you create an ingress, you should annotate each ingress with the appropriate _____&nbsp;</span><span style="color: rgb(34, 34, 34);">to indicate which ingress controller should be used if more than one exists within your cluster.</span></b>
</summary>
ingressClass
</details>

<details>
<summary>
<b>A _____ is a specification of how groups of pods&nbsp;are allowed to communicate with each other and other network endpoints, using&nbsp;_____ to select pods and define rules which specify what traffic is allowed to the selected pods.</b>
</summary>
NetworkPolicy&nbsp;
labels
</details>

<details>
<summary>
<b>Are Pods network-isolated?</b>
</summary>
<span style="color: rgb(34, 34, 34);">Pods can become isolated by having a <b>NetworkPolicy </b>that selects them. By default, they accept traffic from any source.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Once there is any _____ in a namespace selecting a particular pod, that pod will reject any connections that are not allowed by it.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">NetworkPolicy</span>
</details>

<details>
<summary>
<b>Can NetworkPolicies conflict each other?</b>
</summary>
No - they are additive.&nbsp;<span style="color: rgb(34, 34, 34);">&nbsp;If any policy or policies select a pod, the pod is restricted to what is allowed by the union of those policies' ingress/egress rules.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Adding entries to a Pod's </span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;file provides Pod-level override of hostname resolution when DNS and other options are not applicable.&nbsp;</span><span style="color: rgb(34, 34, 34);">You can add these custom entries with the _____ field in PodSpec. Other ways of&nbsp;</span><span style="color: rgb(34, 34, 34);">modification are not suggested because the file is managed by the kubelet and can be overwritten on during Pod creation/restart.</span></b>
</summary>
/etc/hosts
<span style="color: rgb(34, 34, 34);">HostAliases</span>
</details>

<details>
<summary>
<b>By default, a Pod's hosts file includes...</b>
</summary>
localhost, hostname and IPv4/IPv6 boilerplates.
</details>

<details>
<summary>
<b>HostAliases syntax</b>
</summary>
<pre><code><span style="color: rgb(170, 34, 255); font-weight: 700;">apiVersion</span>:<span style="color: rgb(187, 187, 187);"> </span>v1<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">kind</span>:<span style="color: rgb(187, 187, 187);"> </span>Pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">metadata</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>hostaliases-pod<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);"></span><span style="color: rgb(170, 34, 255); font-weight: 700;">spec</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">restartPolicy</span>:<span style="color: rgb(187, 187, 187);"> </span>Never<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">hostAliases</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">ip</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"127.0.0.1"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">hostnames</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(187, 68, 68);">"foo.local"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(187, 68, 68);">"bar.local"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">ip</span>:<span style="color: rgb(187, 187, 187);"> </span><span style="color: rgb(187, 68, 68);">"10.1.2.3"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">hostnames</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(187, 68, 68);">"foo.remote"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(187, 68, 68);">"bar.remote"</span><span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span><span style="color: rgb(170, 34, 255); font-weight: 700;">containers</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">  </span>- <span style="color: rgb(170, 34, 255); font-weight: 700;">name</span>:<span style="color: rgb(187, 187, 187);"> </span>cat-hosts<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">image</span>:<span style="color: rgb(187, 187, 187);"> </span>busybox<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">command</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- cat<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span><span style="color: rgb(170, 34, 255); font-weight: 700;">args</span>:<span style="color: rgb(187, 187, 187);">
</span><span style="color: rgb(187, 187, 187);">    </span>- <span style="color: rgb(187, 68, 68);">"/etc/hosts"</span></code></pre>
</details>

<details>
<summary>
<b>The kubelet manages the _____ file for each container of the Pod to prevent Docker from modifying the file after the containers have already been started.&nbsp;If you make manual changes to the it, those changes are lost when the container exits.</b>
</summary>
hosts
</details>

<details>
<summary>
<b>Can a Pod have a single IPv4 and IPv6 address assigned?</b>
</summary>
Yes - via enabling IPv4/IPv6 dual-stack.
</details>

<details>
<summary>
<b>Endpoint</b>
</summary>
A k8s API object created for you when deploying a service.
Map to pods via selectors.
</details>

<details>
<summary>
<b>What is a headless service?</b>
</summary>
Without a ClusterIP. Directly access pods without a proxy.
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
<b>LoadBalancer Service</b>
</summary>
L4
Creates an external IP address
Only knows node IPs, not pods IPs. It chooses a node to send a packet to.
iptables in the node tells the packet where to actually go.
OnlyLocal annotation removes the double-hop problem by allowing users to define their own balancing.
</details>

<details>
<summary>
<b>Service</b>
</summary>
A group of endpoints (usually pods)
Provides stable Virtual IP address which automatically routes to backend pods.
Clients only need the Virtual IP to connect to, which doesn't change.
</details>

<details>
<summary>
<b>Kube DNS</b>
</summary>
Autoscalable deployment with a static virtual IP.
Servers "A" and "SRV" records to access services and pods
</details>

