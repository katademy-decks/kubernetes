# Jobs 

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">The _____ provides a TTL (time to live) mechanism to limit the lifetime of resource objects that have finished execution.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">TTL controller</span>
</details>

<details>
<summary>
<b>The&nbsp;<span style="color: rgb(34, 34, 34);">TTL controller handles what resource?</span></b>
</summary>
Jobs
</details>

<details>
<summary>
<b>A _____ creates Jobs on a repeating schedule.</b>
</summary>
CronJob&nbsp;
</details>

<details>
<summary>
<b>One CronJob object is like one _____ of a _____ file. It runs a job periodically on a given schedule, written in Cron format.</b>
</summary>
one line of a crontab file
</details>

<details>
<summary>
<b>All CronJob schedule: times are based on the timezone of _____</b>
</summary>
the <b>kube-controller-manager</b>.
</details>

<details>
<summary>
<b>Can CronJobs be used for running backups?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Can CronJobs be used for sending e-mails?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Jobs should be <i>_____ </i>because it is not guaranteed only one job will launch per execution time of its schedule.</b>
</summary>
idempotent
</details>

<details>
<summary>
<b>If a CronJob's _____ field<b>&nbsp;</b>is set, the controller counts how many jobs had missed in the last X seconds.</b>
</summary>
startingDeadlineSeconds&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A CronJob is counted as missed if...&nbsp;</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">it has failed to be created at its scheduled time.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">For example, If&nbsp;</span><code>concurrencyPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;is set to&nbsp;</span><code>Forbid</code><span style="color: rgb(34, 34, 34);">&nbsp;and a CronJob was attempted to be scheduled when there was a previous schedule still running, then it would count as missed.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">Suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;</span><code>08:30:00</code><span style="color: rgb(34, 34, 34);">, and its&nbsp;</span><code>startingDeadlineSeconds</code><span style="color: rgb(34, 34, 34);">&nbsp;field is not set. If the CronJob controller happens to be down from&nbsp;</span><code>08:29:00</code><span style="color: rgb(34, 34, 34);">&nbsp;to&nbsp;</span><code>10:21:00</code><span style="color: rgb(34, 34, 34);">, the job will not start as the number of missed jobs which missed their schedule is greater than 100.</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">
</span>To illustrate this concept further, suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;<code>08:30:00</code>, and its&nbsp;<code>startingDeadlineSeconds</code>&nbsp;is set to 200 seconds. If the CronJob controller happens to be down for the same period as the previous example (<code>08:29:00</code>&nbsp;to&nbsp;<code>10:21:00</code>,) the Job will still start at 10:22:00. This happens as the controller now checks how many missed schedules happened in the last 200 seconds (ie, 3 missed schedules), rather than from the last scheduled time until now.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ creates one or more Pods and ensures that a specified number of them successfully terminate.&nbsp;</span><span style="color: rgb(34, 34, 34);">As pods successfully complete, it tracks the successful completions until a certain number of successful completions is reached.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Job</span>
</details>

<details>
<summary>
<b>A job's default parallelism value is 1.<span style="color: rgb(34, 34, 34);">&nbsp;If it is specified as 0, then the Job...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Is paused until it is increased.</span>
</details>

<details>
<summary>
<b>A job's parallelism is...</b>
</summary>
<span style="color: rgb(34, 34, 34);">The number of Job pods running at any instant.</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For </span>a&nbsp;fixed completion count<span style="color: rgb(34, 34, 34);">&nbsp;Job, you should set&nbsp;_____</span><span style="color: rgb(34, 34, 34);">&nbsp;to the number of completions needed.&nbsp;</span></b>
</summary>
.spec.completions
</details>

<details>
<summary>
<b>What is a Job? What are all the fields to control them?</b>
</summary>
A Pod ran a specific number of completions or schedules&nbsp;
with or without parallelism.
spec:
 &nbsp;completions: 1
 &nbsp;parallelism: 10
 &nbsp;template:
 &nbsp;&nbsp;&nbsp;metadata:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: queue-worker
 &nbsp;&nbsp;&nbsp;spec:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;containers:
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...

spec:
 &nbsp;schedule: "*/1 * * * *"
 &nbsp;jobTemplate:
 &nbsp;&nbsp;&nbsp;spec:&nbsp; &nbsp; &nbsp;containers:
&nbsp; &nbsp; &nbsp; ...
</details>

