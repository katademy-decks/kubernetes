# Network 

<details>
<summary>
<b>The {{c2::NodePort}} type is an extension of the {{c1::ClusterIP}} type. So a service of type {{c2::NodePort}} has a {{c1::cluster IP}} address.
<img src="paste-98292609fa9710f9d58f5ae8b0b04b4a68745a02.jpg"></b>
</summary>

</details>

<details>
<summary>
<b>The {{c1::LoadBalancer}} type is an extension of the {{c2::NodePort}} type. So a Service of this type has a {{c1::cluster IP}} address and one or more {{c2::nodePort}} values.</b>
</summary>

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
<b><span style="color: rgb(34, 34, 34);">Even though health checks are not exposed directly through the Ingress, there exist parallel concepts in Kubernetes such as _____</span><span style="color: rgb(34, 34, 34);">&nbsp;that allow you to achieve the same end result.&nbsp;</span></b>
</summary>
readinessProbes
</details>

<details>
<summary>
<b>A Kubernetes resource that exposes deployments.</b>
</summary>
Services
</details>

<details>
<summary>
<b>Which <b>type </b>of Service makes it only reachable from within the cluster?</b>
</summary>
<b>ClusterIP </b>(default ServiceType)
</details>

<details>
<summary>
<b>Can you set up a DNS service for your Kubernetes cluster?</b>
</summary>
You almost always should. Ex.: CoreDNS
</details>

<details>
<summary>
<b>The _____ is the only way to access ExternalName Services.</b>
</summary>
Kubernetes&nbsp;DNS server
</details>

<details>
<summary>
<b>The service type that&nbsp;<span style="color: rgb(34, 34, 34);">exposes a Service on a cluster-internal IP, making it only reachable from within the cluster is _____</span></b>
</summary>
ClusterIP
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
<b><span style="color: rgb(34, 34, 34);">_____ exposes HTTP and HTTPS routes from outside the cluster to services</span><span style="color: rgb(34, 34, 34);">&nbsp;within the cluster. Traffic routing is controlled by rules defined on the _____ resource.</span></b>
</summary>
Ingress
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In some cases, multiple paths within an Ingress will match a request. In those cases precedence will be given first to the _____.&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">longest matching path</span>
</details>

<details>
<summary>
<b>Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should reference an _____ that contains additional configuration including the name of the controller that should implement it.</b>
</summary>
IngressClass&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You may deploy any number of Ingress controllers</span><span style="color: rgb(34, 34, 34);">&nbsp;within a cluster. When you create an ingress, you should annotate each ingress with the appropriate _____&nbsp;</span><span style="color: rgb(34, 34, 34);">to indicate which ingress controller should be used if more than one exists within your cluster.</span></b>
</summary>
ingressClass
</details>

<details>
<summary>
<b>Can NetworkPolicies conflict each other?</b>
</summary>
No - they are additive.&nbsp;<span style="color: rgb(34, 34, 34);">&nbsp;If any policy or policies select a pod, the pod is restricted to what is allowed by the union of those policies' ingress/egress rules.</span>
</details>

<details>
<summary>
<b>By default, a Pod's hosts file includes...</b>
</summary>
localhost, hostname and IPv4/IPv6 boilerplates.
</details>

<details>
<summary>
<b>Can a Pod have a single IPv4 and IPv6 address assigned?</b>
</summary>
Yes - via enabling IPv4/IPv6 dual-stack.
</details>

<details>
<summary>
<b>A node's _____ tell an incoming packet where in the node to go.</b>
</summary>
iptables
</details>

<details>
<summary>
<b>The _____ service type exposes the Service externally using a cloud provider’s load balancer.</b>
</summary>
LoadBalancer
</details>

<details>
<summary>
<b>The .spec.____ field is a preference-order list of Node labels, which will be used to sort endpoints when accessing this Service. Traffic will be directed to a Node whose value for the first label matches the originating Node's value for that label. If there is no backend for the Service on a matching Node, then the second label will be considered, and so forth, until no labels remain.</b>
</summary>
topologyKeys
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">In an Ingress, if two paths are still equally matched by a request, precedence will be given to paths with the _____ path type over _____ path type.</span></b>
</summary>
exact
prefix
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">.spec._____&nbsp;</span><span style="color: rgb(34, 34, 34);">adds entries to a Pod's </span>/etc/hosts&nbsp;<span style="color: rgb(34, 34, 34);">file, overriding its hostname resolution when DNS and other options are not applicable.&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">HostAliases</span>
</details>

<details>
<summary>
<b>What is a Kubernetes Service?</b>
</summary>
It's an network connection abstraction which defines a logical set of Pods and a policy to access them.
</details>

<details>
<summary>
<b>List possible ServiceTypes for Kubernetes Service</b>
</summary>
ClusterIP (default)
NodePort
LoadBalancer
ExternalName
Headless
</details>

<details>
<summary>
<b>The LoadBalancer Service creates an external IP address, but itself does not know any Pod IP's. Instead,&nbsp;it chooses a _____ to send packets to.</b>
</summary>
Node
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An EndpointSlice is full</span><span style="color: rgb(34, 34, 34);">&nbsp;once it reaches _____ endpoints (by default), at which point additional EndpointSlices will be created.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">100</span>
</details>

<details>
<summary>
<b>Each of a Service's ports can specify the application protocol to use via the _____ field.</b>
</summary>
AppProtocol
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For some Services, you need to expose more than one port. Kubernetes lets you configure multiple port definitions on a Service object. When using multiple ports for a Service, you must give all of your ports _____ so that these are unambiguous.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">names</span>
</details>

<details>
<summary>
<b>Inside a Kubernetes cluster, you might wish to reuse an existing DNS entry, or have legacy systems that are configured for a specific IP address and difficult to re-configure. A Service can specify its own cluster IP address by setting the .spec._____ field.</b>
</summary>
clusterIP
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Kubernetes supports 2 primary modes of finding a Service. These are...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">DNS and environment variables.</span>
</details>

<details>
<summary>
<b>Headless services are created by setting the Service's .spec._____ field to _____</b>
</summary>
clusterIP

"None"
</details>

<details>
<summary>
<b>_____ enables a service to route traffic based upon the Node topology of the cluster.&nbsp;</b>
</summary>
Service Topology
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
<b>A _____ uses _____ to specify how groups of pods&nbsp;are allowed to communicate with each other and other network endpoints.</b>
</summary>
NetworkPolicy&nbsp;
labels
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Once there is any _____ in a namespace selecting a particular pod, that pod will reject any connections that are not allowed by it.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">NetworkPolicy</span>
</details>

<details>
<summary>
<b>The kubelet manages the _____ file for each container of a Pod to prevent Docker from modifying it.</b>
</summary>
hosts
</details>

<details>
<summary>
<b>The Kubernetes LoadBalancer service works on OSI Layer _____</b>
</summary>
4
</details>

<details>
<summary>
<b>In a LoadBalancer service, the _____ annotation removes the double-hop problem by allowing users to define their own balancing.</b>
</summary>
OnlyLocal
</details>

<details>
<summary>
<b>Does a Service load balance traffic across multiple Pods?</b>
</summary>
Yes
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A Service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone by using _____</span></b>
</summary>
Service Topology
</details>

<details>
<summary>
<b>The _____ service type exposes the Service on each Node’s IP at a static port. A ClusterIP Service, to which the it routes, is automatically created.&nbsp;</b>
</summary>
NodePort
</details>

<details>
<summary>
<b>A _____ is an abstract way to expose on the network an application running on a set of Pods.</b>
</summary>
service
</details>

<details>
<summary>
<b>A <b>Service </b>can map any incoming port to a _____. By default and for convenience, it has the same value as the port field.</b>
</summary>
targetPort
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">_____</span><span style="color: rgb(34, 34, 34);">&nbsp;provide a more scalable alternative to Endpoints, distributing network endpoints across multiple resources.</span></b>
</summary>
EndpointSlices
</details>

<details>
<summary>
<b>Every node in a Kubernetes cluster runs a _____, responsible for implementing a form of virtual IP for Services of type other than ExternalName.</b>
</summary>
kube-proxy
</details>

<details>
<summary>
<b>When you don't need load-balancing and a single Service IP, you can create _____</b>
</summary>
headless services
</details>

<details>
<summary>
<b>A Service for with no ClusterIP, proxying, load-balancing, nor handled by kube-proxy is called _____</b>
</summary>
headless
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
<b>You can control Service traffic routing by specifying the .spec._____&nbsp;field.&nbsp;</b>
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
<b><span style="color: rgb(34, 34, 34);">An EndpointSlice's Endpoints can contain labels about its topology information, such as...</span></b>
</summary>
Node - kubernetes.io/hostnameZone - topology.kubernetes.io/zoneRegion - topology.kubernetes.io/region
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">You can secure an Ingress by specifying a</span><span style="color: rgb(34, 34, 34);">&nbsp;Secret&nbsp;</span><span style="color: rgb(34, 34, 34);">that contains a TLS _____ and _____.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">private key and certificate</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">An Ingress TLS secret must contain keys named&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;that contain the certificate and private key to use for TLS.</span></b>
</summary>
<code>tls.crt</code><span style="color: rgb(34, 34, 34);">&nbsp;and&nbsp;</span><code>tls.key</code>
</details>

<details>
<summary>
<b>Are Pods network-isolated?</b>
</summary>
<span style="color: rgb(34, 34, 34);">Pods can become isolated by having a <b>NetworkPolicy </b>that selects them. By default, they accept traffic from any source.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For TLS, the Ingress object currently only supports the port 443, and assumes TLS _____.&nbsp;</span></b>
</summary>
termination
</details>

