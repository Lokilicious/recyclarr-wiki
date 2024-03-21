---
id: migration
title: Migration System
---

The Migration System allows Recyclarr to attempt certain automatic actions for the user. These
actions, referred to as Migration Steps, are usually in response to certain changes between releases
of Recyclarr (mostly major releases, which represent breaking changes). The overall goal of this
system is to reduce the amount of manual action a user must take.

## Behavior

The migration system is built into two distinct parts:

- When a [sync] is executed, all of the migration steps are checked to see if actions need to be
  performed. The user will be notified if there is any work to perform. No actions are taken
  automatically for users. If any migration steps are required, the `sync` command will not run
  until those migration steps are executed.
- The [`migrate`][mig] command executes all migration steps that have work to do.

Migration Steps can fail. When this happens, instructions are provided to the user on how to recover
and/or perform those steps manually. Regardless of the reason, Recyclarr will immediately exit and
cannot proceed until the advice output during the previous execution is followed.

[sync]: ../cli/sync.md
[mig]: ../cli/migrate.md

## Failure & Recovery

When a Migration Step fails, processing of further steps is halted and the program exits. The
failure also results in diagnostic information and remediation steps being printed to the console:

- A description of the Migration Step that failed. This is usually a description of what the step
  was trying to do.
- A failure reason. Explains why the step failed and could not be processed.
- Remediation steps. One or more ways to solve the problem. Will likely either ask you to perform
  the steps by hand or take some action to allow the migration step to succeed the next time
  Recyclarr is executed.
