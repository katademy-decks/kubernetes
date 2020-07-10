# Ephemeral_Containers 

<details>
<summary>
<span style="color: rgb(34, 34, 34);">An ephemeral container&nbsp; runs temporarily in an existing Pod&nbsp;</span><span style="color: rgb(34, 34, 34);">to accomplish...</span>
</summary>
<div>*user-initiated actions*&nbsp;</div><div>Such as troubleshooting and inspecting services</div>
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Sometimes it's necessary to inspect the state of an existing Pod, however, for example to troubleshoot a hard-to-reproduce bug. In these cases you can run _____&nbsp;</span><span style="color: rgb(34, 34, 34);">in an existing Pod to _____</span>
</summary>
<span style="color: rgb(34, 34, 34);">an ephemeral container&nbsp;</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">inspect its state and run arbitrary commands</span>
</div>
</details>

<details>
<summary>
Will an ephemeral container ever be automatically restarted?
</summary>
No
</details>

<details>
<summary>
Do ephemeral containers have guaranteed resources?
</summary>
No
</details>

<details>
<summary>
Do ephemeral containers guarantee execution?
</summary>
No
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Ephemeral containers are described using...</span>
</summary>
<span style="color: rgb(34, 34, 34);">the same&nbsp;</span><code>ContainerSpec</code><span style="color: rgb(34, 34, 34);">&nbsp;as regular containers</span><div><span style="color: rgb(34, 34, 34);">
</span></div><div><span style="color: rgb(34, 34, 34);">However, many fields are incompatible and disallowed</span></div>
</details>

<details>
<summary>
<div>You are trying to interactively troubleshoot a container.&nbsp;</div><div>
</div><div><code>kubectl exec</code>&nbsp;was insufficient because the container has crashed</div><div>
</div><div>The container image is *minimal *and&nbsp;*distroless *and doesn't include debugging utilities.</div>
<div>What can you use to troubleshoot?</div>
</summary>
Ephemeral containers
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">When using ephemeral containers, it's helpful to enable _____&nbsp;</span>so you can view processes in other containers.

</summary>
process namespace sharing
</details>

<details>
<summary>
<span style="color: rgb(34, 34, 34);">Ephemeral containers are created using the&nbsp;</span><code>ephemeralcontainers</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">subresource of Pod,&nbsp;</span><span style="color: rgb(34, 34, 34);">which can be demonstrated using&nbsp;</span><code>kubectl --raw.</code><div><code>
</code></div><div>First describe the ephemeral container to add as an EphemeralContainers list:<code>
</code></div>
</summary>
<div>{
</div><div><pre><code>    <span style="color: green; font-weight: 700;">"apiVersion"</span>: <span style="color: rgb(187, 68, 68);">"v1"</span>,
    <span style="color: green; font-weight: 700;">"kind"</span>: <span style="color: rgb(187, 68, 68);">"EphemeralContainers"</span>,
    <span style="color: green; font-weight: 700;">"metadata"</span>: {
            <span style="color: green; font-weight: 700;">"name"</span>: <span style="color: rgb(187, 68, 68);">"example-pod"</span>
    },
    <span style="color: green; font-weight: 700;">"ephemeralContainers"</span>: [{
        <span style="color: green; font-weight: 700;">"command"</span>: [
            <span style="color: rgb(187, 68, 68);">"sh"</span>
        ],
        <span style="color: green; font-weight: 700;">"image"</span>: <span style="color: rgb(187, 68, 68);">"busybox"</span>,
        <span style="color: green; font-weight: 700;">"imagePullPolicy"</span>: <span style="color: rgb(187, 68, 68);">"IfNotPresent"</span>,
        <span style="color: green; font-weight: 700;">"name"</span>: <span style="color: rgb(187, 68, 68);">"debugger"</span>,
        <span style="color: green; font-weight: 700;">"stdin"</span>: <span style="color: rgb(170, 34, 255); font-weight: 700;">true</span>,
        <span style="color: green; font-weight: 700;">"tty"</span>: <span style="color: rgb(170, 34, 255); font-weight: 700;">true</span>,
        <span style="color: green; font-weight: 700;">"terminationMessagePolicy"</span>: <span style="color: rgb(187, 68, 68);">"File"</span>
    }]
}</code></pre></div>
</details>

