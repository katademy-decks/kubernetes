# Network 

<details>
<summary>A Kubernetes resource that exposes deployments.</summary>
Services
<br></details><details>
<summary>Which <b>type </b>of Service makes it only reachable from within the cluster?</summary>
<b>ClusterIP </b>(default ServiceType)
<br></details><details>
<summary>Can you set up a DNS service for your Kubernetes cluster?</summary>
You almost always should. Ex.: CoreDNS
<br></details><details>
<summary>The _____ is the only way to access ExternalName Services.</summary>
Kubernetes&nbsp;DNS server
<br></details><details>
<summary>The service type that&nbsp;<span style="color: rgb(34, 34, 34);">exposes a Service on a cluster-internal IP, making it only reachable from within the cluster is _____</span></summary>
ClusterIP
<br></details><details>
<summary>The _____ service type&nbsp;maps the Service to the contents of the _____ field (e.g. foo.bar.example.com), by returning a CNAME record.</summary>
ExternalName
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In order to allow you to choose a port number for your Services, we must ensure that no two Services can collide. Kubernetes does that by allocating each Service its own _____</span></summary>
<span style="color: rgb(34, 34, 34);">IP address.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">_____ exposes HTTP and HTTPS routes from outside the cluster to services</span><span style="color: rgb(34, 34, 34);">&nbsp;within the cluster. Traffic routing is controlled by rules defined on the _____ resource.</span></summary>
Ingress
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In some cases, multiple paths within an Ingress will match a request. In those cases precedence will be given first to the _____.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">longest matching path</span>
<br></details><details>
<summary>Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should reference an _____ that contains additional configuration including the name of the controller that should implement it.</summary>
IngressClass&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You may deploy any number of Ingress controllers</span><span style="color: rgb(34, 34, 34);">&nbsp;within a cluster. When you create an ingress, you should annotate each ingress with the appropriate _____&nbsp;</span><span style="color: rgb(34, 34, 34);">to indicate which ingress controller should be used if more than one exists within your cluster.</span></summary>
ingressClass
<br></details><details>
<summary>Can NetworkPolicies conflict each other?</summary>
No - they are additive.&nbsp;<span style="color: rgb(34, 34, 34);">&nbsp;If any policy or policies select a pod, the pod is restricted to what is allowed by the union of those policies' ingress/egress rules.</span>
<br></details><details>
<summary>By default, a Pod's hosts file includes...</summary>
localhost, hostname and IPv4/IPv6 boilerplates.
<br></details><details>
<summary>Can a Pod have a single IPv4 and IPv6 address assigned?</summary>
Yes - via enabling IPv4/IPv6 dual-stack.
<br></details><details>
<summary>A node's _____ tell an incoming packet where in the node to go.</summary>
iptables
<br></details><details>
<summary>The _____ service type exposes the Service externally using a cloud provider’s load balancer.</summary>
LoadBalancer
<br></details><details>
<summary>The .spec.____ field is a preference-order list of Node labels, which will be used to sort endpoints when accessing this Service. Traffic will be directed to a Node whose value for the first label matches the originating Node's value for that label. If there is no backend for the Service on a matching Node, then the second label will be considered, and so forth, until no labels remain.</summary>
topologyKeys
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In an Ingress, if two paths are still equally matched by a request, precedence will be given to paths with the _____ path type over _____ path type.</span></summary>
exact
prefix
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">.spec._____&nbsp;</span><span style="color: rgb(34, 34, 34);">adds entries to a Pod's </span>/etc/hosts&nbsp;<span style="color: rgb(34, 34, 34);">file, overriding its hostname resolution when DNS and other options are not applicable.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">HostAliases</span>
<br></details><details>
<summary>What is a Kubernetes Service?</summary>
It's an network connection abstraction which defines a logical set of Pods and a policy to access them.
<br></details><details>
<summary>List possible ServiceTypes for Kubernetes Service</summary>
ClusterIP (default)
NodePort
LoadBalancer
ExternalName
Headless
<br></details><details>
<summary>The LoadBalancer Service creates an external IP address, but itself does not know any Pod IP's. Instead,&nbsp;it chooses a _____ to send packets to.</summary>
Node
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice is full</span><span style="color: rgb(34, 34, 34);">&nbsp;once it reaches _____ endpoints (by default), at which point additional EndpointSlices will be created.</span></summary>
<span style="color: rgb(34, 34, 34);">100</span>
<br></details><details>
<summary>Each of a Service's ports can specify the application protocol to use via the _____ field.</summary>
AppProtocol
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">For some Services, you need to expose more than one port. Kubernetes lets you configure multiple port definitions on a Service object. When using multiple ports for a Service, you must give all of your ports _____ so that these are unambiguous.</span></summary>
<span style="color: rgb(34, 34, 34);">names</span>
<br></details><details>
<summary>Inside a Kubernetes cluster, you might wish to reuse an existing DNS entry, or have legacy systems that are configured for a specific IP address and difficult to re-configure. A Service can specify its own cluster IP address by setting the .spec._____ field.</summary>
clusterIP
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Kubernetes supports 2 primary modes of finding a Service. These are...</span></summary>
<span style="color: rgb(34, 34, 34);">DNS and environment variables.</span>
<br></details><details>
<summary>Headless services are created by setting the Service's .spec._____ field to _____</summary>
clusterIP

"None"
<br></details><details>
<summary>To ensure each Service receives a unique IP, an internal allocator atomically updates a global allocation map in _____ prior to creating each Service.</summary>
etcd
<br></details><details>
<summary>_____ enables a service to route traffic based upon the Node topology of the cluster.&nbsp;</summary>
Service Topology
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.</span></summary>
Ingress controller
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An _____ may be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL / TLS, and offer name based virtual hosting.</span></summary>
<span style="color: rgb(34, 34, 34);">Ingress</span>
<br></details><details>
<summary>An Ingress with no rules sends all traffic to a single _____, which is typically a configuration option of the Ingress Controller&nbsp;and is not specified in your Ingress resources. If none of the hosts or paths match the HTTP request in the Ingress objects, the traffic is routed to it.</summary>
default backend
<br></details><details>
<summary>A _____ uses _____ to specify how groups of pods&nbsp;are allowed to communicate with each other and other network endpoints.</summary>
NetworkPolicy&nbsp;
labels
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Once there is any _____ in a namespace selecting a particular pod, that pod will reject any connections that are not allowed by it.</span></summary>
<span style="color: rgb(34, 34, 34);">NetworkPolicy</span>
<br></details><details>
<summary>The kubelet manages the _____ file for each container of a Pod to prevent Docker from modifying it.</summary>
hosts
<br></details><details>
<summary>The Kubernetes LoadBalancer service works on OSI Layer _____</summary>
4
<br></details><details>
<summary>In a LoadBalancer service, the _____ annotation removes the double-hop problem by allowing users to define their own balancing.</summary>
OnlyLocal
<br></details><details>
<summary>Does a Service load balance traffic across multiple Pods?</summary>
Yes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A Service can specify that traffic be preferentially routed to endpoints that are on the same Node as the client, or in the same availability zone by using _____</span></summary>
Service Topology
<br></details><details>
<summary>Containers within a single pod share network resources - _____ and _____</summary>
IP address and port space
<br></details><details>
<summary>The _____ service type exposes the Service on each Node’s IP at a static port. A ClusterIP Service, to which the it routes, is automatically created.&nbsp;</summary>
NodePort
<br></details><details>
<summary>A _____ is an abstract way to expose on the network an application running on a set of Pods.</summary>
service
<br></details><details>
<summary>A <b>Service </b>can map any incoming port to a _____. By default and for convenience, it has the same value as the port field.</summary>
targetPort
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">_____</span><span style="color: rgb(34, 34, 34);">&nbsp;provide a more scalable alternative to Endpoints, distributing network endpoints across multiple resources.</span></summary>
EndpointSlices
<br></details><details>
<summary>Every node in a Kubernetes cluster runs a _____, responsible for implementing a form of virtual IP for Services of type other than ExternalName.</summary>
kube-proxy
<br></details><details>
<summary>When you don't need load-balancing and a single Service IP, you can create _____</summary>
headless services
<br></details><details>
<summary>A Service for with no ClusterIP, proxying, load-balancing, nor handled by kube-proxy is called _____</summary>
headless
<br></details><details>
<summary>The _____ service type exposes a Service on each Node's IP at a static port.</summary>
NodePort
<br></details><details>
<summary>The _____ service type&nbsp;exposes the Service externally using a cloud provider's load balancer.</summary>
LoadBalancer
<br></details><details>
<summary>You can control Service traffic routing by specifying the .spec._____&nbsp;field.&nbsp;</summary>
topologyKeys&nbsp;
<br></details><details>
<summary>EndpointSlices support three address types:</summary>
IPv4, IPv6, FQDN (Fully Qualified Domain Name)
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice's Endpoints can contain labels about its topology information, such as...</span></summary>
Node - kubernetes.io/hostnameZone - topology.kubernetes.io/zoneRegion - topology.kubernetes.io/region
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can secure an Ingress by specifying a</span><span style="color: rgb(34, 34, 34);">&nbsp;Secret&nbsp;</span><span style="color: rgb(34, 34, 34);">that contains a TLS _____ and _____.</span></summary>
<span style="color: rgb(34, 34, 34);">private key and certificate</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An Ingress TLS secret must contain keys named&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;that contain the certificate and private key to use for TLS.</span></summary>
<code>tls.crt</code><span style="color: rgb(34, 34, 34);">&nbsp;and&nbsp;</span><code>tls.key</code>
<br></details><details>
<summary>Are Pods network-isolated?</summary>
<span style="color: rgb(34, 34, 34);">Pods can become isolated by having a <b>NetworkPolicy </b>that selects them. By default, they accept traffic from any source.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">For TLS, the Ingress object currently only supports the port 443, and assumes TLS _____.&nbsp;</span></summary>
termination
<br></details><details>
<summary>_____ resources route requests to different services, depending on a set of rules, for example, matching parts of the request URL. They can also terminate TLS connections for your application.</summary>
Ingress
<br></details><details>
<summary>The NodePort type is an extension of the _____ type. So a NodePort service also has a _____ address.</summary>
ClusterIP
<br></details><details>
<summary>The LoadBalancer service type is an extension of the _____ type. A LoadBalancer Service has a clusterIP address and one or more _____ values.</summary>
NodePort
<br></details>