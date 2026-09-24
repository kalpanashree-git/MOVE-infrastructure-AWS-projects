# Project 03: Backup, Restore and Recovery Verification

**Status: Planned**

## Problem
If important application or configuration data disappears, or a server becomes unusable, can I actually recover it?

## Planned scope
- Back up configuration and application files to Amazon S3, with retention.]\
- Validate backups, then deliberately delete or corrupt data and perform a real restore.
- Measure RPO (potential data loss) and RTO (actual recovery time).
- Keep file recovery, application recovery and infrastructure recovery clearly separate.

**Tools:** Bash, AWS CLI, S3, IAM, Ansible

