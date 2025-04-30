## Secret Scanning
### Domain 1: GHAS Security Features and Functionality
#### Secret Scanning in a Secure Development Lifecycle 
- **Key Distinction**:
  - Secret Scanning: Protects against accidental exposure of sensitive data.
- **Secret Scanning**
  - Detects sensitive information/credentials (e.g., API keys, tokens) within repositories inadvertently exposed in code.
  - Scans all repository content, including git history and pull request discussions and issues.
  - Includes **Push Protection** to block and prevents  the commit of secrets proactively .
  - Notifies admins and optionally alerts secret providers for mitigation.


#### How Secret Scanning Contributes to a Secure Development Lifecycle

- Features:
  - Push Protection: Blocks secret-containing commits.
  - Alerts: Highlights vulnerabilities in real-time for rapid response.
  - Supports custom patterns for detecting organization-specific secrets.

#### Security Embedded into the Development Lifecycle
- **Benefits**:
  - Promotes consistent adherence to security standards and reduces production risks.
  - Enhances collaboration between developers and security teams.
  - Proactively identifies and prevents credential leaks.
  - Ensures confidentiality of sensitive information at all development stages.
  - Monitors git history, issues, pull requests, and discussions for secrets.

- **Workflow Integration**:
  - Automated scans during pull requests.
  - Actionable alerts within the development pipeline.

### Domain 2: Configure and Use Secret Scanning
#### Enable and Use Secret Scanning
  
 - **How to Enable**
   - Navigate to **Repository Settings > Code Security and Analysis**.
   - Enable **Secret Scanning** for individual or all repositories.

#### Configure Secret Scanning for Public and Private Repositories
- Public Repositories:
  - Enabled by default for scanning common secret patterns.
- Private Repositories:
  - Requires **GitHub Advanced Security** license.
  - Supports custom secret patterns for organization-specific needs.

#### Set up Secret Scanning Alerts
- **Steps:**
  1. Go to the repository's **Security tab**.
  2. Enable **Secret Scanning Alerts**.
  3. Alerts notify admins and optionally the secret's provider.
- **Push Protection**:
  - Prevents secrets from being committed by scanning during `git push`.

#### Exclude Files from Scanning
- Use `.gitattributes` to mark files as binary.
- Add patterns or file types to **exclusion lists** in repository settings.

#### Configure Custom Alert Patterns
- Custom patterns to detect organization-specific secrets:
  - Define regex-based patterns in repository settings.
  - Apply for specific repositories or across an organization.

#### Respond to Secret Scanning Alerts
- **Process:**
  1. Review alerts in the **Security tab**.
  2. Evaluate the impact of the detected secret.
  3. Revoke and replace exposed credentials immediately.
  4. Add the secret to an exclusion list if false positive.
- **Dismissal Options**:
  - Mark alerts as resolved or invalid if no action is needed.

#### Roles and Permissions in Secret Scanning
- **Admin Role**:
  - Full access to configure and manage alerts.
- **Write Role**:
  - View and act on alerts.
- **Organization Owners**:
  - Can enable and enforce policies across repositories.

#### Enable Secret Scanning for Organizations
  - **Steps:**
    1. Navigate to **Organization Settings > Code Security and Analysis**.
    2. Enable **Secret Scanning** for all repositories.
    3. Set up default settings for new repositories.
- Apply **Push Protection** across repositories for added security.
