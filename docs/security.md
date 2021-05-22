<details>
	<summary>
		Can network segmentation improve Kubernetes security? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A request to kube-apiserver must include the username of the requester, the requested _____, and the object affected by the action.

	</summary>
		action
</details>

<details>
	<summary>
		_____ are usually stored in the /etc/kubernetes/pki directory.

	</summary>
		PKI certificates
</details>

<details>
	<summary>
		Should you run etcd on dedicated nodes? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		"Kubernetes determines the _____ of an incoming request from the common name field in the subject field of the certificate (e.g., ""/CN=katademy"")"

	</summary>
		username
</details>

<details>
	<summary>
		Are service accounts bound to specific namespaces? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A request is authorized if an existing policy declares that the user has permissions to complete the requested action on the given _____.

	</summary>
		object
</details>

<details>
	<summary>
		Once created, a CertificateSigningRequest must be _____ before it can be signed.

	</summary>
		approved
</details>

<details>
	<summary>
		In order to approve CertificateSigningRequests, you must allow the _____ to approve them.

	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		Authentication protocols (such as LDAP, SAML, Kerberos, etc) can be integrated into Kubernetes by using an _____ or authenticating webhook.
	</summary>
		authenticating proxy
</details>

<details>
	<summary>
		The four audit levels are: None - don't log these events. Metadata - log a request's user, timestamp, resource, verb, etc. _____ RequestResponse - log event metadata, request body and response bodies.

	</summary>
		Request - log event metadata and request body.
</details>

<details>
	<summary>
		You should usually use at least two methods of authentication in your cluster: one for _____ and one for service accounts.

	</summary>
		human users
</details>

<details>
	<summary>
		_____ are tied to a set of credentials stored as Secrets, which allow Pods to talk to the Kubernetes API.

	</summary>
		ServiceAccounts
</details>

<details>
	<summary>
		ServiceAccounts are tied to a set of credentials stored as _____, which allow Pods to talk to the Kubernetes API.

	</summary>
		Secrets
</details>

<details>
	<summary>
		Are Client Certificates a valid authentication module? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		When multiple _____ objects select the same Pod, it becomes restricted to what is allowed by the union of those policies' ingress/egress rules.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		When an attacker has control of a Kubernetes _____, they may be able to access the cloud provider's user and metadata APIs to exfiltrate credentials of your cloud account.

	</summary>
		Node
</details>

<details>
	<summary>
		The default _____ that can be used in the API server are ABAC, RBAC, and Webhook.

	</summary>
		authorization modules
</details>

<details>
	<summary>
		The kubelet's _____ flag controls its automatic certificate rotation. It can automatically generate a new key and request a new certificate from the Kubernetes API before the current certificate's expiration.

	</summary>
		--rotate-certificates
</details>

<details>
	<summary>
		The four audit levels are: None - don't log these events. _____ Request - log event metadata and request body. RequestResponse - log event metadata, request body and response bodies.

	</summary>
		Metadata - log a request's user, timestamp, resource, verb, etc.
</details>

<details>
	<summary>
		Are authentication proxies a valid authentication method? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A Certificate Authority _____ and certificate are required to sign kubelet certificates.

	</summary>
		key
</details>

<details>
	<summary>
		_____ objects require a specific backend running in the cluster that implements them, such as Calico or Flannel.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		A request is authorized if an existing policy declares that the user has permissions to complete the requested _____ on the given object.

	</summary>
		action
</details>

<details>
	<summary>
		Are plain, bootstrap and JWT tokens a valid Kubernetes authentication module? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Kubernetes requires _____ certificates for authentication over TLS.

	</summary>
		PKI
</details>

<details>
	<summary>
		With _____ files, you can organize your clusters, users, contexts, and namespaces.

	</summary>
		kubeconfig
</details>

<details>
	<summary>
		Do AppArmor profiles have to be manually downloaded into the Node before applying the annotation? _____

	</summary>
		Yes - except the container runtime's default AppArmor profile.
</details>

<details>
	<summary>
		An Admission Controller Module rejects a request. What happens to the request? _____

	</summary>
		It is immediately rejected.
</details>

<details>
	<summary>
		The kube-apiserver should have a _____ restricting it to be accessible only by specific IPs.

	</summary>
		firewall
</details>

<details>
	<summary>
		A request to kube-apiserver must include the _____ of the requester, the requested action, and the object affected by the action.

	</summary>
		username
</details>

<details>
	<summary>
		A kubelet's kubeconfig file requires a key and a _____ to connect to kube-apiserver.

	</summary>
		cert
</details>

<details>
	<summary>
		Can Admission controllers act on requests that create an object? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		"Potentially insecure Linux capabilities (such as ""all"", ""CHOWN"", ""NET_RAW"", ""SETPCAP"") can be disabled via _____."

	</summary>
		securityContext
</details>

<details>
	<summary>
		The KUBECONFIG environment variable holds _____

	</summary>
		a list of kubeconfig files
</details>

<details>
	<summary>
		Restricting access to _____ prevents an attacker from modifying the desired cluster state.

	</summary>
		etcd
</details>

<details>
	<summary>
		Setting securityContext._____ to False makes it harder to escalate privileges inside a Container.

	</summary>
		allowPrivilegeEscalation
</details>

<details>
	<summary>
		"Tools like _____ or kata containers can ""sandbox"" Pods on the same host from each other, giving you an extra layer of isolation."

	</summary>
		gVisor
</details>

<details>
	<summary>
		CertificateSigningRequest objects include a PEM-encoded PKCS#10 signing request in the spec._____ field.

	</summary>
		request
</details>

<details>
	<summary>
		A public image registry may be compromised, so it is useful to use _____ registries.

	</summary>
		dedicated, private
</details>

<details>
	<summary>
		AppArmor profiles are specified per _____

	</summary>
		Container
</details>

<details>
	<summary>
		Admission Control Modules can modify or _____ requests.

	</summary>
		reject
</details>

<details>
	<summary>
		API requests are tied to either a username, a service account, or are treated as _____.

	</summary>
		anonymous requests
</details>

<details>
	<summary>
		After the request is _____ as coming from a valid user, the request must then be authorized to check if it's allowed.

	</summary>
		authenticated
</details>

<details>
	<summary>
		When TLS bootstrapping, the _____ must be able to authenticate as a user with the rights to create and retrieve CertificateSigningRequests

	</summary>
		kubelet
</details>

<details>
	<summary>
		The _____ audit backend writes event to a disk

	</summary>
		log
</details>

<details>
	<summary>
		"Requests in Kubernetes come with ""usernames"" for access control decisions and logging. But how does Kubernetes define a ""user""? _____"

	</summary>
		It doesn't! No concrete representative human ""user"" object exists in Kubernetes.
</details>

<details>
	<summary>
		Admission Control Modules can access contents of Kubernetes objects that are being _____ or modified.

	</summary>
		created
</details>

<details>
	<summary>
		Any request that presents a valid _____ signed by the cluster's Certificate Authority is considered authenticated.

	</summary>
		certificate
</details>

<details>
	<summary>
		Any request that presents a valid certificate signed by the cluster's _____ is considered authenticated.

	</summary>
		Certificate Authority
</details>

<details>
	<summary>
		_____ like fluentd can be used to collect/distribute Kubernetes audit events from log files

	</summary>
		Log collectors
</details>

<details>
	<summary>
		Logstash can be used to collect/distribute Kubernetes audit events from the _____

	</summary>
		webhook audit backend
</details>

<details>
	<summary>
		When a request reaches kube-apiserver, it goes through stages: _____, Authorization, Admission Control

	</summary>
		Authentication
</details>

<details>
	<summary>
		The four audit levels are: _____ Metadata - log a request's user, timestamp, resource, verb, etc. Request - log event metadata and request body. RequestResponse - log event metadata, request body and response bodies.

	</summary>
		None - don't log these events.
</details>

<details>
	<summary>
		A RoleBinding grants a role's permissions to a set of users, _____ or service accounts.

	</summary>
		groups
</details>

<details>
	<summary>
		"The root (""/"") filesystem on containers should be set as read-only via securityContext._____, because an attacker may escalate privileges by editing operating system files."

	</summary>
		readOnlyRootFilesystem: true
</details>

<details>
	<summary>
		Kubernetes authorizes API requests at the _____

	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		"Kubernetes determines the username of an incoming request from the common name field in the subject field of the certificate (e.g., ""_____"")"

	</summary>
		/CN=katademy
</details>

<details>
	<summary>
		Are client certificates a valid authentication method? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A request was authorized by a single Authorization Module. Does it also get evaluated by other available Authorization Modules before being authorized? _____

	</summary>
		No
</details>

<details>
	<summary>
		If a request cannot be authenticated, it is _____

	</summary>
		rejected with status code 401
</details>

<details>
	<summary>
		The default authorization modules that can be used in the API server are ABAC, RBAC, and _____.

	</summary>
		Webhook
</details>

<details>
	<summary>
		An attacker may download exploits directly into a container if its Pod has free access to _____.

	</summary>
		the Internet
</details>

<details>
	<summary>
		Attackers can break out of the _____ by epxloiting the container runtime, kernel etc.

	</summary>
		Container
</details>

<details>
	<summary>
		Is basic auth a valid authentication method? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Setting securityContext.allowPrivilegeEscalation to _____ makes it harder to escalate privileges inside a Container.

	</summary>
		False
</details>

<details>
	<summary>
		_____ objects define rules about what events should be recorded and what data they should include.

	</summary>
		audit.k8s.io/v1 kind: Policy
</details>

<details>
	<summary>
		_____ allows defining privilege and access controls per Pod or per Container.

	</summary>
		securityContext
</details>

<details>
	<summary>
		When kubelet starts, it looks for its _____ file and its credentials (normally a TLS key and signed certificate), then retrieves the kube-apiserver URL and attempts to communicate with it.

	</summary>
		kubeconfig
</details>

<details>
	<summary>
		When a request reaches kube-apiserver, it goes through stages: Authentication, Authorization, _____

	</summary>
		Admission Control
</details>

<details>
	<summary>
		Audit backends persist audit events to _____.

	</summary>
		an external storage
</details>

<details>
	<summary>
		Audit _____ determine what events are recorded and which backends persist the records.

	</summary>
		policies
</details>

<details>
	<summary>
		A kubelet's kubeconfig file requires a _____ and a cert to connect to kube-apiserver.

	</summary>
		key
</details>

<details>
	<summary>
		Audit logging increases the memory consumption of the kube-api-server because some context required for auditing is stored for each _____.

	</summary>
		request
</details>

<details>
	<summary>
		You can combine ClusterRoles using an _____

	</summary>
		aggregationRule
</details>

<details>
	<summary>
		securityContext allows defining privilege and access controls per _____ or per Container.

	</summary>
		Pod
</details>

<details>
	<summary>
		A CertificateSigningRequest's _____ field denotes the recipient that the request is being made to.

	</summary>
		spec.signerName
</details>

<details>
	<summary>
		Are passwords a valid Kubernetes authentication module? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Each request on each stage of its execution generates an audit event, which is then pre-processed according to a certain _____ object and written to a backend.

	</summary>
		audit.k8s.io/v1 Policy
</details>

<details>
	<summary>
		Admission Control Modules can _____ or reject requests.

	</summary>
		modify
</details>

<details>
	<summary>
		A _____'s spec.signerName field denotes the recipient that the request is being made to.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		Once a _____ selects a particular Pod, that Pod will reject any connections that are not explicitly allowed by it.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		The four audit levels are: None - don't log these events. Metadata - log a request's user, timestamp, resource, verb, etc. Request - log event metadata and request body. _____

	</summary>
		RequestResponse - log event metadata, request body and response bodies.
</details>

<details>
	<summary>
		Can Admission controllers act on requests that connect (proxy) to an object? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Pods that do not need to use kube-apiserver should have their _____ disabled.

	</summary>
		default ServiceAccount
</details>

<details>
	<summary>
		securityContext allows defining privilege and access controls per Pod or per _____.

	</summary>
		Container
</details>

<details>
	<summary>
		Is Kubelet RBAC enabled by default? _____

	</summary>
		No!!!
</details>

<details>
	<summary>
		Kubernetes authentication examines the incoming HTTP request's _____ and certificate.

	</summary>
		headers
</details>

<details>
	<summary>
		When multiple NetworkPolicy objects select the same _____, it becomes restricted to what is allowed by the union of those policies' ingress/egress rules.

	</summary>
		Pod
</details>

<details>
	<summary>
		Is RBAC enabled for a new cluster by default? _____

	</summary>
		No!!!
</details>

<details>
	<summary>
		The _____ group represents authenticated users.

	</summary>
		system:authenticated
</details>

<details>
	<summary>
		Should you be able to freely send network traffic to etcd from the cluster? _____

	</summary>
		No
</details>

<details>
	<summary>
		By default, requests to the kubelet's HTTPS endpoint that are not rejected by other configured authentication methods are treated as _____ requests.

	</summary>
		anonymous
</details>

<details>
	<summary>
		A kubelet's kubeconfig requires a certificate to communicate with kube-apiserver. This certificate must be signed by a _____ trusted by kube-apiserver.

	</summary>
		Certificate Authority
</details>

<details>
	<summary>
		Your current, in-use cluster namespace is stored in the _____ file on your local machine.

	</summary>
		kubeconfig
</details>

<details>
	<summary>
		Any request that presents a valid certificate signed by the cluster's Certificate Authority is considered _____.

	</summary>
		authenticated
</details>

<details>
	<summary>
		Does a user need a Role and RoleBinding to access Kubernetes resources? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		ServiceAccounts are tied to a set of credentials stored as Secrets, which allow _____ to talk to the Kubernetes API.

	</summary>
		Pods
</details>

<details>
	<summary>
		A _____ resource is used to request that a certificate be signed by a denoted signer, after which the request may be approved or denied before finally being signed.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		"Potentially insecure Linux _____ (such as ""all"", ""CHOWN"", ""NET_RAW"", ""SETPCAP"") can be disabled via securityContext."

	</summary>
		capabilities
</details>

<details>
	<summary>
		Admission Control Modules can access contents of Kubernetes objects that are being created or _____.

	</summary>
		modified
</details>

<details>
	<summary>
		Can _____ help prevent internal denial of service attacks? Yes

	</summary>
		ResourceQuotas
</details>

<details>
	<summary>
		When an event is processed, it's compared against the list of audit.k8s.io/v1/Policy rules in order. The first matching rule sets the _____ of the event.

	</summary>
		audit level
</details>

<details>
	<summary>
		Are bearer tokens a valid authentication method? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		_____ is a file used to configure access to clusters

	</summary>
		kubeconfig
</details>

<details>
	<summary>
		After the request is authenticated as coming from a valid user, the request must then be _____ to check if it's allowed.

	</summary>
		authorized
</details>

<details>
	<summary>
		Containers in production should run under a Linux non-root user. This is set in securityContext via _____

	</summary>
		runAsNonRoot: true
</details>

<details>
	<summary>
		Do you need to distribute a CA certificate to each kubelet? _____

	</summary>
		No - only the master nodes where kube-apiserver is running.
</details>

<details>
	<summary>
		The _____ audit backend sends events to an external API.

	</summary>
		webhook
</details>

<details>
	<summary>
		Can attackers remove a NetworkPolicy from within etcd? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		_____ audit failures might suggest a misconfigured service account, or the presence of an attacker.

	</summary>
		RBAC
</details>

<details>
	<summary>
		Should you enforce image signing in production? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Pods that need to connect to the apiserver can automatically inject the _____ and valid bearer token into themselves via a service account.

	</summary>
		public root certificate
</details>

<details>
	<summary>
		Nodes must be provisioned with valid client credentials and a _____ to connect to kube-apiserver.

	</summary>
		public root certificate
</details>

<details>
	<summary>
		A service mesh can trace and profile requests happening inside a cluster. You can then find and disable requests that aren't expected to ever happen, for ex. via a _____.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		"A kubelet's initial bootstrap credentials for TLS can be either authentication file tokens, or _____ tokens."

	</summary>
		""bootstrap""
</details>

<details>
	<summary>
		Log collectors like fluentd can be used to collect/distribute Kubernetes audit events from _____

	</summary>
		log files
</details>

<details>
	<summary>
		The default Pod ServiceAccount can be disabled by setting _____

	</summary>
		autonomousServiceAccountToken: false
</details>

<details>
	<summary>
		The _____ and ClusterRole Objects contain sets of additive authorization permissions

	</summary>
		Role
</details>

<details>
	<summary>
		Do you need to upload AppArmor profiles to ALL of your Nodes? _____

	</summary>
		Yes - since you don't know which Node your Pod may be scheduled to.
</details>

<details>
	<summary>
		Can using standardized, base images for all of your Containers improve overall workload security? _____

	</summary>
		Yes. If the base image is secured by default, child images will inherit these upgrades.
</details>

<details>
	<summary>
		Restricting access to your cluster nodes (especially _____ nodes) can prevent further privilege escalation to your cloud provider platform.

	</summary>
		master
</details>

<details>
	<summary>
		Does Container/Operating System scanning improve cluster security? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		PKI certificates are usually stored in the /etc/kubernetes/_____ directory.

	</summary>
		pki
</details>

<details>
	<summary>
		Once an attacker controls a container, there is risk they might obtain control of the _____ it runs on, and then the internal cluster network.

	</summary>
		Node
</details>

<details>
	<summary>
		A RoleBinding grants a role's permissions to a set of _____, groups or service accounts.

	</summary>
		users
</details>

<details>
	<summary>
		A NetworkPolicy uses _____ to specify the groups of pods allowed to communicate with each other, and other network endpoints.

	</summary>
		labels
</details>

<details>
	<summary>
		The kubelet uses _____ for authenticating to the Kubernetes API.

	</summary>
		certificates (with 1 year expiration)
</details>

<details>
	<summary>
		When kubelet starts, it looks for its kubeconfig file and its credentials (normally a TLS key and signed certificate), then retrieves the _____ URL and attempts to communicate with it.

	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		Do you need to distribute a key and signed certificate for each kubelet? _____

	</summary>
		Yes - ideally unique ones.
</details>

<details>
	<summary>
		When multiple NetworkPolicy objects select the same Pod, it becomes restricted to what is allowed by the _____ of those policies' ingress/egress rules.

	</summary>
		union
</details>

<details>
	<summary>
		Can attackers manipulate cluster data in etcd, bypassing kube-apiserver completely? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Each request on each stage of its execution generates an audit _____, which is then pre-processed according to a certain audit.k8s.io/v1 Policy object and written to a backend.

	</summary>
		event
</details>

<details>
	<summary>
		Should you minimise user privilege inside your containers in production? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		True or False? Kubernetes automatically its Container Runtime's default seccomp and AppArmor profiles to Pods and Containers. _____

	</summary>
		False!!! A Container running on Kubernetes has FEWER restrictions applied to it by default than if it were ran directly on a Container Runtime. Go set them now!
</details>

<details>
	<summary>
		If a container has network access to a /metrics endpoint, what does that mean for security? _____

	</summary>
		Attackers could potentially find almost everything about the cluster from inside the container by reading cAdvisor/Heapster output at the endpoint.
</details>

<details>
	<summary>
		A CertificateSigningRequest will initially have Pending status. If it meets specific criteria, it will be promoted by the _____ to Approved status.

	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		_____ allows cluster administrators to learn about the context of a cluster event: when it happened, where, who initiated it and what it did.

	</summary>
		Audit
</details>

<details>
	<summary>
		Your current, in-use cluster context is stored in the _____ file on your local machine.

	</summary>
		kubeconfig
</details>

<details>
	<summary>
		The _____ resource type allows a client to ask for an X.509 certificate be issued, based on a signing request.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		Audit logging increases the memory consumption of the _____ because some context required for auditing is stored for each request.

	</summary>
		kube-api-server
</details>

<details>
	<summary>
		Does a service mesh make your workloads more isolated by default? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		A _____ object can prevent an attacker inside one Pod from running the services of another Pod

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		A Certificate Authority key and _____ are required to sign kubelet certificates.

	</summary>
		certificate
</details>

<details>
	<summary>
		You can secure an Ingress by specifying a Secret that contains a TLS _____ and certificate

	</summary>
		private key
</details>

<details>
	<summary>
		A _____ grants a role's permissions to a set of users, groups or service accounts.

	</summary>
		RoleBinding
</details>

<details>
	<summary>
		Audit policies determine what events are recorded and which _____ persist the records.

	</summary>
		backends
</details>

<details>
	<summary>
		When a request reaches _____, it goes through stages: Authentication, Authorization, Admission Control

	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		A _____ uses labels to specify the groups of pods allowed to communicate with each other, and other network endpoints.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		Can service meshes encrypt in-cluster traffic (and automatically rotate certificates)? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		You should usually use at least two methods of authentication in your cluster: one for human users and one for _____.

	</summary>
		service accounts
</details>

<details>
	<summary>
		A RoleBinding grants a role's permissions to a set of users, groups or _____.

	</summary>
		service accounts
</details>

<details>
	<summary>
		Groups are a set of strings, each of which indicates _____.

	</summary>
		a user's membership
</details>

<details>
	<summary>
		"The root (""/"") filesystem on containers should be set as read-only via securityContext.readOnlyRootFilesystem: true, because _____."

	</summary>
		an attacker may escalate privileges by editing operating system files
</details>

<details>
	<summary>
		The default authorization modules that can be used in the API server are ABAC, _____, and Webhook.

	</summary>
		RBAC
</details>

<details>
	<summary>
		Each _____ on each stage of its execution generates an audit event, which is then pre-processed according to a certain audit.k8s.io/v1 Policy object and written to a backend.

	</summary>
		request
</details>

<details>
	<summary>
		Audit allows cluster administrators to learn about the context of a cluster _____: when it happened, where, who initiated it and what it did.

	</summary>
		event
</details>

<details>
	<summary>
		Does the admission or validation of a request happen first? _____

	</summary>
		admission
</details>

<details>
	<summary>
		When _____ starts, it looks for its kubeconfig file and its credentials (normally a TLS key and signed certificate), then retrieves the kube-apiserver URL and attempts to communicate with it.

	</summary>
		kubelet
</details>

<details>
	<summary>
		A request to kube-apiserver must include the username of the requester, the requested action, and the _____ affected by the action.

	</summary>
		object
</details>

<details>
	<summary>
		"A kubelet's initial bootstrap credentials for TLS can be either authentication _____ tokens, or ""bootstrap"" tokens."

	</summary>
		file
</details>

<details>
	<summary>
		Kubernetes authentication examines the incoming HTTP request's headers and _____.

	</summary>
		certificate
</details>

<details>
	<summary>
		Pods that need to connect to the apiserver can automatically inject the public root certificate and valid _____ into themselves via a service account.

	</summary>
		bearer token
</details>

<details>
	<summary>
		_____ objects include a PEM-encoded PKCS#10 signing request in the spec.request field.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		Each request on each stage of its execution generates an audit event, which is then pre-processed according to a certain audit.k8s.io/v1 Policy object and written to a _____.

	</summary>
		backend
</details>

<details>
	<summary>
		Authentication protocols (such as LDAP, SAML, Kerberos, etc) can be integrated into Kubernetes by using an authenticating proxy or _____.
	</summary>
		authenticating webhook
</details>

<details>
	<summary>
		_____ (such as LDAP, SAML, Kerberos, etc) can be integrated into Kubernetes by using an authenticating proxy or authenticating webhook.
	</summary>
		Authentication protocols
</details>

<details>
	<summary>
		To improve security, you could ideally collect logs from all containers - but especially RBAC _____ logs.

	</summary>
		access/deny
</details>

<details>
	<summary>
		Is admission control's NodeRestriction enabled by default? _____

	</summary>
		No!
</details>

<details>
	<summary>
		The _____ environment variable holds a list of kubeconfig files

	</summary>
		KUBECONFIG
</details>

<details>
	<summary>
		To specify which AppArmor profile a Container should run with, specify the profile as an _____ in the Pod's metadata.

	</summary>
		annotation
</details>

<details>
	<summary>
		Can admission controllers set complex defaults for fields? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		Audit records begin their lifecycle inside the _____ Kubernetes component.

	</summary>
		kube-apiserver
</details>

<details>
	<summary>
		_____ is a user-space kernel that can intercept and implement syscalls in userspace, effectively sandboxing the Pod to an environment with low capabilities and restricted seccomp filters.

	</summary>
		gVisor
</details>

<details>
	<summary>
		Once created, a _____ must be approved before it can be signed.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		You can secure an Ingress by specifying a Secret that contains a TLS private key and _____

	</summary>
		certificate
</details>

<details>
	<summary>
		By default, Pods in a cluster come with a _____ with permissions allowing it to communicate with kube-apiserver. This should be disabled for Pods that are never expected to need to talk to kube-apiserver, as an attacker could otherwise steal the auth token.

	</summary>
		service account
</details>

<details>
	<summary>
		Kubernetes requires PKI certificates for _____ over TLS.

	</summary>
		authentication
</details>

<details>
	<summary>
		A _____ object can divide your workloads into network tiers, locking them by default, with the ability specifically allow communication between them, or between their namespaces.

	</summary>
		NetworkPolicy
</details>

<details>
	<summary>
		Containers in production should run under a Linux non-root user. This is set in _____ via runAsNonRoot: true

	</summary>
		securityContext
</details>

<details>
	<summary>
		A _____ will initially have Pending status. If it meets specific criteria, it will be promoted by the kube-controller-manager to Approved status.

	</summary>
		CertificateSigningRequest
</details>

<details>
	<summary>
		Whenever a kubelet retrieves a new signed certificate from the Kubernetes API it will write it to _____

	</summary>
		the disk
</details>

<details>
	<summary>
		To specify which AppArmor profile a Container should run with, specify the profile as an annotation in the Pod's _____.

	</summary>
		metadata
</details>

<details>
	<summary>
		Can Admission controllers act on requests that delete an object? _____

	</summary>
		Yes
</details>

<details>
	<summary>
		"Tools like gVisor or _____ can ""sandbox"" Pods on the same host from each other, giving you an extra layer of isolation."

	</summary>
		kata containers
</details>

<details>
	<summary>
		A CertificateSigningRequest will initially have Pending status. If it meets specific criteria, it will be promoted by the kube-controller-manager to _____ status.

	</summary>
		Approved
</details>

<details>
	<summary>
		The default authorization modules that can be used in the API server are _____, RBAC, and Webhook.

	</summary>
		ABAC
</details>

<details>
	<summary>
		When a request reaches kube-apiserver, it goes through stages: Authentication, _____, Admission Control

	</summary>
		Authorization
</details>

<details>
	<summary>
		etcd should have authentication, be firewalled and _____ at rest.

	</summary>
		encrypted
</details>

<details>
	<summary>
		Can Admission controllers act on requests that read an object? _____

	</summary>
		No
</details>

<details>
	<summary>
		The Role and _____ Objects contain sets of additive authorization permissions

	</summary>
		ClusterRole
</details>

<details>
	<summary>
		_____ persist audit events to an external storage.

	</summary>
		Audit backends
</details>

<details>
	<summary>
		Does kube-apiserver verify the kubelet's serving certificate by default? _____

	</summary>
		No. The connection is subject to MITM attacks by default.
</details>

<details>
	<summary>
		Can normal users be added to a cluster through an API call? _____

	</summary>
		No
</details>

<details>
	<summary>
		Once Cluster TLS is established, incoming requests can begin the _____ step when trying to communicate to the cluster.

	</summary>
		Authentication
</details>

