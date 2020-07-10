# DaemonSet 

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

