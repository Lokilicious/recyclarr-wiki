---
id: help
title: Getting Help
---

:::caution

Recyclarr may stop working at any time due to guide updates and changes in either Radarr or Sonarr.
It is a priority to fix them in a timely manner. [Reporting][issues] such issues ASAP would be
appreciated and will help identify problems more quickly.

[issues]: https://github.com/recyclarr/recyclarr/issues

:::

## Before Asking for Help

:::tip Help me, help you!

Please make an effort to read this section. You might not get any help you if you don't provide
enough detail or ask the right questions.

:::

Recyclarr has an amazing support community full of people happy to help you with any questions you
may have. However, the time of those that provide support is limited. You can get the most out of
your time and the best answer to your questions by doing some due diligence. Please understand that
this is an open source project and completely free to you. You are expected to put in some self-help
effort before seeking help or reporting issues.

Please review the checklist below and ensure you have done the following.

- **Read the documentation!**
- If you need help with an error or warning message, check the [Errors &
  Warnings](errors-warnings.md) page.
- Search the Github [issues] and [discussion] sections for existing answers to your questions or to
  see if your issue has already been reported.
- If you are getting errors, *read the error messages and try to understand them!* Many of
  Recyclarr's error messages are designed to be human-readable.

[discussion]: https://github.com/recyclarr/recyclarr/discussions

## How to Get Help

Thank you for reading the previous section and attempting to self-help before reaching out. There
are a few ways to get help, listed below.

- The `#recyclarr` support channel in the [TRaSH Discord][discord] community.
- Start a [discussion] on Github.

Please refer to the sections below on how to obtain logs and/or provide your configuration YAML.
Both of these may be necessary when requesting help and **will be required** if you are reporting an
issue.

[discord]: https://discord.com/invite/Vau8dZ3

### Obtaining Debug Logs

Recyclarr always outputs logs as files in a directory on your filesystem. Each execution of
Recyclarr yields a new file and those files always contain debug logs. You should always include
logs from the file rather than the command line output since Recyclarr will not include debug logs
by default in the console output.

Below is a list of locations where you can find the log directory depending on platform.

| Platform | Location                                       |
| -------- | ---------------------------------------------- |
| Windows  | `%APPDATA%\recyclarr\logs`                     |
| Linux    | `~/.config/recyclarr/logs`                     |
| MacOS    | `~/Library/Application Support/recyclarr/logs` |
| Docker   | `/config/logs`                                 |

Within the log directory is a `cli` directory which contains logs specific to the Recyclarr CLI.
Each run of Recyclarr outputs two files:

- `debug.log`: This is the most important file. This should always be shared.
- `verbose.log`: Contains very noisy information that is sometimes, but not always, useful. You
  should not provide this file unless it is explicitly requested, especially for help requests.

:::info

Information in log files such as service host names and API keys are always redacted automatically
by Recyclarr.

:::

### Redacting Configuration YAML {#redact-config}

:::tip

Use [secrets](/yaml/secrets-reference.md) so you don't have to do this by hand!

:::

Your `recyclarr.yml` and other custom configuration YAML files contain sensitive information. In
particular, the Base URL and API Key for each service you've configured. Typically you won't want
this information shared to others when you request help or file bug reports on Github. As such, you
should ensure that this information is redacted. You can do this in multiple ways.

- Use [secrets](/yaml/secrets-reference.md) (requires `v3.0` or higher)
- Manually edit your YAML before sharing it to redact `base_url` and `api_key` values.

## Reporting Issues

If you feel you have identified a defect *or* you would like to request a feature or enhancement,
you may do so on the Github [issues] page. Please **do not skip the issue template**! If you skip
questions or put in minimal effort, your issue may be immediately closed with no further
consideration.
