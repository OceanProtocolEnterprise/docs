# Configure Authentik to Use RS256

### Overview

For **Authentik 2026.8.0**, configure the OAuth2/OpenID provider associated with the `oe-market-demo` application to use an RSA signing key, authenticated as `akadmin`.

Selecting a signing key configures Authentik to sign JWTs asymmetrically using the private key associated with the selected certificate. The corresponding public key is exposed through the provider's configuration endpoint for [token verification](configure-authentik-to-use-rs256.md#verification).

### Procedure

1. Authenticate in Authentik Dashboard as `akadmin` , Administrator account which was created at [initial setup](../../infrastructure/user-management-package/deployment-steps/post-installation-steps.md#set-the-authentik-server-administrator-account).
2. Navigate to **Applications → Providers** and search for the OIDC provider associted with the application.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.07.44.png" alt="" width="437"><figcaption></figcaption></figure>

3. Edit the OAuth2/OpenID provider.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.12.31.png" alt="" width="366"><figcaption></figcaption></figure>

3. Expand **Advanced protocol settings** and locate **Signing Key**.
4. Select an **RSA certificate/key pair**. For example, select **`authentik Self-signed Certificate`** if it uses an RSA key.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.15.21.png" alt=""><figcaption></figcaption></figure>

5. Save the provider configuration.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.16.38.png" alt=""><figcaption></figcaption></figure>

### Verification

1. Access `.well-known` configuration URL associated with OIDC provider.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.11.15.png" alt=""><figcaption></figcaption></figure>

2. Check `id_token_signing_alg_values_supported`  to be `RS256` .

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-28 at 12.07.57.png" alt=""><figcaption></figcaption></figure>

### Troubleshooting

After applying the configuration, verify the Signer Server authentication flow. If the following error is returned in the browser **DevTools**:

```
{
  "statusCode": 401,
  "timestamp": "2026-09-22T12:37:22.940Z",
  "path": "/api/v1/available-networks",
  "message": "Invalid or missing Authentik token"
}
```

Check the signing certificate configured for the Authentik provider:

* If a **custom certificate** is currently selected, switch the **Signing Key** to **`authentik Self-signed Certificate`**, provided it is an RSA certificate, and test the authentication flow again.
* If **`authentik Self-signed Certificate`** is selected and the error persists, try selecting the configured **custom RSA certificate** instead and test again.

The important requirement for Signer Server **v1.0.0** is that the JWT is signed using an **RSA key**, allowing it to be validated using the **RS256** algorithm.

