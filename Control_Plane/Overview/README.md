# Overview 

<details>
<summary>
<b>List processes running on every Kubernetes Master</b>
</summary>
1. kube-apiserver
2. kube-controller-manager
3. kube-scheduler

<img src="paste-d842301571ce981466b41d198776a3b6b0df20e8.jpg">
</details>

<details>
<summary>
<b>Kubernetes Master</b>
</summary>
kube-controller-manager
kube-apiserverkube-scheduler
Uses and provides the following communication:
<ul><li>fetch pod logs.</li><li>kubectl-attach</li><li>kubectl port-forward</li><li>SSH tunnel</li></ul>
</details>

