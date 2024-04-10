## Custom Vault Connector

The `SampleVaultConnector` provides a custom vault connector implementation for managing secrets within a vault, extending the capabilities of the Saviynt Security Manager (SSM). This connector implements essential methods such as `getSecret()`, `setSecret()`, `displayName()`, `version()`, and `setVaultConfig()`, alongside an optional `dataFormatting()` method for additional data manipulation.

## Features

- **Secret Management**: Securely fetch and store secrets in a vault.
- **Dynamic Configuration**: Dynamically set vault configuration through the UI, enabling customization according to specific requirements.
- **Custom Encryption**: Support for custom encryption mechanisms during secret storage and retrieval.
- **Connection Testing**: Includes methods for testing the connectivity with the vault, ensuring reliability and correctness.

## Prerequisites

- Java 8 or later.
- Access to a vault that supports the necessary API operations for secret management.
- Saviynt SSM framework for integration.

## Installation

1. Ensure Java 8 or higher is installed on your system.
2. Clone this repository or download the source code.
3. Build the project using your preferred Java build tool (e.g., Maven or Gradle).
4. Deploy the resulting artifact into your Saviynt SSM environment.

## Usage

### Setting Up Vault Configuration

To configure the vault connection, use the `setVaultConfig(VaultConfigVo configData)` method. Define connection attributes, encrypted attributes, and required attributes according to your vault's API documentation.

Example:

```java
VaultConfigVo configData = new VaultConfigVo();
configData.addConnectionAttribute("AUTH_URL", "https://example.com/auth");
configData.addEncryptedConnectionAttribute("Password", "your_password_here");
// Add more configuration as needed
sampleVaultConnector.setVaultConfig(configData);
```
### Setting Up Vault Configuration

To store a secret in the vault, use the setSecret(Map<String, Object> vaultConfigData, Map<String, Object> data) method. Pass the necessary vault configuration and the secret to be stored.

```java
Map<String, Object> vaultConfigData = new HashMap<>();
Map<String, Object> data = new HashMap<>();
// Configuration and data setup
Map result = sampleVaultConnector.setSecret(vaultConfigData, data);
```

### Fetching Secrets

To retrieve a secret from the vault, use the `getSecret(Map<String, Object> vaultConfigData, Map<String, Object> data)` method. Provide the appropriate configuration and the name of the secret to be retrieved.

```java
Map<String, Object> vaultConfigData = new HashMap<>();
Map<String, Object> data = new HashMap<>();
// Configuration and data setup
Map result = sampleVaultConnector.getSecret(vaultConfigData, data);
```

### Customizing Data Formatting

The dataFormatting(Map vaultConfigData) method can be overridden to customize the format of vault configuration data before it is passed to getSecret() or setSecret() methods.

### Testing Connectivity

To test the connectivity with your vault, use the test(Map<String, Object> vaultConfigData, Map<String, Object> data) method. It should return a map indicating the status of the connection.

### Contributions

Contributions are welcome. Please submit pull requests or open issues to propose changes or report bugs.

License

This README.md provides a foundational guide for users and developers to understand, set up, and utilize the `SampleVaultConnector`. Ensure to customize it with specific details about your vault setup, prerequisites, and additional functionalities as needed.
