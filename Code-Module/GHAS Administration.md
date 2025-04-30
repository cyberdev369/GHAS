## GHAS Administration
### Domain 7: GitHub Advanced Security Administration
#### Enable GHAS in GitHub Enterprise Server
- **Steps**:
  1. Log in to the **GitHub Enterprise Server** administrative console.
  2. Navigate to **Site Admin > Enterprise Settings > GitHub Advanced Security**.
  3. Enable **Advanced Security** at the enterprise level.
  4. Ensure the license includes GHAS features like **Secret Scanning**, **Code Scanning**, and **Dependabot**.
- **Requirements**:
  - Sufficient **license capacity** for the enabled repositories.
  - Administrative permissions for configuration.

#### Enable GHAS for Organizations
- **Organization-Level Configuration**:
  1. Go to **Organization Settings > Security & Analysis**.
  2. Enable **Advanced Security** for all repositories.
  3. Apply default configurations for new repositories.
- **Repository-Specific Enablement**:
  - Navigate to the repository’s **Settings > Code Security and Analysis**.
  - Enable individual GHAS features as required.

#### Configure Security Policies for Repositories and Organizations
- **Repository-Level Policies**:
  - Enable or disable:
    - **Secret Scanning**.
    - **Code Scanning** with CodeQL or third-party tools.
    - **Dependabot Alerts and Security Updates**.
  - Set up branch protection rules to enforce dependency and code scanning checks.
- **Organization-Wide Policies**:
  - Define default security configurations for all repositories.
  - Enforce compliance by requiring specific workflows or settings:
    - Example: Require all pull requests to pass security checks before merging.

#### API Endpoints for GHAS: Secret Scanning, Code Scanning, and Dependabot
- **Secret Scanning API**:
  - Endpoints to list and manage detected secrets.
  - Example:
    ```bash
    GET /repos/{owner}/{repo}/secret-scanning/alerts
    ```
- **Code Scanning API**:
  - Manage CodeQL analyses and results.
  - Example:
    ```bash
    GET /repos/{owner}/{repo}/code-scanning/alerts
    ```
- **Dependabot API**:
  - View and manage dependency alerts.
  - Example:
    ```bash
    GET /repos/{owner}/{repo}/vulnerability-alerts
    ```
- **Use Cases**:
  - Automate reporting and monitoring.
  - Integrate with third-party tools for centralized security management.

#### Manage Permissions and Roles in Security Workflows
- **Roles and Their Access**:
  - **Repository Admins**:
    - Full control over enabling/disabling GHAS features.
    - Manage alerts and policies for individual repositories.
  - **Organization Owners**:
    - Configure default security settings for all repositories.
    - Grant or restrict access to security tools.
  - **Collaborators**:
    - **Write Access**: View and act on Code Scanning and Dependabot alerts.
    - **Admin Role**: Required to manage Secret Scanning alerts.
- **Permission Best Practices**:
  - Use role-based access to minimize over-permissioning.
  - Restrict alert visibility to essential personnel.
  - Grant explicit permissions for external contributors as needed.