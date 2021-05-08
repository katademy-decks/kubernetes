<details>
<summary>A _____ is like a virtual server on your cluster.</summary>
Service
<br></details>

<details>
<summary>The service type that&nbsp;<span style="color: rgb(34, 34, 34);">exposes a Service on a cluster-internal IP, making it only reachable from within the cluster is _____</span></summary>
ClusterIP
<br></details>

<details>
<summary>The _____ service type&nbsp;maps the Service to the contents of the _____ field (e.g. foo.bar.example.com), by returning a CNAME record.</summary>
ExternalName
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In order to allow you to choose a port number for your Services, we must ensure that no two Services can collide. Kubernetes does that by allocating each Service its own _____</span></summary>
<span style="color: rgb(34, 34, 34);">IP address.</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In some cases, multiple paths within an Ingress will match a request. In those cases precedence will be given first to the _____.&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">longest matching path</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">In an Ingress, if two paths are still equally matched by a request, precedence will be given to paths with the _____ path type over _____ path type.</span></summary>
exact
prefix
<br></details>

<details>
<summary>The 5 possible ServiceTypes for Kubernetes Service are:
_____ - Exposes as an in-cluster IP (default)_____ - Exposes as a port on each node_____ - Exposes externally via your cloud provider's LB_____ - Maps to the contents of the ExternalName, returns a CNAME record with the value_____</summary>
ClusterIP
NodePort
LoadBalancer
ExternalName
Headless
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An EndpointSlice is full</span><span style="color: rgb(34, 34, 34);">&nbsp;once it reaches _____ endpoints (by default), at which point additional EndpointSlices will be created.</span></summary>
<span style="color: rgb(34, 34, 34);">100</span>
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An _____&nbsp;</span><span style="color: rgb(34, 34, 34);">is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.</span></summary>
Ingress controller
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">StatefulSets currently require manually creating a _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to be responsible for the network identity of the Pods.</span></summary>
headless service
<br></details>

<details>
<summary>A Service for with no ClusterIP, proxying, load-balancing, nor handled by kube-proxy is called _____</summary>
headless
<br></details>

<details>
<summary>The _____ service type exposes a Service on each Node's IP at a static port.</summary>
NodePort
<br></details>

<details>
<summary>The _____ service type&nbsp;exposes the Service externally using a cloud provider's load balancer.</summary>
LoadBalancer
<br></details>

<details>
<summary>EndpointSlices support three address types: _____, _____, _____.</summary>
IPv4, IPv6, Fully Qualified Domain Name
<br></details>

<details>
<summary>_____ resources route requests to different services, depending on a set of rules, for example, matching parts of the request URL.&nbsp;</summary>
Ingress
<br></details>

<details>
<summary>The NodePort type is an extension of the _____ type. So a NodePort service also has a _____ address.</summary>
ClusterIP
<br></details>

<details>
<summary>The LoadBalancer service type is an extension of the _____ type. A LoadBalancer Service has a clusterIP address and one or more _____ values.</summary>
NodePort
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____</span><span style="color: rgb(34, 34, 34);">&nbsp;provide a more scalable alternative to Endpoints, distributing network endpoints across multiple resources.</span></summary>
EndpointSlices
<br></details>

<details>
<summary>To ensure each Service receives a unique IP, an internal allocator atomically updates a global allocation map in _____ prior to creating each Service.</summary>
etcd
<br></details>

<details>
<summary>An Ingress with no rules sends all traffic to a single _____, which is typically a configuration option of the Ingress Controller&nbsp;and is not specified in your Ingress resources. If none of the hosts or paths match the HTTP request in the Ingress objects, the traffic is routed to it.</summary>
default backend
<br></details>

<details>
<summary>It takes time for kube-proxy or the Ingress controller to be notified of endpoint changes. Traffic will then remain flowing to a Pod even after its _____. Graceful _____ is required of an app upon its container being sent a SIGTERM signal, stopping it from accepting new requests, and consecutively closing existing connections.</summary>
termination
connection termination

<a href="https://freecontent.manning.com/handling-client-requests-properly-with-kubernetes/">https://freecontent.manning.com/handling-client-requests-properly-with-kubernetes/</a>
<br></details>

<details>
<summary>An Ingress TLS secret must contain keys named&nbsp;_____&nbsp;that contain the certificate and private key to use for TLS.</summary>
tls.crt&nbsp;and&nbsp;tls.key
<br></details>

<details>
<summary>Can ingress objects terminate TLS connections for your application?</summary>
Yes
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">_____ exposes HTTP and HTTPS routes from outside the cluster to services</span><span style="color: rgb(34, 34, 34);">&nbsp;within the cluster. Traffic routing is controlled by rules defined on the _____ resource.</span></summary>
Ingress
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">An _____ may be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL / TLS, and offer name based virtual hosting.</span></summary>
<span style="color: rgb(34, 34, 34);">Ingress</span>
<br></details>

<details>
<summary>The resources that expose deployments on a network are _____</summary>
Services
<br></details>

<details>
<summary>When you don't need load-balancing and a single Service IP, you can create _____</summary>
headless services
<br></details>

<details>
<summary>Headless services are created by setting the Service's .spec._____ field to _____</summary>
clusterIP

"None"
<br></details>

<details>
<summary>The <b>kubernetes </b>service is configured in all namespaces&nbsp;with virtual IP address that is redirected via _____ to the apiserver.</summary>
kube-proxy
<br></details>

<details>
<summary>Inside a Kubernetes cluster, you might wish to reuse an existing DNS entry, or have legacy systems that are configured for a specific IP address and difficult to re-configure. A Service can specify its own cluster IP address by setting the .spec._____ field.</summary>
clusterIP
<br></details>

<details>
<summary>Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should reference an _____ that contains additional configuration including the name of the controller that should implement it.</summary>
IngressClass&nbsp;
<br></details>

<details>
<summary><span style="color: rgb(34, 34, 34);">You may deploy any number of Ingress controllers</span><span style="color: rgb(34, 34, 34);">&nbsp;within a cluster. When you create an ingress, you should annotate each ingress with the appropriate _____&nbsp;</span><span style="color: rgb(34, 34, 34);">to indicate which ingress controller should be used if more than one exists within your cluster.</span></summary>
ingressClass
<br></details>

<details>
<summary>The _____ service type exposes the Service on each Node�s IP at a static port. A ClusterIP Service, to which the it routes, is automatically created.&nbsp;</summary>
NodePort
<br></details>