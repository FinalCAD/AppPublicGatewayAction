# AppPublicGatewayAction

Github Action to deploy our apigateway public

## Inputs
### `app-name`
Application ID to identify the app

### `aws-role`
[**Required**] AWS role allowing Secret manager usage

### `terraform-version`
Terraform version to use, Default: latest

### `terragrunt-version`
Terragrunt version to use, Default: latest

### `application-repo`
Repository containing terraform code for applicaton resource creation, Default: FinalCAD/terraform-public-api-gateway

### `application-ref`
Reference to use for `application-repo` repository, Default: master

### `github-token`
Github token to avoid limit rate when pulling package

### `github-ssh`
[**Required**] Github ssh key to pull `application-repo` repository

### `environment`
[**Required**] Finalcad envrionment: production, staging, sandbox

### `region-friendly`
Finalcad region: `frankfurt` or `tokyo`, Default: frankfurt

### `application-file`
Path for application file definition

### `dry-run`
Dry run, will not trigger apply, Default: false

## Usage

```yaml
- name: Push secrets
  uses: FinalCAD/AppPublicGatewayAction@v1.0.0
  with:
    github-ssh: ${{ secrets.GH_DEPLOY_SSH }}
    environment: sandbox
    region-friendly: frankfurt
    aws-role: ${{ secrets.DEPLOY_ROLE_MASTER }}
    application-file: ./aws_config.yaml
```
