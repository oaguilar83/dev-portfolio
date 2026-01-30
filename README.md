# dev-portfolio

A comprehensive developer portfolio project showcasing frontend development and infrastructure automation skills. This repository aggregates all related repositories as Git submodules.

## Repositories

| Repository | Description |
|------------|-------------|
| [dev-portfolio-frontend](https://github.com/oaguilar83/dev-portfolio-frontend) | React portfolio website built with Vite |
| [dev-portfolio-iac](https://github.com/oaguilar83/dev-portfolio-iac) | Infrastructure as Code for AWS deployment |

## Features

### Frontend
- **Home Section** - Profile introduction with bio and social media links
- **About Me Section** - Personal background, professional summary, and skills tags
- **Projects Section** - Showcase of portfolio projects
- **Contact Form** - Email contact form powered by EmailJS
- **Responsive Design** - CSS Modules for component-scoped styling
- **Smooth Navigation** - Scroll-based navigation with active section highlighting
- **Accessibility** - Proper alt text and aria-labels for screen reader support

### Infrastructure
- **Automated Provisioning** - Terraform manages all AWS resources
- **Auto-generated SSH Keys** - RSA 4096-bit key pair created during provisioning
- **CI/CD Ready** - Security group configured for GitHub Actions automation
- **TLS Certificates** - Let's Encrypt certificates via Certbot

## Architecture Overview

```
dev-portfolio/
├── dev-portfolio-frontend/    # React + Vite portfolio website
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── sections/          # Page sections (home, about, projects, contact)
│   │   ├── hooks/             # Custom React hooks
│   │   └── data/              # Static content data
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
- Material UI (MUI) Icons
- EmailJS
- CSS Modules
- Vitest + React Testing Library
- react-hot-toast
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

### Run Tests

```bash
cd dev-portfolio-frontend
npm run test        # Watch mode
npm run test:run    # Run once
npm run test:coverage
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

### Connect to Server

After Terraform completes, use the output SSH command:

```bash
cd dev-portfolio-iac/terraform
terraform output ssh_command
```

## License

MIT
