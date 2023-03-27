# secure-api-gateway-releases-helpers

This repo holds helm charts for packages that will aid in the running of secure-api-gateway.

## Mutating Webhook
The mutating webhooks functionality is to apply a whitelist to any ingesses within the cluster, it will also update the SSL certificates used by the ingresses if they are updated via the External Secrets package.

## External Secrets GSM
The external secrets Google Secrets Manager charts specify the secrets to be created in the kubernetes cluster. We use Google Secrets Manager for our secrets, but other secrets managers can be used. 
