---
title : "Create Secure Vault"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

#### Eliminate Hard-coding with AWS Secrets Manager
To strictly adhere to enterprise-grade security compliance, the Backend source code must not contain any usernames, database credentials, or API encryption keys in plaintext. Instead, we abstract these sensitive parameters into a centralized electronic vault using AWS Secrets Manager.

1. Navigate to the **AWS Secrets Manager Console** and select **Store a new secret**.
2. Under **Secret type**, choose **Other type of secret**.
3. In the **Key/value pairs** section, declare the dynamic environment configurations for the application runtime:
   + `DB_USER` : `pawverse`
   + `DB_PASS` : `pawverse123Secret`
   + `JWT_SECRET` : `mySecretKeyForJwtTokenInPawVerseApplication2026`

![Create AWS Secrets Manager](/images/5-Workshop/5.4-Database-Security/secrets-manager.png)
*Figure 5.4.1.1: Storing database connection strings and JWT Secrets as encrypted Key/Value pairs.*

4. Click **Next**. In the **Secret name** field, define the production environment identifier: `pawverse-prod-secrets`.
5. Leave all other configurations at their default parameters, scroll to the bottom, and click **Store** to successfully provision the secure vault.