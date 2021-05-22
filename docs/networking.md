<details>
	<summary>
		EndpointSlices support three address types: _____, IPv6, Fully Qualified Domain Name

	</summary>
		IPv4
</details>

<details>
	<summary>
		EndpointSlices are a scalable alternative to _____, distributing network endpoints across multiple resources.

	</summary>
		Endpoints
</details>

<details>
	<summary>
		An _____ is full once it reaches 100 endpoints (by default), at which point additional slices will be created.

	</summary>
		EndpointSlice
</details>

<details>
	<summary>
		The controller that creates Services, Endpoints and updates to iptables on nodes is _____

	</summary>
		kube-proxy
</details>

<details>
	<summary>
		_____ objects provide Services with externally-reachable URLs, load balancing, TLS termination, and name-based virtual hosting.

	</summary>
		Ingress
</details>

<details>
	<summary>
		"Headless services are created by setting the Service's .spec._____ field to ""None"""

	</summary>
		clusterIP
</details>

<details>
	<summary>
		An incoming request may be matched by multiple host paths within an Ingress Object. Precedence is given to the _____ matching path rule.

	</summary>
		longest
</details>

<details>
	<summary>
		The .spec.HostAliases field adds entries to a Pod's /etc/_____ file, overriding its internal hostname resolution. This is useful when DNS and other routing options are unavailable.

	</summary>
		hosts
</details>

<details>
	<summary>
		An _____ Object routes incoming requests to different Services depending on a set of rules.

	</summary>
		Ingress
</details>

<details>
	<summary>
		In a LoadBalancer service, the _____ annotation removes the double-hop problem by allowing users to define their own balancing.

	</summary>
		OnlyLocal
</details>

<details>
	<summary>
		Headless services have no ClusterIP, proxying, _____ and are not handled by kube-proxy.

	</summary>
		load-balancing
</details>

<details>
	<summary>
		A Service of type _____ exposes a cluster-internal IP, making it only reachable from within the cluster.

	</summary>
		ClusterIP
</details>

<details>
	<summary>
		The .spec._____ field adds entries to a Pod's /etc/hosts file, overriding its internal hostname resolution. This is useful when DNS and other routing options are unavailable.

	</summary>
		HostAliases
</details>

<details>
	<summary>
		"In each namespace of a cluster, an internal ""Kubernetes"" Service is configured with a virtual IP address that redirects to kube-apiserver via _____."

	</summary>
		kube-proxy
</details>

<details>
	<summary>
		A Service's ports can specify the application protocol to use via the _____ field.

	</summary>
		AppProtocol
</details>

<details>
	<summary>
		You may deploy several Ingress Controllers within one cluster. Just annotate your Ingress objects with a reference to the _____ indicating which Ingress Controller should implement it.

	</summary>
		IngressClass
</details>

<details>
	<summary>
		_____ are a scalable alternative to Endpoints, distributing network endpoints across multiple resources.

	</summary>
		EndpointSlices
</details>

<details>
	<summary>
		"In each namespace of a cluster, an internal ""Kubernetes"" Service is configured with a virtual IP address that redirects to _____ via kube-proxy."

	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		You may deploy several Ingress Controllers within one cluster. Just annotate your _____ objects with a reference to the IngressClass indicating which Ingress Controller should implement it.

	</summary>
		Ingress
</details>

<details>
	<summary>
		The kubernetes components running inside a worker node are: kubelet, _____ and the container runtime

	</summary>
		kube-proxy
</details>

<details>
	<summary>
		The kubernetes components running inside a worker node are: _____, kube-proxy and the container runtime

	</summary>
		kubelet
</details>

<details>
	<summary>
		Every Kubernetes node runs kube-proxy which implements a form of _____ for Services (except ExternalName and headless services)

	</summary>
		Virtual IP
</details>

<details>
	<summary>
		A global allocation map in _____ is updated with a unique IP for each newly created Service.

	</summary>
		etcd
</details>

<details>
	<summary>
		EndpointSlices support three address types: IPv4, _____, Fully Qualified Domain Name

	</summary>
		IPv6
</details>

<details>
	<summary>
		A Service of type NodePort exposes itself on each Node’s IP at a specified, static port. A _____ to which it routes is automatically created.

	</summary>
		ClusterIP
</details>

<details>
	<summary>
		Does a Pod have its own virtual ethernet connection? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Does each Pod have a unique IP? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A Service can map any incoming port to a _____. By default it has the same value as the port field.

	</summary>
		targetPort
</details>

<details>
	<summary>
		Ingress objects can be implemented by various Ingress Controllers. Ingress objects can reference an _____ holding the specific configuration, including the name of the specific controller that should implement it.

	</summary>
		IngressClass
</details>

<details>
	<summary>
		When a request incoming to the cluster is matched by several equal-length Ingress paths, precedence is given to paths with the exact path type over _____ path type.

	</summary>
		prefix
</details>

<details>
	<summary>
		Every Kubernetes node runs _____ which implements a form of Virtual IP for Services (except ExternalName and headless services)

	</summary>
		kube-proxy
</details>

<details>
	<summary>
		Headless services have no _____, proxying, load-balancing and are not handled by kube-proxy.

	</summary>
		ClusterIP
</details>

<details>
	<summary>
		An Ingress Object routes incoming requests to different _____ depending on a set of rules.

	</summary>
		Services
</details>

<details>
	<summary>
		_____ API objects define traffic routing as rules.
	</summary>
		Ingress
</details>

<details>
	<summary>
		To reuse an existing DNS entry, or encapsulate legacy systems configured under a specific IP address, a Service may be set with a custom in-cluster IP address via the .spec._____ field.

	</summary>
		clusterIP
</details>

<details>
	<summary>
		Headless services have no ClusterIP, proxying, load-balancing and are not handled by _____.

	</summary>
		kube-proxy
</details>

<details>
	<summary>
		If none of the hosts or paths match the HTTP request in any of your Ingress objects, traffic is routed to _____, typically implemented by the Ingress Controller.

	</summary>
		the default backend
</details>

<details>
	<summary>
		Ingress API objects define traffic routing as _____.
	</summary>
		rules
</details>

<details>
	<summary>
		The _____ Service creates an external IP address. The Service itself does not speak with any Pod IP's; instead, it chooses a Node to send packets to.

	</summary>
		LoadBalancer
</details>

<details>
	<summary>
		When a request incoming to the cluster is matched by several equal-length Ingress paths, precedence is given to paths with the _____ path type over prefix path type.

	</summary>
		exact
</details>

<details>
	<summary>
		A Service of type _____ maps the Service to the contents of the ExternalName field (e.g. foo.bar.example.com), by returning a CNAME record.

	</summary>
		ExternalName
</details>

<details>
	<summary>
		"_____ services are created by setting the Service's .spec.clusterIP field to ""None"""

	</summary>
		Headless
</details>

<details>
	<summary>
		An Ingress' TLS secret must contain a _____ and private key (tls.key).

	</summary>
		certificate (tls.crt)
</details>

<details>
	<summary>
		A Service of type _____ exposes itself on each Node’s IP at a specified, static port. A ClusterIP to which it routes is automatically created.

	</summary>
		NodePort
</details>

<details>
	<summary>
		Can Ingress API Objects terminate TLS connections for your application? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		EndpointSlices support three address types: IPv4, IPv6, _____

	</summary>
		Fully Qualified Domain Name
</details>

<details>
	<summary>
		A _____ in etcd is updated with a unique IP for each newly created Service.

	</summary>
		global allocation map
</details>

<details>
	<summary>
		Headless services have no ClusterIP, _____, load-balancing and are not handled by kube-proxy.

	</summary>
		proxying
</details>

<details>
	<summary>
		"In each _____ of a cluster, an internal ""Kubernetes"" Service is configured with a virtual IP address that redirects to kube-apiserver via kube-proxy."

	</summary>
		namespace
</details>

<details>
	<summary>
		Every Kubernetes node runs kube-proxy which implements a form of Virtual IP for Services (except _____ and headless services)

	</summary>
		ExternalName
</details>

<details>
	<summary>
		_____ services have no ClusterIP, proxying, load-balancing and are not handled by kube-proxy.

	</summary>
		Headless
</details>

<details>
	<summary>
		Every Kubernetes node runs kube-proxy which implements a form of Virtual IP for Services (except ExternalName and _____ services)

	</summary>
		headless
</details>

<details>
	<summary>
		The kubernetes components running inside a worker node are: kubelet, kube-proxy and the _____

	</summary>
		container runtime
</details>

<details>
	<summary>
		The _____ service type exposes the Service externally using a cloud provider’s load balancer.

	</summary>
		LoadBalancer
</details>

<details>
	<summary>
		An Ingress' TLS secret must contain a certificate (tls.crt) and _____.

	</summary>
		private key (tls.key)
</details>

<details>
	<summary>
		"Headless services are created by setting the Service's .spec.clusterIP field to _____"

	</summary>
		""None""
</details>

<details>
	<summary>
		A _____ object is a network abstraction that allows routing to workloads in the cluster.

	</summary>
		Service
</details>

<details>
	<summary>
		The _____ service type exposes the Service externally using a cloud provider's load balancer.

	</summary>
		LoadBalancer
</details>

<details>
	<summary>
		The _____ service type exposes a Service on each Node's IP at a static port.

	</summary>
		NodePort
</details>

<details>
	<summary>
		Does a Pod have its own network namespace inside? _____

	</summary>
		Yes
</details>

