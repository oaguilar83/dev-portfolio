# dev-portfolio

A comprehensive developer portfolio project showcasing frontend development and infrastructure automation skills. This repository aggregates all related repositories as Git submodules.

## Repositories

| Repository | Description |
|------------|-------------|
| [dev-portfolio-frontend](https://github.com/oaguilar83/dev-portfolio-frontend) | React portfolio website built with Vite |
| [dev-portfolio-iac](https://github.com/oaguilar83/dev-portfolio-iac) | Infrastructure as Code for AWS deployment |

## Architecture Overview

```
dev-portfolio/
├── dev-portfolio-frontend/    # React + Vite portfolio website
│   ├── src/                   # React components and styles
│   ├── public/                # Static assets
│   └── .github/workflows/     # CI/CD pipelines
└── dev-portfolio-iac/         # Infrastructure automation
    ├── terraform/             # AWS resources (EC2, Route53, Security Group, Key Pair)
    └── ansible/playbooks/     # Server configuration (Nginx, TLS)
```

## Tech Stack

### Frontend
- React 19
- Vite 7
- Material UI (MUI) + MUI Icons
- EmailJS
- GitHub Actions (CI/CD)

### Infrastructure
- Terraform (AWS: EC2, Route53, Security Groups, Key Pair)
- Ansible (Nginx, Certbot/Let's Encrypt)
- Ubuntu 24.04 LTS

## Getting Started

### Clone with Submodules

```bash
# Clone repository with all submodules
git clone --recurse-submodules https://github.com/oaguilar83/dev-portfolio.git

# Or if already cloned, initialize submodules
git submodule update --init --recursive
```

### Update Submodules

```bash
# Pull latest changes for all submodules
git submodule update --remote --merge
```

## Quick Start

### Run Frontend Locally

```bash
cd dev-portfolio-frontend
npm install
npm run dev
```

### Deploy Infrastructure

```bash
# Provision AWS resources (generates SSH key automatically)
cd dev-portfolio-iac/terraform
terraform init && terraform apply

# Configure server
cd ../ansible
export SSH_PRIVATE_KEY_FILE=../terraform/dev-portfolio-key.pem
ansible-playbook -i inventory playbooks/install_nginx.yml
ansible-playbook -i inventory playbooks/install_tls_cert.yml
```

## License

MIT
