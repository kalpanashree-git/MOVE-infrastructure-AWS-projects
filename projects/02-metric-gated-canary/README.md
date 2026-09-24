# Project 02: Metric-Gated Canary

**Status: In progress**

## Problem
A release can pass CI and still fail under real traffic. How can a pipeline deploy a new container to one server first, judge it using live Prometheus metrics, then automatically promote it, or roll back and alert, without a human watching?

## Planned design
- GitHub Actions builds a Docker image and deploys it to App2 (canary).
- The pipeline generates traffic for 3 minutes, then queries Prometheus for error rate, p95 latency and memory.
- Healthy: promote to App1. Unhealthy: roll back to the previous image and send an Alertmanager notification.
- If metrics cannot be read, the release fails (fail closed).

## Tools
GitHub Actions, Docker, Prometheus, Grafana, Alertmanager, Node Exporter, Bash

## Progress
- [ ] Monitoring foundation (Node Exporter, Prometheus, Grafana)
- [ ] Demo app in Docker with its own metrics
- [ ] CI pipeline
- [ ] Image registry and self-hosted runner
- [ ] Canary deploy, metric gate, promote or rollback
- [ ] Alerting and dashboard
- [ ] Failure scenarios, incident reports and runbooks

Evidence (screenshots, reports) will be added as each step is completed.

