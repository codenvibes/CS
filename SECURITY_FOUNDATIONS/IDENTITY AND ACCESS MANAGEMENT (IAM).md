
| Identity       | the set of things that define or characterize someone or something such, as their username and password and their level of authorization.    |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Authorization  | Denying or granting access to a user after Authentication by determining the level of access or the permissions an authenticated person has. |
| Authentication | Authentication is the process of proving that a person is who they claim they are.                                                           |

---
# Identity Infrastructure
The architecture and technologies that manage the identity lifecycle, authentication, authorization, and governance of user access.

## Four pillars of an identity infrastructure

| **Administration** | Administration is about the creation and management/governance of identities for users, devices, and services. As an administrator, you manage how and under what circumstances the characteristics of identities can change (be created, updated, deleted). |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Authentication** | The authentication pillar tells the story of how much an IT system needs to know about an identity to have sufficient proof that they really are who they say they are. It involves the act of challenging a party for legitimate credentials.<br>           |
| **Authorization**  | The authorization pillar is about processing the incoming identity data to determine the level of access an authenticated person or service has within the application or service that it wants to access.                                                   |
| **Auditing**       | The auditing pillar is about tracking who does what, when, where, and how. Auditing includes having in-depth reporting, alerts, and governance of identities.                                                                                                |

___

# Modern Authentication

## IDP (Identity Provider)
- A trusted service that **authenticates users** and **issues identity tokens**.
- Examples: ==**Azure AD**, **Google**, **Auth0**, **Okta**, **Keycloak**.==
## Token
- A compact, digitally signed string that **represents the user's identity and permissions**.
- Common types:
    - **ID Token**: Provides identity information about the user (via OIDC).
    - **Access Token**: Grants access to a resource (via OAuth 2.0).
    - **Refresh Token**: Used to obtain new tokens without re-authenticating.
	Tokens usually follow the **JWT (JSON Web Token)** format.
## Claims
- **Key-value pairs** embedded inside tokens.
- They carry information about the user and the authentication session.
- Examples of claims:
    - `sub`: Subject (user ID)    
    - `iat`: Issued At : The **timestamp** (in Unix time) when the token was created.   
    - `exp`: Expiration : The **timestamp** after which the token is no longer valid. Prevents the use of old, potentially compromised tokens.
    - `aud`: Audience : Indicates the **intended recipient** of the token. Ensures that a token meant for one service isn’t used in another.
    - `email`, `name`, `roles`: Additional user info    
## Subject (`sub`)
- A **unique identifier** for the authenticated user.    
- Does not change even if the user's email or username does.    
- Important for linking a token to a specific user.    

## 🔐 Authentication Flow
1. **Client initiates authentication** by submitting identity credentials to the **Identity Provider (IdP)**.    
2. The **IdP verifies** the identity—this can involve passwords, biometrics, certificates, or other factors.    
3. Upon successful authentication, the **IdP issues a security token** (e.g., a JWT).    
4. The **client sends this token to the resource server** when requesting access to protected resources.    
5. The **resource server validates the token**, typically by:
    - Checking its **signature**.
    - Ensuring the token is **not expired** (`exp` claim).
    - Verifying the **audience** (`aud` claim).
    - Confirming **issuer** and **trust relationship** with the IdP.
6. If the token is valid, the **server grants access** based on the **claims** within the token.

---

## Single Sign-On (SSO)

- **SSO** is a fundamental capability provided by **modern identity providers**.    
- It allows a **user to authenticate once** and gain access to **multiple applications or systems** without needing to log in again for each one.    

### Benefits of SSO:
- Enhances **user experience** (fewer logins).
- Improves **security** (fewer password prompts reduces phishing risk).
- Centralizes **session management** and reduces password fatigue.

 **Example:**
**“Login with Google / Facebook / Apple”** on websites or apps:
- Logging into apps like Spotify, Airbnb, or Canva using your **Google or Facebook** account.
- This avoids creating a new username and password for each service.

### Federation
Federation enables the access of services across organizational or domain boundaries by establishing trust relationships between the respective domain’s identity provider.
Each organization’s **IdP trusts the other**, allowing users to access resources **across organizational boundaries**.

**Example:**
- **Logging into GitHub with your Company Login**:
    - Your company uses **Azure AD**.
    - GitHub trusts Azure AD (via SAML/OIDC).
    - You don’t have a GitHub password—your Azure login works.  
        _→ This is Federation._
- **University login to an academic journal**:
    - You log in to **ScienceDirect** using your university credentials.
    - ScienceDirect trusts your university’s IdP (EduGain/Shibboleth).  
        _→ Federation between two different identity systems._
- **Government Services Portal**:
    - You log into one central government portal.
    - That login grants access to health services, tax, immigration systems, even if those are separate departments.
    - Behind the scenes, **federation** exists between government agencies.  
        _→ Federation across multiple departments/IdPs._

### Analogy
 - **SSO** is like using one key to unlock all doors **in your own house**.
 - **Federation** is like using your work ID badge to enter **another company’s building**, because they’ve agreed to trust your employer’s ID system.


---

## References