# Jobs 

<details>
<summary><span style="color: rgb(34, 34, 34);">Suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;</span><code>08:30</code><span style="color: rgb(34, 34, 34);">, and its&nbsp;</span><code>startingDeadlineSeconds</code><span style="color: rgb(34, 34, 34);">&nbsp;field is not set. If the CronJob controller happens to be down from&nbsp;</span><code>08:29</code><span style="color: rgb(34, 34, 34);">&nbsp;to&nbsp;</span><code>10:21</code><span style="color: rgb(34, 34, 34);">, what happens to the job?</span></summary>
<span style="color: rgb(34, 34, 34);">The job will not start.&nbsp;</span><span style="color: rgb(34, 34, 34);">The number of missed jobs which missed their schedule is greater than 100.</span>
<br></details><details>
<summary>Suppose a CronJob is set to schedule a new Job every one minute beginning at&nbsp;<code>08:30</code>, and its&nbsp;<code>startingDeadlineSeconds</code>&nbsp;is set to 200 seconds. If the CronJob controller happens to be down between&nbsp;<code>08:29</code>&nbsp;to&nbsp;<code>10:21,</code>&nbsp;the Job will still start at _____.&nbsp;</summary>
10:22
This happens as the controller checks how many missed schedules happened in the last 200 seconds (ie, 3 missed schedules).
<br></details><details>
<summary>Jobs on a repeating schedule are called...</summary>
CronJobs
<br></details><details>
<summary>One CronJob object is like one line of a _____ file. It runs a job periodically on a given schedule, written in Cron format.</summary>
crontab
<br></details><details>
<summary>Can CronJobs be used for running backups?</summary>
Yes
<br></details><details>
<summary>Because it is not guaranteed only one job will launch per execution time of its schedule, Jobs should be&nbsp;<i>_____&nbsp;</i></summary>
idempotent
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A CronJob is counted as missed if it...</span></summary>
<span style="color: rgb(34, 34, 34);">has failed to be created at its scheduled time.</span>
<br></details><details>
<summary>A job's default parallelism value is 1.<span style="color: rgb(34, 34, 34);">&nbsp;If it is specified as 0, then the Job...</span></summary>
<span style="color: rgb(34, 34, 34);">Is paused until it is increased.</span>
<br></details><details>
<summary>A job's parallelism is...</summary>
<span style="color: rgb(34, 34, 34);">The number of Job pods running at any instant.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The _____ provides a TTL (time to live) mechanism to limit the lifetime of resource objects that have finished execution.</span></summary>
<span style="color: rgb(34, 34, 34);">TTL controller</span>
<br></details><details>
<summary>The&nbsp;<span style="color: rgb(34, 34, 34);">TTL controller handles what resource?</span></summary>
Jobs
<br></details><details>
<summary>All CronJob schedules are based on the timezone of _____</summary>
the <b>kube-controller-manager</b>.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If a CronJob's&nbsp;</span><code>concurrencyPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;is set to&nbsp;</span><code>Forbid,</code><span style="color: rgb(34, 34, 34);">&nbsp;and it attempted to be scheduled when there was a previous schedule still running, then it would count as _____.</span></summary>
missed
<br></details><details>
<summary>Can CronJobs be used for sending e-mails?</summary>
Yes
<br></details><details>
<summary>The Job Controller counts how many jobs had missed in the last X seconds, but only if a CronJob's _____ field<b>&nbsp;</b>is set.</summary>
startingDeadlineSeconds&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A _____ creates one or more Pods and ensures that a specified number of them successfully terminate.&nbsp;</span><span style="color: rgb(34, 34, 34);">As pods successfully complete, it tracks the successful completions until a certain number of successful completions is reached.</span></summary>
<span style="color: rgb(34, 34, 34);">Job</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">For </span>a&nbsp;fixed completion count<span style="color: rgb(34, 34, 34);">&nbsp;Job, you should set its .spec._____ field</span></summary>
completions
<br></details><details>
<summary>_____ run a Pod a specified number of times before completing. _____ run a Pod periodically at specified times.</summary>
Jobs
CronJobs
<br></details>