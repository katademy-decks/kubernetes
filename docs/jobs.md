<details>
	<summary>
		A CronJob is counted as _____ if its concurrencyPolicy is set to Forbid, and it attempted to be scheduled when there was a previous schedule still running.
	</summary>
		missed
</details>

<details>
	<summary>
		A job's _____ is the number of Pods it may run at the same time. By default, it is set to 1.
	</summary>
		parallelism
</details>

<details>
	<summary>
		If a Job's parallelism is set to 0, the Job is _____.
	</summary>
		paused until Parallelism is increased
</details>

<details>
	<summary>
		Every dependent (i.e. owned) object has a metadata._____ field that points to the owning object (usually a Controller). You can specify relationships between owners and dependents by manually setting the field.
	</summary>
		ownerReferences
</details>

<details>
	<summary>
		A _____ runs a Pod periodically at specified times.
	</summary>
		CronJob
</details>

<details>
	<summary>
		All CronJob schedules are based on the timezone of the _____.
	</summary>
		kube-controller-manager
</details>

<details>
	<summary>
		"A CronJob is counted as ""_____"" if it has failed to be created at its scheduled time."
	</summary>
		missed
</details>

<details>
	<summary>
		A _____ run a Pod a specified number of times before completing.
	</summary>
		Job
</details>

<details>
	<summary>
		A _____ creates one or more Pods and ensures that a specified number of them successfully terminate. The minimum required number of completions is configured via the Job's .spec.completions field.
	</summary>
		Job
</details>

<details>
	<summary>
		A CronJob is counted as missed if its concurrencyPolicy is set to _____, and it attempted to be scheduled when there was a previous schedule still running.
	</summary>
		Forbid
</details>

<details>
	<summary>
		Jobs on a repeating schedule are called _____
	</summary>
		CronJobs
</details>

<details>
	<summary>
		A single _____ object is similar to a single line of a crontab file.
	</summary>
		CronJob
</details>

<details>
	<summary>
		A job's parallelism is the number of _____ it may run at the same time. By default, it is set to 1.
	</summary>
		Pods
</details>

<details>
	<summary>
		A Job creates one or more Pods and ensures that a specified number of them successfully terminate. The minimum required number of completions is configured via the Job's .spec._____ field.
	</summary>
		completions
</details>

<details>
	<summary>
		If a Job's parallelism is set to _____, the Job is paused until Parallelism is increased.
	</summary>
		0
</details>

<details>
	<summary>
		A single CronJob object is similar to a single line of a _____ file.
	</summary>
		crontab
</details>

