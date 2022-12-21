## Rotate AWS SecretsManager Secrets Automatically

### How To Set Up?

1) Enable rotation on your AWS SecretsManager secret and use Lambda as the function.
2) Use the script in this repo as your Python Lambda code.
3) In your Lambda, set `SECRETS_MANAGER_ENDPOINT` environment variable and point it to your AWS SecretsManager endpoint.

### Example

## Rotate AWS CodeArtifact auth tokens using this script

```
CODEARTIFACT_AUTH_TOKEN = boto3.client('codeartifact').get_authorization_token(domain="your-domain", domainOwner="your-account-id", durationSeconds=12 * 3600)["authorizationToken"]
service_client.put_secret_value(SecretId=arn, ClientRequestToken=token, SecretString=CODEARTIFACT_AUTH_TOKEN, VersionStages=['AWSPENDING'])
```