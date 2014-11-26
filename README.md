Runbook Webhook
===============

This repo is home to `cr-webhook.sh` which is a simple shell script designed to interact with [Runbook](https://runbook.io), a monitoring and automation SaaS.

This script simply uses `curl` to make an HTTP POST that updates a `webhook` monitor on Runbook. This script can change the webhooks status to either **Healthy** or **Failed**. It can also check the status of a monitor using the status action, which isn't very webhooky but that's ok.

**Usage:**

    # ./cr-api.sh -k <check_key> -u <url> -a healthy|failed|status

**Changing a monitor to healthy state:**

    # ./cr-api.sh -u https://dash.runbook.io/api/cr-api/unique-url -k somesupersecretkey -a healthy
    Sending Request to: https://dash.runbook.io/api/cr-api/unique-url
    -------------------------
    Results: {"result": "success"}

**Changing a monitor to failed state:**

    # ./cr-api.sh -u https://dash.runbook.io/api/cr-api/unique-url -k somesupersecretkey -a failed
    Sending Request to: https://dash.runbook.io/api/cr-api/unique-url
    -------------------------
    Results: {"result": "success"}

**Checking monitor state:**

    # ./cr-api.sh -u https://dash.runbook.io/api/cr-api/unique-url -k somesupersecretkey -a status
    Sending Request to: https://dash.runbook.io/api/cr-api/unique-url
    -------------------------
    Results: {"status": "failed", "failcount": 0, "result": "success"}

## Examples in the wild

Below is a list of examples of using `cr-webhook.sh` with existing tools.

* [nginx health checker](https://gist.github.com/madflojo/53b221dcfe1b0289e5b4)
