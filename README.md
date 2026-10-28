<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=3000&pause=800&color=00E5A0&center=true&vCenter=true&width=700&lines=%24+terraform+apply+-auto-approve;%24+kubectl+rollout+status+deploy%2Fapp;%24+git+push+origin+main+%26%26+watch+the+pipeline;%24+whoami+%E2%86%92+Pavan+Padamata" alt="Typing SVG" />

# `Pavan Padamata` · Cloud & DevOps Engineer

**Infrastructure as Code · CI/CD · Kubernetes · Observability · Automation**

![Profile Views](https://komarev.com/ghpvc/?username=PavanPadamata&label=profile+views&color=00e5a0&style=flat-square)
![Followers](https://img.shields.io/github/followers/PavanPadamata?style=flat-square&logo=github&color=00e5a0)

</div>

---

## `~/about`

```yaml
engineer:
  name: Pavan Padamata
  focus:
    - Cloud infrastructure & platform engineering
    - Declarative, reproducible, version-controlled everything
    - CI/CD pipelines with security shifted left
    - Observability-driven operations (SLIs / SLOs / alerts)
  principles:
    - "If it's not in Git, it doesn't exist"
    - "Automate the toil, document the rest"
    - "Immutable infrastructure over snowflake servers"
    - "Least privilege by default"
  currently:
    learning: [Kubernetes internals, GitOps, eBPF, FinOps]
    building: [Terraform modules, CI/CD templates, homelab cluster]
  reach_me: https://github.com/PavanPadamata
```

---

## `~/stack`

### ☁️ Cloud
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=FF9900)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)

### 🏗️ Infrastructure as Code & Config Management
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Packer](https://img.shields.io/badge/Packer-02A8EF?style=for-the-badge&logo=packer&logoColor=white)
![CloudFormation](https://img.shields.io/badge/CloudFormation-FF4F8B?style=for-the-badge&logo=amazonwebservices&logoColor=white)

### 📦 Containers & Orchestration
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)

### 🔁 CI/CD
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab_CI-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white)

### 📊 Observability & Security
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F5A800?style=for-the-badge&logo=grafana&logoColor=black)
![Vault](https://img.shields.io/badge/Vault-FFEC6E?style=for-the-badge&logo=vault&logoColor=black)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge&logo=aqua&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=for-the-badge&logo=sonarqubeserver&logoColor=white)

### 🧰 Languages & Systems
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)

---

## `~/architecture`

A typical delivery flow I design and operate:

```mermaid
flowchart TB
    DEV([Developer]) -->|git push| GIT[(Git repo)]
    GIT --> CI

    subgraph CI [CI pipeline]
        direction LR
        T[Lint + test] --> S[SAST + Trivy] --> B[Build + push]
    end

    CI --> REG[(Registry)]
    REG -->|tag bump| GO[GitOps repo]
    GO -->|sync| ARGO[Argo CD]
    ARGO --> K8S

    subgraph RUN [Runtime]
        direction LR
        K8S[[Kubernetes]] --> OBS[Prometheus + Grafana + Loki]
    end

    TF[Terraform] -->|provisions| CLOUD[(AWS / Azure / GCP)]
    CLOUD --> K8S
    OBS -.->|alerts| DEV
```

---

## `~/snippets`

<details>
<summary><b>Terraform</b> · remote state with locking</summary>

```hcl
terraform {
  required_version = ">= 1.6"

  backend "s3" {
    bucket         = "org-tf-state"
    key            = "prod/network/terraform.tfstate"
    region         = "ap-south-1"
    dynamodb_table = "tf-state-lock"
    encrypt        = true
  }
}
```
</details>

<details>
<summary><b>GitHub Actions</b> · build, scan, push</summary>

```yaml
name: ci
on:
  push:
    branches: [main]

permissions:
  id-token: write   # OIDC, no long-lived cloud keys
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/build-push-action@v6
        with:
          push: false
          load: true
          tags: app:${{ github.sha }}
      - uses: aquasecurity/trivy-action@master
        with:
          image-ref: app:${{ github.sha }}
          severity: CRITICAL,HIGH
          exit-code: 1
```
</details>

<details>
<summary><b>Kubernetes</b> · hardened deployment</summary>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app
spec:
  replicas: 3
  strategy:
    rollingUpdate: { maxSurge: 1, maxUnavailable: 0 }
  selector:
    matchLabels: { app: app }
  template:
    metadata:
      labels: { app: app }
    spec:
      securityContext:
        runAsNonRoot: true
        seccompProfile: { type: RuntimeDefault }
      containers:
        - name: app
          image: registry.example.com/app:1.0.0
          resources:
            requests: { cpu: 100m, memory: 128Mi }
            limits:   { cpu: 500m, memory: 256Mi }
          readinessProbe:
            httpGet: { path: /healthz, port: 8080 }
          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities: { drop: [ALL] }
```
</details>

---

## `~/stats`

<div align="center">

<img height="180" src="https://github-readme-stats.vercel.app/api?username=PavanPadamata&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&rank_icon=github" alt="GitHub stats" />
<img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=PavanPadamata&layout=donut&langs_count=8&theme=tokyonight&hide_border=true" alt="Top languages" />

<img src="https://streak-stats.demolab.com/?user=PavanPadamata&theme=tokyonight&hide_border=true" alt="GitHub streak" />

</div>
