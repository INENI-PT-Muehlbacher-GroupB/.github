<div align="center">

# 🚀 Platform Engineering Project

**A Kubernetes-based multi-tenant SaaS platform built with GitOps, Crossplane, and Infrastructure as Code.**

[![Made with Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat&logo=terraform&logoColor=white)](https://www.terraform.io/)
[![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat&logo=argo&logoColor=white)](https://argo-cd.readthedocs.io/)
[![Crossplane](https://img.shields.io/badge/Crossplane-684BC1?style=flat&logo=crossplane&logoColor=white)](https://www.crossplane.io/)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat&logo=googlecloud&logoColor=white)](https://cloud.google.com/)

</div>

---

## 📖 About

This organization hosts the source code and documentation for our **Platform Engineering** university project at **University of Applied Sciences Burgenland** in the Master's Degree **Cloud Computing Engineering**.

The goal is to design, build, and operate a cloud-native platform on **Google Kubernetes Engine (GKE)** that enables the automated, on-the-fly provisioning of multi-tenant SaaS application instances using **GitOps** and **Crossplane**.

---

## 🏗️ Architecture Overview



---

## 📦 Repositories

| Repository | Description | Visibility |
|------------|-------------|------------|
| [`platform`](https://github.com/INENI-PT-GROUP-B/platform) | General repository for documentation | 🌐 Public |
| [`platform-iac`](https://github.com/INENI-PT-GROUP-B/platform-iac) | Infrastructure as Code (Terraform) – GKE, VPC, IAM, DNS | 🌐 Public |
| [`platform-gitops`](https://github.com/INENI-PT-GROUP-B/platform-gitops) | GitOps configuration – ArgoCD apps, Helm releases | 🌐 Public |
| [`platform-crossplane`](https://github.com/INENI-PT-GROUP-B/platform-crossplane) | Crossplane XRDs & Compositions for tenant provisioning | 🌐 Public |
| [`app-backend`](https://github.com/INENI-PT-GROUP-B/app-backend) | Sample application backend (REST API) | 🌐 Public |
| [`app-frontend`](https://github.com/INENI-PT-GROUP-B/app-frontend) | Sample application frontend (SPA) | 🔒 Private |
| [`.github`](https://github.com/INENI-PT-GROUP-B/.github) | Organization-wide templates & GitHub actions for validation | 🌐 Public |

---

## 🎯 Key Features

- ✅ **Infrastructure as Code** – Fully automated cluster provisioning with Terraform
- ✅ **GitOps** – Declarative application delivery via ArgoCD
- ✅ **Multi-Tenancy** – Isolated tenant instances with network policies & resource quotas
- ✅ **Self-Service Provisioning** – Crossplane-driven SaaS instance creation
- ✅ **Secrets Management** – No plaintext secrets, powered by External Secrets Operator
- ✅ **Automated DNS & TLS** – ExternalDNS + cert-manager with Let's Encrypt
- ✅ **Security First** – Workload Identity, OIDC, least-privilege IAM

---

## 🛠️ Tech Stack

| Category | Technology |
|----------|------------|
| **Cloud** | Google Cloud Platform (GCP) |
| **Kubernetes** | Google Kubernetes Engine (GKE) |
| **IaC** | Terraform |
| **GitOps** | ArgoCD |
| **Provisioning** | Crossplane |
| **Secrets** | External Secrets Operator + Google Secret Manager |
| **DNS** | ExternalDNS + Cloud DNS |
| **TLS** | cert-manager + Let's Encrypt |
| **Database** | CloudNativePG (PostgreSQL Operator) |
| **CI/CD** | GitHub Actions |

---

## ✅ Prerequisites

Before deploying the platform, the following GCP setup must be completed.

### 1. Google Cloud Account

1. Create a Google Cloud account at [cloud.google.com](https://cloud.google.com).
2. Set up a billing account and link it to the project.
3. Create a dedicated GCP project for the platform (e.g., `ineni-pt-group-b`).


### 2. Required APIs

Enable the following APIs in the GCP project:

| API | Purpose |
|-----|---------|
| `cloudresourcemanager.googleapis.com` | Project and resource management |
| `serviceusage.googleapis.com` | API enablement via IaC |
| `iam.googleapis.com` | Service accounts, roles, IAM bindings |
| `iamcredentials.googleapis.com` | Workload Identity token exchange |
| `sts.googleapis.com` | Security Token Service (Workload Identity Federation) |
| `compute.googleapis.com` | Node pools, disks, load balancers, VPC, firewalls, static IPs |
| `container.googleapis.com` | GKE cluster management |
| `dns.googleapis.com` | Cloud DNS for ExternalDNS and cert-manager DNS-01 challenge |
| `secretmanager.googleapis.com` | Secrets backend for External Secrets Operator |
| `servicenetworking.googleapis.com` | Private service access (e.g. CloudSQL peering via Crossplane) |
| `logging.googleapis.com` | Cloud Logging (enabled by default on GKE, explicit for cost awareness) |
| `monitoring.googleapis.com` | Cloud Monitoring (bonus task, enabled by default on GKE) |

### 3. Remote State Backend

Terraform state is stored in a GCS bucket with versioning and state locking enabled.

> 🚧 **Setup details to be added.** See issue [`feat(iac): setup remote state backend (GCS)`](#).

---

## 🚀 Getting Started

To deploy the platform from scratch, follow the documentation in [`platform`](https://github.com/INENI-PT-GROUP-B/platform).

**High-level flow:**

1. Configure GCP credentials and Terraform backend
2. Run `terraform apply` in `platform-iac` → cluster + bootstrap
3. ArgoCD takes over and reconciles `platform-gitops`
4. Crossplane is ready to provision tenants on demand
5. Create a new tenant via a PR in `platform-gitops`

---

## 👥 Team

| Member | Role | GitHub |
|--------|------|--------|
| Ronald Ley | IaC Lead | [@ronaldley](https://github.com/ronaldley) |
| Marco Reeh | GitOps & CI Lead | [@marco93r](https://github.com/marco93r) |
| Alexander Mihai | Crossplane & Secrets Lead | [@mlexinho27](https://github.com/mlexinho27) |
| Patrick Prohaska | Application & DNS Lead | [@prohaskap](https://github.com/prohaskap) |

---

## 📄 License

This project is for educational purposes only.

---

<div align="center">

**Built with ❤️ by the Platform Engineering Team**

</div>