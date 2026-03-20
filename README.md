<div align="center">

# 🧊 Personal Talos Kubernetes Cluster

*A self-hosted, GitOps-driven Kubernetes cluster built on Talos Linux, focused on reliability, observability, and clean automation.*

[![Talos](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.vyltech.com%2Ftalos_version&style=for-the-badge&logo=talos&logoColor=orange&label=%20&color=teal)](https://www.talos.dev/)&nbsp;&nbsp;
[![Kubernetes](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.vyltech.com%2Fkubernetes_version&style=for-the-badge&logo=kubernetes&logoColor=orange&label=%20&color=teal)](https://www.kubernetes.io/)&nbsp;&nbsp;
[![Flux](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.vyltech.com%2Fflux_version&style=for-the-badge&logo=flux&logoColor=orange&label=%20&color=teal)](https://fluxcd.io)&nbsp;&nbsp;

</div>

---

## 📌 Overview

This repository contains the full **GitOps-managed configuration** for my personal Kubernetes cluster.
The cluster runs on **Talos Linux** and is fully declarative: every component, application, and configuration is defined in Git and continuously reconciled using **FluxCD**.

Key goals of this setup:

* 🔁 **Reproducibility** – rebuild the entire cluster from Git
* 🔒 **Immutability & Security** – minimal OS, no SSH, API-driven management
* 📈 **Observability** – metrics, alerts, and public status visibility
* 🤖 **Automation-first** – updates, deployments, and testing without manual intervention

---

## 🧩 Core Components

| Component          | Description                                                                        |
| ------------------ | -----------------------------------------------------------------------------------|
| **Kubernetes**     | Container orchestration platform for running and managing workloads                |
| **Talos Linux**    | Immutable, API-driven Linux distribution purpose-built for Kubernetes              |
| **FluxCD**         | GitOps operator used for continuous reconciliation of cluster state                |
| **Mend Renovate**  | Automatically tracks and updates container images and dependencies                 |
| **GitHub Actions** | CI pipelines for validation, linting, and testing of cluster configs               |
| **SOPS**           | Encryption of all secrets and credentials stored in Git, integrated with FluxCD    |
| **ForgeTool**    | Bootstrap tool from TrueForge used to build the basic Cluster Structure and Setup  |

---

## 🗂 Directory Structure

~~~text
clusters/
└── main/
    ├── kubernetes/   # Applications and Kubernetes workloads
    └── talos/        # Talos Linux machine and cluster configuration

repositories/
├── entries/           # Repository entry definitions
├── git/               # Flux GitRepository sources
├── helm/              # Flux HelmRepository sources
└── oci/               # Flux OCIRepository sources
~~~

---

## 🔐 Secrets Management

All secrets and credentials are stored in this repository **encrypted with SOPS**.

- Secrets are committed to Git in encrypted form
- Decryption happens inside the cluster via FluxCD
- Decryption keys are managed externally and are never stored in Git
- This enables full GitOps workflows without exposing sensitive data

---

## ☁️ Cloud & External Dependencies

| Service        | Usage                                                     |
| -------------- | --------------------------------------------------------- |
| **Cloudflare** | DNS management, registrar, and S3-compatible object storage |
| **GitHub**     | Source control, CI, and GitOps reconciliation source      |


---

## 🙏 Acknowledgements

This cluster is heavily inspired by and built upon the excellent work of:

* **TrueForge** – [https://trueforge.org/](https://trueforge.org/)
* **Home Operations** – [https://github.com/home-operations](https://github.com/home-operations)

Their open-source contributions and documentation made this setup possible.

---

> ⚠️ **Note**
> This repository is public for transparency and learning purposes. Secrets and credentials **are stored in Git in encrypted form** using **SOPS**.
> Decryption keys are managed externally and are **not** committed to the repository, ensuring sensitive values remain protected.

> 🧪 This cluster is used as a learning, testing, and long-running homelab environment.  
> Configurations may evolve as new Kubernetes, Talos, or GitOps features are evaluated.
