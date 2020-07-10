# Overview 

<details>
<summary>
List processes running on every Kubernetes Master
</summary>
1. kube-apiserver
2. kube-controller-manager
3. kube-scheduler

<img src="paste-d842301571ce981466b41d198776a3b6b0df20e8.jpg">
</details>

<details>
<summary>
Kubernetes Master
</summary>
<div><div>kube-controller-manager
kube-apiserver<div>kube-scheduler</div></div><div>
</div>Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

