# Deployment Steps

{% hint style="warning" %}
**Note:** Signer Server **v1.0.0** supports only the **RS256** signing algorithm for JWT tokens. Signer Server **v1.0.2** supports both **RS256** and **ES256**.

When using Signer Server **v1.0.0** with JWTs issued by Authentik, Authentik must be configured to issue JWTs signed with the **RS256** algorithm. Please follow the guidelines, [Configure Authentik to Use RS256](../../../operational-guidelines/user-directory-management/configure-authentik-to-use-rs256.md), to update the Authentik configuration accordingly.
{% endhint %}

As outlined in the introduction to the User Management Package, this can be deployed by both data space operators and data space participants. Because these two entities differ not only in their deployment requirements but also in the resulting system configuration, the package provides two distinct deployment modules: one for Data Space Operators and one for Data Space Participants.

This chapter covers all stages involved in deploying the User Management Package, including:

* [Hardware and Software Prerequisites to run the User Management Package](prerequisites.md)
* [Pre-installation steps](pre-installation-steps.md)
* [Deployment steps for Dataspace Operators](dataspace-operator-deployment-module-installation-steps.md)
* [Deployment steps for Dataspace Participant](dataspace-participant-deployment-module-installation-steps.md)
* [Post-installation steps](post-installation-steps.md)

