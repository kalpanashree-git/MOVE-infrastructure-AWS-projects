# MOVE Infrastructure AWS projects

*Formerly "Enterprise-Linux-Operations-Platform".*

A hands-on Linux and AWS operations lab. **One shared environment, five projects, one lifecycle:**

**Operate → Patch → Observe → Detect → Troubleshoot → Recover → Validate → Prevent**

The goal is to show that I can operate, monitor, troubleshoot and recover Linux/AWS infrastructure reliably, not just that I have touched many tools.

## The lab

```
AWS VPC
 ├─ Public side : Bastion host, NAT instance
 └─ Private side: App Server 1, App Server 2, Monitoring Server
```

Free-tier sized instances (t2/t3.micro). A NAT instance is used instead of a managed NAT Gateway to keep cost at zero.
See [`infrastructure/`](infrastructure/) and [`architecture/`](architecture/) for details.

## Projects

| # | Project | Focus | Main tools | Status |
|---|---------|-------|------------|--------|
| 01 | [Patch Management and Health Validation](projects/patch%20management/) | Safe maintenance and change | Ansible, Bash, Jinja2, Linux | Complete |
| 02 | [Metric-Gated Canary](projects/02-metric-gated-canary/) | Safe releases, detection, rollback | GitHub Actions, Docker, Prometheus, Grafana, Alertmanager | In progress |
| 03 | [Backup, Restore and Recovery](projects/backup-and-disaster-recovery/) | Recovery, RTO/RPO | Bash, AWS CLI, S3, Ansible | Planned |
| 04 | [Configuration Drift Management](projects/04-config-drift/) | Consistency, access, security | Ansible, IAM, SSH, Security Groups | Planned |
| 05 | [AWS Operations and Troubleshooting](projects/05-aws-troubleshooting/) | Cloud and network troubleshooting | VPC, EC2, Security Groups, Linux tools | Planned |

### Project 01 at a glance
A pre-patch audit checks disk, load, connectivity, services and ports. A decision engine classifies each server as safe to patch, warning, or patch aborted. Servers are patched in a controlled order, then validated and reported before/after.

## Repository layout

| Folder | Contents |
|--------|----------|
| `projects/` | One self-contained folder per project, each with its own README |
| `infrastructure/` | The shared AWS lab: network, security groups, server inventory |
| `architecture/` | Diagrams for the whole lab |
| `incident-reports/` | Structured reports from controlled failures |
| `runbooks/` | Step-by-step fix guides |
| `screenshots/` | Evidence |
| `docs/` | Roadmap, conventions and learning notes |
| `scripts/` | Helpers shared by several projects |
| `.github/workflows/` | CI/CD pipelines (added with Project 02) |

## Conventions
- Each project answers one real operational problem and keeps its own README, evidence and documentation.
- Failures are created on purpose, investigated with real diagnostics, and written up as incident reports.
- Status is always honest: Complete, In progress or Planned.

Maintained by [@kalpanashree-git](https://github.com/kalpanashree-git).

