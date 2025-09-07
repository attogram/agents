[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > Workflow Scheduling

# Scheduling Workflows with Cron

GitHub Actions allows you to automate tasks on a schedule, similar to the
traditional cron utility in Unix-like systems.
This is useful for recurring tasks like nightly builds, daily reports, or
weekly dependency checks.

## How it Works

You can trigger a workflow to run at specific UTC times using the `schedule`
event.
This event is configured with a `cron` expression.

```yaml
on:
  schedule:
    - cron: "30 5 * * 1-5"
```

This example triggers the workflow at 5:30 AM UTC every day from Monday to
Friday.

## Understanding Cron Syntax

A cron expression is a string of five fields that represent a time schedule.

```
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday)
│ │ │ │ │
│ │ │ │ │
* * * * *
```

### Special Characters

- `*`: Matches any value.
  `* * * * *` runs every minute.
- `,`: Separates multiple values.
  `0,15,30,45 * * * *` runs at minutes 0, 15, 30, and 45.
- `-`: Defines a range of values.
  `0 9-17 * * *` runs every hour from 9 AM to 5 PM.
- `/`: Specifies a step value.
  `*/15 * * * *` runs every 15 minutes.

### Examples

| Cron Expression   | Description                                        |
| ----------------- | -------------------------------------------------- |
| `0 0 * * *`       | Run at midnight UTC every day.                     |
| `0 9 * * 1`       | Run at 9:00 AM UTC every Monday.                   |
| `0 * * * *`       | Run at the beginning of every hour.                |
| `*/30 9-17 * * *` | Run every 30 minutes between 9 AM and 5 PM UTC.    |
| `0 0 1 * *`       | Run at midnight UTC on the first day of the month. |

## Example Workflow

Here is a complete example of a workflow that runs a script every day at
midnight UTC.

```yaml
# .github/workflows/nightly-build.yml
name: Nightly Build

on:
  schedule:
    - cron: "0 0 * * *"
  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository
        uses: actions/checkout@v3

      - name: Run nightly script
        run: ./scripts/run-nightly.sh
```

## Best Practices

1.  **Use UTC:** All scheduled times are in Coordinated Universal Time (UTC).
    Be sure to account for time zone differences.

2.  **Minimum Frequency:** The shortest interval you can schedule a workflow to
    run is every 5 minutes.

3.  **Use `workflow_dispatch`:** It's a good practice to add
    `workflow_dispatch` alongside `schedule`.
    This allows you to manually trigger the workflow from the GitHub UI, which
    is very useful for testing.

4.  **Be Mindful of Usage:** Scheduled workflows consume your GitHub Actions
    minutes.
    If a task doesn't need to run frequently, choose a longer interval.

5.  **Handle Failures:** Consider adding a step to your workflow to send a
    notification (e.g., via email or Slack) if a scheduled job fails.
    This way, you can quickly address any issues.

By leveraging scheduled workflows, you can automate a wide range of
maintenance and operational tasks, helping to keep your project healthy and
up-to-date.
