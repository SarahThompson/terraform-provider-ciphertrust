# Create an Azure RSA key

This example shows how to:
- Create an Azure connection
- Create an Azure key and restore it to a different vault

These steps explain how to:
- Configure CipherTrust Manager Provider parameters required to run the examples
- Configure Azure parameters required to create Azure keys
- Run the example

## Configure CipherTrust Manager

### Use environment variables

```bash
export CM_ADDRESS=https://cm-address
export CM_USERNAME=cm-username
export CM_PASSWORD=cm-password
export CM_DOMAIN=cm-domain
```
### Use a configuration file

Create a ~/.ciphertrust/config file and configure these keys with your values.

```bash
address = https://cm-address
username = cm-username
password = cm-password
domain = cm-domain
```

### Edit the provider block in main.tf

```bash
provider "ciphertrust" {
  address  = "https://cm-address"
  username = "cm-username"
  password = "cm-password"
  domain   = "cm-domain"
}
```

## Configure Azure Credentials

### Use environment variables

```bash
export ARM_CLIENT_ID=client-id
export ARM_CLIENT_SECRET=client-secret
export ARM_TENANT_ID=tenant-id
```

### Edit the connection resource in main.tf

```bash
resource "ciphertrust_azure_connection" "azure_connection" {
  name          = "azure-connection"
  client_id     = "client-id"
  client_secret = "client-secret"
  tenant_id     = "tenant-id"
}
```

## Configure Azure Vaults

### Update Azure for all Azure examples

Update values in scripts/azure_vars.sh and run the script.

This updates all azure_vars.tf files found in the subdirectories.

### Configure for this example only

Edit azure_vars.tf in this directory and update with your values.

## Run the Example

```bash
terraform init
terraform apply
```

## Destroy Resources

Resources must be destroyed before another sample script using the same cloud is run.

```bash
terraform destroy
```
Run this step even if the apply step fails.
