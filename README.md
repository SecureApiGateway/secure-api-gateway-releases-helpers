# Secure API Gateway - Releases Helpers

## Prerequisites

- Kubernetes v1.23 +
- Helm 3.0.0 +

To add the forgerock helm artifactory repository to your local machine to consume helm charts use the following;

```console
  helm repo add forgerock-helm https://maven.forgerock.org/artifactory/forgerock-helm-virtual/ --username [backstage_username]  --password [backstage_password]
  helm repo update
```

NOTE: You must have a valid [subscription](https://backstage.forgerock.com/knowledge/kb/article/a57648047#XAYQfS) to aquire the `backstage_username` and `backstage_password` values.

It is assumed that, the following components have been sucessfully built and docker images are within a docker container registry ready to be used. 

- [Secure API Gateway - Remote Consent Service](https://github.com/SecureApiGateway/secure-api-gateway-ob-uk-rcs)
- [Secure API Gateway - Remote Consent Service User Interface](https://github.com/SecureApiGateway/secure-api-gateway-ob-uk-ui)
- [Secure API Gateway - Test Bank Facility](https://github.com/SecureApiGateway/secure-api-gateway-ob-uk-rs)
- [Secure API Gateway - Test User Account Creator](https://github.com/SecureApiGateway/secure-api-gateway-ob-uk-test-data-initializer)

It is assumed that, either a deployments repo has been created containing the specific deployment overrides has been created, or if a repository are not being used they are at hand (within the instructions below it is assumed that a repo is being used)

It is assumed that all infrastructure has been created, including deploying the Cloud Instance, and that the following prerequisits have been deployed to the cluster
- [Nginx](https://kubernetes.github.io/ingress-nginx/deploy/)
- [MongoDB](https://github.com/SecureApiGateway/secure-api-gateway-releases/blob/master/third-party/Chart.yaml)

## External Secrets GSM
The [external secrets](https://external-secrets.io/v0.8.1/) Google Secrets Manager charts specify the secrets to be created in the kubernetes cluster. We use Google Secrets Manager for our secrets, but other secrets managers can be used. 

## Deployment Guide

The charts in this repo can create helm package to be pushed to the [forgerock helm artifactory](https://maven.forgerock.org). 
To publish a new version of the secure-api-gateway-helpers to the artifactory perform the following steps

- Go to [Github Actions](https://github.com/SecureApiGateway/secure-api-gateway-releases/actions/workflows/release.yaml)
- Click `Run Workflow`
  - Keep Branch as `master`
  - Add 'Release [VERSION]' as the description (optional)
  - Add [VERSION] to 'Provide release version number'
  - Click `Run Workflow`

Once the workflow has completed, a new tag and release will have been created within secure-api-gateway-release-helpers repo, and new helm packages will have been pushed to the atrifactory.

| Key | Description | Example |
|-----|-------------|---------|
| `VERSION` | Version of the charts to publish, must be unique and not already be in use | 1.0.0 |

## Support

For any issues or questions, please raise an issue within the [SecureApiGateway](https://github.com/SecureApiGateway/SecureApiGateway/issues) repository.
