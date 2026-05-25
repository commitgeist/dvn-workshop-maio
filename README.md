# DVN Workshop — DevOps na Nuvem com Claude

Este repositório contém a infraestrutura e aplicações do workshop de **DevOps na Nuvem**, construído com o auxílio de [Claude Code](https://claude.ai) como engenheiro de plataforma.

## Visão Geral

O workshop percorre todo o ciclo de vida de uma aplicação cloud-native: infraestrutura como código, containerização, orquestração Kubernetes, CI/CD e GitOps — tudo provisionado na **AWS**.

## Arquitetura

| Stack | Descrição |
|---|---|
| `00-remote-backend-stack-ai` | Bucket S3 e DynamoDB para estado remoto do Terraform |
| `01-networking-stack-ai` | VPC multi-AZ com subnets públicas/privadas, NAT Gateway, flow logs |
| `02-eks-stack-ai` | Cluster EKS com managed node groups, ECR, add-ons |
| `03-ci-cd-stack-ai` | GitHub Actions OIDC + IAM roles |

## Estrutura

```
dvn-workshop-terraform/    # Stacks Terraform (IaC)
dvn-workshop-apps/         # Código-fonte das aplicações
├── frontend/              # Next.js
└── backend/               # .NET
dvn-workshop-kubernetes/   # Manifests Kubernetes (Deployment, Service, PDB)
docs/                      # ADRs (Architecture Decision Records)
.claude/                   # Skills e regras do Claude Code
└── skills/                # Habilidades especializadas (deploy, docker, etc.)
```

## Tecnologias

- **IaC:** Terraform (provider `hashicorp/aws`, sem módulos comunitários)
- **Orquestração:** Amazon EKS + Kubernetes
- **CI/CD:** GitHub Actions + ArgoCD (GitOps)
- **Aplicações:** Next.js (frontend) + .NET (backend)
- **Assistência:** Claude Code com agentes `devops-solution-architect` e `devops-senior-engineer`

## Pré-requisitos

- AWS CLI configurado com credentials
- Terraform >= 1.10.0
- kubectl
- Docker

## Deploy

```bash
# Deploy de uma stack específica
/terraform-deploy 01-networking-stack-ai

# Deploy de todas as stacks (sequencial)
/terraform-deploy
```

## Skills do Claude

- `terraform-deploy` — fmt, validate, plan, apply
- `dockerfile-generator` — Dockerfiles multi-stage otimizados
- `docker-push-ecr` — build e push para ECR
# dvn-workshop-maio
