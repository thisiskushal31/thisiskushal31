# Grid Platform

**Open-source, self-hosted control plane** for infrastructure you describe in Git.

- **Status:** In active development
- **Site:** https://gridplatform.org
- **GitHub:** https://github.com/gridplatform
- **Role:** Author and maintainer

## What it is

You write what should exist as JSON in a repository you own. A unit is a project, a cloud, an environment, and a type. Grid syncs that tree and runs plan, apply, and destroy the same way on every cloud. Each cloud has its own catalog of types Grid builds there.

You run Grid on your own machine. It is not a hosted service. Terraform and Kubernetes stay the engines. Grid is the control plane around them.

## Features

- **Intent in Git.** Path-shaped JSON is the source of truth. Sync pulls it into inventory. A file that disappears is marked stale. Destroy is a separate release.
- **One release path.** Plan, apply, and destroy, with live logs, audit, and environment approvals.
- **A catalog for each cloud.** The path shape is the same. The types belong to that cloud.
- **Terraform engine.** Generate from the module bank, keep remote state, and write plain Terraform under `archive/` so the unit stays portable.
- **Kubernetes engine.** Managed clusters and node pools are Terraform units. Workloads inside a cluster are GitOps (Argo CD / OpenShift GitOps) on the same release path.
- **Console.** Infrastructure, Deployments, Releases, Topology, Monitoring, Alerts, and Admin.
- **Auth.** Local users, groups, roles, and approval policy per environment. Private Git remotes use a username, a host token, and an expiry. SSH remotes use a deploy key on the host.
- **State and monitoring.** One remote state backend for the control plane, independent of which cloud a unit targets. Prometheus and Alertmanager run on the host.
- **Install.** Pin a release tag. Compose or a VM install script brings up the control plane.

## How it is built

| Piece | Role |
|-------|------|
| grid-core | API, Sync, releases, auth, install |
| grid-ui | Console |
| grid-cli | Generate, plan, apply, destroy |
| grid-terraform | Module bank, one folder per cloud |
| Your Git repository | Intent. The public sample tree is only an example |

## Links

[Website](https://gridplatform.org) · [Organization](https://github.com/gridplatform) · [Docs](https://github.com/gridplatform/grid-docs) · [Architecture diagram](architecture-diagram.mmd)
