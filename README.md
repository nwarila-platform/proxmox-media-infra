# proxmox-media-infra

Terraform-managed Proxmox ISO/media lifecycle and media catalog publishing for
Packer framework builds.

## Purpose

This repository owns the stateful Proxmox media infrastructure that supports
Packer image builds. It is separate from
`nwarila-platform/proxmox-packer-framework`, which owns the reusable Packer
workflow, Packer variable contract, and Proxmox builder implementation.

Downstream OS-template repositories should call the Packer framework reusable
workflow. They should not run this Terraform root as part of normal image
validation or image builds.

## Scope

This repo owns:

- Proxmox ISO/media lifecycle Terraform.
- Terraform provider and CLI version pins for that lifecycle.
- Input examples for media/storage settings.
- Future media catalog generation and publishing.

This repo does not own:

- Packer reusable workflows.
- Packer template or builder implementation.
- OS installer templates.
- Ansible roles, playbooks, or hardening content.

## Layout

```text
proxmox-media-infra/
|-- examples/
|   `-- terraform/
|-- terraform/
|   |-- data.tf
|   |-- locals.tf
|   |-- outputs.tf
|   |-- providers.tf
|   |-- resources.tf
|   |-- variables.tf
|   `-- versions.tf
`-- README.md
```

## Local Validation

```bash
cd terraform
terraform init -backend=false
terraform fmt -check -recursive .
terraform validate
```
