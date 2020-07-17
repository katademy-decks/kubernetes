# Jobs 

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">Suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;</span><code>08:30</code><span style="color: rgb(34, 34, 34);">, and its&nbsp;</span><code>startingDeadlineSeconds</code><span style="color: rgb(34, 34, 34);">&nbsp;field is not set. If the CronJob controller happens to be down from&nbsp;</span><code>08:29</code><span style="color: rgb(34, 34, 34);">&nbsp;to&nbsp;</span><code>10:21</code><span style="color: rgb(34, 34, 34);">, what happens to the job?</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">The job will not start.&nbsp;</span><span style="color: rgb(34, 34, 34);">The number of missed jobs which missed their schedule is greater than 100.</span>
</details>

<details>
<summary>
<b>Suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;<code>08:30</code>, and its&nbsp;<code>startingDeadlineSeconds</code>&nbsp;is set to 200 seconds. If the CronJob controller happens to be down between&nbsp;<code>08:29</code>&nbsp;to&nbsp;<code>10:21,</code>&nbsp;the Job will still start at _____.&nbsp;</b>
</summary>
10:22
This happens as the controller checks how many missed schedules happened in the last 200 seconds (ie, 3 missed schedules).
</details>

<details>
<summary>
<b>Jobs on a repeating schedule are called...</b>
</summary>
CronJobs
</details>

<details>
<summary>
<b>One CronJob object is like one line of a _____ file. It runs a job periodically on a given schedule, written in Cron format.</b>
</summary>
crontab
</details>

<details>
<summary>
<b>Can CronJobs be used for running backups?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>Because it is not guaranteed only one job will launch per execution time of its schedule, Jobs should be&nbsp;<i>_____&nbsp;</i></b>
</summary>
idempotent
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A CronJob is counted as missed if it...</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">has failed to be created at its scheduled time.</span>
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
<b>All CronJob schedules are based on the timezone of _____</b>
</summary>
the <b>kube-controller-manager</b>.
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">If a CronJob's&nbsp;</span><code>concurrencyPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;is set to&nbsp;</span><code>Forbid,</code><span style="color: rgb(34, 34, 34);">&nbsp;and it attempted to be scheduled when there was a previous schedule still running, then it would count as _____.</span></b>
</summary>
missed
</details>

<details>
<summary>
<b>Can CronJobs be used for sending e-mails?</b>
</summary>
Yes
</details>

<details>
<summary>
<b>The Job Controller counts how many jobs had missed in the last X seconds, but only if a CronJob's _____ field<b>&nbsp;</b>is set.</b>
</summary>
startingDeadlineSeconds&nbsp;
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">A _____ creates one or more Pods and ensures that a specified number of them successfully terminate.&nbsp;</span><span style="color: rgb(34, 34, 34);">As pods successfully complete, it tracks the successful completions until a certain number of successful completions is reached.</span></b>
</summary>
<span style="color: rgb(34, 34, 34);">Job</span>
</details>

<details>
<summary>
<b><span style="color: rgb(34, 34, 34);">For </span>a&nbsp;fixed completion count<span style="color: rgb(34, 34, 34);">&nbsp;Job, you should set its .spec._____ field</span></b>
</summary>
completions
</details>

<details>
<summary>
<b>_____ run a Pod a specified number of times before completing. _____ run a Pod periodically at specified times.</b>
</summary>
Jobs
CronJobs
</details>

