# Connect Azure to Google Admin console

To achieve this, you'll need to set up Automatic User Provisioning (using SCIM) alongside SAML-based SSO in Microsoft Entra ID (formerly Azure AD). This makes Entra ID your "Source of Truth"—when you add a user to the Entra application, they are created in Google; when you remove them, they are suspended or deleted in Google.

### Phase 1: Enable API Access in Google

Before Entra can "talk" to Google to create users, you must grant it permission.

1. Sign in to the Google Admin Console.
2. Go to Security > Access and data control > API controls.
3. Ensure Trust internal, domain-owned apps is selected (or specifically trust the Microsoft Office 365 app later).
4. You will also need a Super Admin account to authorize the connection from the Azure side.

### Phase 2: Add the Google Connector in Entra ID

1. Log in to the Microsoft Entra admin center.
2. Navigate to Identity > Applications > Enterprise applications > New application.
3. Search for and select Google Cloud / G Suite Connector by Microsoft.
4. Click Create.

### Phase 3: Configure Automatic Provisioning

This is the part that handles the "create/remove" logic.

1. In your new Google app in Entra, select Provisioning from the left menu.
2. Set Provisioning Mode to Automatic.
3. Under Admin Credentials, click Authorize. This will open a Google login window—log in with your Google Super Admin account.
4. Once authorized, click Test Connection to ensure it works.
5. Under Mappings, click Provision Microsoft Entra ID Users.
   * Ensure `externalId` is mapped to `mail` or `userPrincipalName`.
   * Ensure the Delete and Create actions are enabled.
6. Set the Provisioning Status to On.

### Phase 4: Set Up Single Sign-On (SSO)

While provisioning creates the account, SSO ensures they use their Microsoft password to log in.

1. In the Entra app, go to Single sign-on > SAML.
2. Basic SAML Configuration: Enter your Google primary domain in the Identifier and Reply URL fields (e.g., `google.com/a/yourdomain.com`).
3. Download the Certificate (Base64) and copy the Login URL.
4. In the Google Admin Console, go to Security > Authentication > SSO with third-party IdP.
5. Click Add SAML Profile, upload the certificate, and paste the Login URL from Entra.

#### Important Considerations

* Licensing: Provisioning creates the user, but you must ensure you have enough available licenses in Google Workspace, or the creation will fail.
* Matching ID: The `userPrincipalName` in Entra MUST match the primary email address you want the user to have in Google.
* Deprovisioning: By default, when you "delete" a user in Entra or remove them from the app scope, Entra tells Google to suspend the user rather than hard-delete them. This is a safety feature to prevent data loss (like Drive files).
