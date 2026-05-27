# Reset token in Microsoft Entra

### Manage user authentication options <a href="#manage-user-authentication-options" id="manage-user-authentication-options"></a>

[Authentication Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#authentication-administrator) can require other users to reset their password, re-register for MFA, or revoke the user's sessions. Users can't update their own user object. To change or reset their own security methods, users can go to [Security info](https://aka.ms/security-info), or go to [self-service password reset](https://aka.ms/sspr) to reset their password. To manage other user's settings, complete the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Authentication Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#authentication-administrator).
2. Browse to **Entra ID** > **Users**.
3. Choose the user you wish to perform an action on and select **Authentication methods**. At the top of the window, then choose one of the following options for the user:
   * **Reset password** resets the user's password and assigns a temporary password that must be changed on the next sign-in.
   * **Require re-register MFA** deactivates the user's hardware OATH tokens and deletes the following authentication methods from this user: phone numbers, Microsoft Authenticator apps and software OATH tokens. If needed, the user is requested to set up a new MFA authentication method the next time they sign in.
   * **Revoke sessions** invalidates a user's refresh tokens, forcing reauthentication across active sessions and applications. (this just makes them reauth with text, email or auth app)

