# GitHub Advanced Security Certification Map
---

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
- Proactively identifies and prevents credential leaks.
- Ensures confidentiality of sensitive information at all development stages.
- Features:
  - Push Protection: Blocks secret-containing commits.
  - Alerts: Highlights vulnerabilities in real-time for rapid response.
- Supports custom patterns for detecting organization-specific secrets.

#### Security Embedded into the Development Lifecycle
- **Core Features**:
  - **Secret Scanning**: Prevents accidental leaks of sensitive data.
  - **Code Scanning**: Identifies vulnerabilities during the coding phase.
  - **Dependabot**: Manages dependencies to ensure they are secure and up-to-date.
- **Benefits**:
  - Early detection of vulnerabilities reduces production risks.
  - Promotes consistent adherence to security standards.
  - Enhances collaboration between developers and security teams.
- **Workflow Integration**:
  - Automated scans during pull requests.
  - Actionable alerts within the development pipeline.

### Domain 2: Configure and Use Secret Scanning
#### Enable and Use Secret Scanning
 - **What is Secret Scanning?**
  - Scans repositories for sensitive credentials (e.g., API keys, tokens).
  - Monitors git history, issues, pull requests, and discussions for secrets.
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
  - Review alerts in the **Security tab**.
  - Evaluate the impact of the detected secret.
  - Revoke and replace exposed credentials immediately.
  - Add the secret to an exclusion list if false positive.
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
 


---

## Code Scanning
### Domain 1: GHAS Security Features and Functionality
#### Code Scanning in a Secure Development Lifecycle
- **Key Distinction**:
  - Code Scanning: Protects against vulnerabilities within the code.
- **Code Scanning**:
  - Focuses on Analyzes/identifying security vulnerabilities and coding errors within the source code.
  - Uses static analysis to detect issues/risk like SQL injection, XSS, and buffer overflows.
  - Provides automated feedback during pull requests to fix issues early.
  - Integrates with workflows for early feedback during development.

#### How Code Scanning Improves Security in the Development Lifecycle
- Detects vulnerabilities before they reach production.
- Improves code quality and reduces security debt by addressing issues early.
- Provides actionable insights directly in development workflows (e.g., pull requests).
- Supports custom queries and third-party integrations for enhanced analysis.
- Ensures compliance with security standards and reduces risks associated with coding errors.

#### Integration of Security at Every Step of the Lifecycle
- **Secret Scanning**:
  - Detects and mitigates secret leaks from the first commit to production deployment.
  - Push Protection blocks sensitive data at commit time.
- **Code Scanning**:
  - Provides static analysis at critical points in the development workflow:
    - Pull requests
    - Scheduled scans
    - Repository pushes
- **Dependabot**:
  - Automates dependency management by updating to secure versions.
  - Identifies vulnerable dependencies and raises alerts for updates.
- **Overall Workflow**:
  - Security is embedded into the lifecycle rather than being treated as a separate phase.
  - Collaboration between developers and security teams ensures rapid issue resolution.
  - Real-time alerts enable continuous monitoring and improvement of security posture.
 
### Domain 4: Configure and Use Code Scanning
#### Enable Code Scanning with GitHub Actions
- **Overview:**
  - Code scanning uses GitHub Actions to detect vulnerabilities in code.
  - Provides feedback directly in pull requests.
- **Steps:**
  1. Navigate to the **Security tab** in the repository.
  2. Enable **Code Scanning Alerts**.
  3. Select or configure a default **workflow** for code scanning.

#### Configure Workflows with GitHub Actions
- **Built-in Workflows:**
  - Use predefined templates like **CodeQL Analysis**.
- **Custom Workflows:**
  - Define custom `.yml` workflows in `.github/workflows/`.

#### Set up CodeQL Analysis
- **CodeQL**:
  - GitHub's static code analysis tool for identifying security vulnerabilities.
  - Supports languages like JavaScript, Python, Java, and C++.
- **Steps:**
  1. Add **CodeQL workflow** to your repository.
  2. Configure supported languages in the workflow file.
  3. Run scans manually, on a schedule, or during pull requests.

#### Code Scanning with Third-Party Tools
- **Supported Tools:**
  - Upload SARIF (Static Analysis Results Interchange Format) reports from third-party tools.
- **Integration:**
  - Include third-party analysis in your repository's security overview.

#### Scanning Frequency: Scheduled vs. Event-Driven
- **Scheduled Scans**:
  - Set up periodic scans (e.g., daily or weekly) in GitHub Actions.
  - Use `schedule` trigger in the workflow file.
- **Event-Driven Scans**:
  - Triggered on specific events like `push` or `pull_request`.
  - Ensures vulnerabilities are identified during active development.

#### Workflow Customization in GitHub Actions
- **Customization Options:**
  - Define custom **triggers**, **paths**, and **actions** in workflow files.
  - Modify scan configurations to target specific file types or directories.
- **Example**:
  ```yaml
  on:
    push:
      paths:
        - "src/**"
  jobs:
    build:
      runs-on: ubuntu-latest  

### Domain 5: Use Code Scanning with CodeQL
#### What is CodeQL: Definition, Packs, Queries, and Suites
- **CodeQL**:
  - GitHub's semantic code analysis engine for identifying vulnerabilities.
  - Uses a database generated from source code for query-based analysis.
- **CodeQL Packs**:
  - Bundles of CodeQL libraries and queries designed for specific languages or frameworks.
- **Queries**:
  - Predefined or custom scripts used to analyze the CodeQL database.
- **Suites**:
  - Collections of related queries grouped for comprehensive analysis.

#### Code Analysis Using CodeQL
- Analyzes code to detect security vulnerabilities, coding issues, and bad practices.
- Supports languages like JavaScript, Python, Java, C++, Ruby, and more.
- Produces actionable insights directly in pull requests or dashboards.

#### Run CodeQL from the CLI
- **Setup**:
  1. Install the CodeQL CLI from GitHub.
  2. Authenticate using a GitHub token if analyzing a private repository.
- **Steps**:
  1. Generate a CodeQL database:
     ```bash
     codeql database create <database_name> --language=<language> --source-root=<source_dir>
     ```
  2. Run queries on the database:
     ```bash
     codeql query run <query_file> --database=<database_name>
     ```
  3. Review the results in SARIF format.

#### Integrate CodeQL into GitHub Actions Workflows
- **Steps**:
  1. Navigate to `.github/workflows` directory.
  2. Add or modify the `codeql-analysis.yml` file.
  3. Example Workflow:
     ```yaml
     on:
       push:
         branches:
           - main
       pull_request:
         branches:
           - main

     jobs:
       codeql:
         runs-on: ubuntu-latest
         steps:
           - uses: actions/checkout@v3
           - uses: github/codeql-action/init@v2
             with:
               languages: javascript
           - uses: github/codeql-action/analyze@v2
     ```

#### Configure the Language Matrix in CodeQL
- **Language Matrix**:
  - Supports analyzing multiple languages in a repository.
  - Define supported languages in the workflow:
    ```yaml
    with:
      languages: |
        javascript
        python
    ```
  - CodeQL automatically detects relevant files and configurations for specified languages.

#### Reference Queries from Public, Private Repositories, and Local Directories
- **Public Repositories**:
  - Use queries from GitHub's public query libraries.
- **Private Repositories**:
  - Reference queries in private repositories with appropriate permissions.
- **Local Directories**:
  - Add local queries by specifying their path:
    ```yaml
    with:
      queries: ./local-queries/
    ```
- Combine multiple sources to create a comprehensive query suite.


### Domain 6: GitHub Advanced Security Best Practices
#### Improving the Management of Code Scanning Alerts
- **Proactive Alert Management**:
  - Regularly review alerts in the repository's **Security tab**.
  - Triage alerts based on severity, relevance, and impact.
- **Effective Resolution**:
  - Address high and critical severity alerts immediately.
  - Use automated suggestions provided in pull requests for quick fixes.
- **Alert Dismissal**:
  - Dismiss false positives with documented reasons.
  - Suppress alerts for legacy code using annotations or `.codeql` configuration files.
- **Prioritize Key Issues**:
  - Leverage **alert grouping** to focus on the most impactful vulnerabilities.
  - Use historical trends to identify recurring issues and root causes.
- **Collaboration**:
  - Involve security teams and developers in alert reviews for diverse perspectives.
  - Assign alerts to relevant team members for faster remediation.

#### Optimizations and Best Practices in CodeQL
- **Optimize Query Performance**:
  - Use **narrow scopes** for queries to reduce runtime and improve focus.
  - Avoid unnecessary joins and predicates in custom queries.
- **Utilize Built-In Queries**:
  - Leverage GitHub’s extensive library of **predefined CodeQL queries** for common vulnerabilities.
  - Regularly update query packs to ensure you're using the latest security intelligence.
- **Custom Queries**:
  - Develop organization-specific queries for unique security requirements.
  - Test custom queries in isolated environments to validate accuracy and performance.
- **CodeQL Database Management**:
  - Generate databases specific to the programming languages used in the project.
  - Reuse databases for multiple analyses to save resources.
- **Collaboration with Open Source**:
  - Contribute new or optimized queries to the CodeQL community.
  - Use queries shared in public repositories for additional coverage.
- **Automated Integrations**:
  - Schedule regular scans with CodeQL in **GitHub Actions workflows**.
  - Integrate CodeQL with CI/CD pipelines for continuous monitoring.
- **Training and Documentation**:
  - Train developers to understand CodeQL alerts and results.
  - Maintain clear documentation for query usage and troubleshooting.

---

## Dependabot
### Domain 1: GHAS Security Features and Functionality
#### Dependabot in a Secure Development Lifecycle
- **Role of Dependabot**:
  - Automates dependency management by keeping libraries and frameworks up to date.
  - Alerts developers to vulnerabilities in dependencies.
  - Provides automated pull requests to fix vulnerable or outdated dependencies.
- **Key Features**:
  - **Dependabot Alerts**:
    - Notifies about vulnerable dependencies found in the **GitHub Advisory Database**.
    - Displays detailed information in the repository’s **Security tab**.
  - **Dependabot Security Updates**:
    - Automatically generates pull requests to update dependencies with known vulnerabilities.
  - **Dependency Review**:
    - Highlights the security impact of dependency changes in pull requests.
- **Benefits in the SDLC**:
  - Reduces the risk of supply chain attacks.
  - Ensures projects use the most secure versions of libraries.
  - Automates routine tasks, freeing developers to focus on core features.

#### How Dependabot, Secret Scanning, and Code Scanning Create a Secure Development Workflow
- **Comprehensive Security Coverage**:
  - **Dependabot**:
    - Manages and secures third-party dependencies.
    - Prevents introducing vulnerable packages into the codebase.
  - **Secret Scanning**:
    - Detects and prevents leaks of sensitive data like API keys and tokens.
    - Blocks pushes containing secrets using **Push Protection**.
  - **Code Scanning**:
    - Identifies vulnerabilities and coding errors within the source code.
    - Provides actionable feedback during development.
- **Workflow Integration**:
  - Security features are embedded into **pull requests**, **pushes**, and **scheduled scans**.
  - Alerts and automated fixes integrate directly into GitHub workflows.
- **Benefits**:
  - **Proactive Security**:
    - Issues are addressed during development instead of after deployment.
  - **Consistency**:
    - Security checks are applied uniformly across all repositories and workflows.
  - **Collaboration**:
    - Developers and security teams work together seamlessly using shared insights.
- **Lifecycle Stages**:
  1. **Dependency Management**: Dependabot ensures secure and updated libraries.
  2. **Credential Protection**: Secret Scanning prevents accidental leaks of sensitive information.
  3. **Code Integrity**: Code Scanning identifies and mitigates vulnerabilities in the source code.

### Domain 3: Configure and Use Dependency Management
#### Enable and Configure Dependabot Alerts
- **Steps to Enable Alerts**:
  1. Navigate to **Settings > Code Security and Analysis**.
  2. Enable **Dependency graph** and **Dependabot alerts**.
- **Scope**:
  - Public repositories: Enabled by default for known vulnerabilities.
  - Private repositories: Requires **GitHub Advanced Security** license.

#### Define Vulnerabilities in Dependencies
- **Vulnerabilities**:
  - Issues in external libraries that pose risks to security.
  - Identified by cross-referencing the **GitHub Advisory Database**.
- **Impact**:
  - Exploits in vulnerable dependencies can compromise applications and data.

#### Dependabot Security Updates
- **Automated Updates**:
  - Creates pull requests to fix vulnerabilities in dependencies.
  - Proactively upgrades to the latest secure versions.
- **Grouped Updates**:
  - Combines updates to reduce the number of pull requests.
- **Compatibility Scores**:
  - Indicates potential impact of updates on functionality.

#### Dependency Graph and Generated Alerts
- **Dependency Graph**:
  - Visual representation of direct and transitive dependencies.
  - Tracks updates and identifies vulnerable components.
- **Generated Alerts**:
  - Provides details on affected dependencies, versions, and fixes.
  - Available in the repository's **Security tab**.

#### Configure Dependabot for Public and Private Repositories
- **Public Repositories**:
  - Supports alerts and security updates for free.
- **Private Repositories**:
  - Requires explicit configuration and a security license.
  - Steps:
    - Enable the dependency graph.
    - Configure Dependabot in **Settings > Code Security and Analysis**.

#### Set Up Alerts for Organizations
- **Organization-Wide Configuration**:
  - Navigate to **Organization Settings > Code Security and Analysis**.
  - Enable **Dependabot alerts** for all repositories.
- **Default Settings**:
  - Automatically enable alerts for new repositories.

#### Create a Valid Dependabot Configuration File
- **File Location**:
  - Save as `.github/dependabot.yml` in the repository.
- **Configuration Options**:
  - `version`: Specifies the configuration file version.
  - `updates`:
    - Defines package ecosystems (e.g., npm, pip, maven).
    - Specifies scan intervals (`daily`, `weekly`).
    - Example:
      ```yaml
      version: 2
      updates:
        - package-ecosystem: "npm"
          directory: "/"
          schedule:
            interval: "daily"
      ```

#### Remediate Vulnerable Dependencies
- **Steps**:
  1. Review alerts in the **Security tab**.
  2. Assess the severity and relevance of the vulnerability.
  3. Apply updates using Dependabot pull requests or manually.
  4. Validate changes through testing and CI/CD pipelines.
- **Dismiss Alerts**:
  - Dismiss false positives with documented justifications.
- **Alternative Actions**:
  - Remove unused dependencies to reduce the attack surface.


### Domain 6: GitHub Advanced Security Best Practices
#### Use CVE and CWE to Address Dependency Alerts
- **CVE (Common Vulnerabilities and Exposures)**:
  - A globally recognized identifier for publicly disclosed security vulnerabilities.
  - Each CVE includes:
    - A unique ID (e.g., CVE-2023-XXXXX).
    - A description of the vulnerability.
    - References for further details and fixes.
  - Use in Dependency Alerts:
    - Alerts link to the CVE for detailed vulnerability information.
    - Helps identify impacted versions and recommended fixes.

- **CWE (Common Weakness Enumeration)**:
  - A classification of software and hardware vulnerabilities.
  - Focuses on the **underlying weaknesses** that lead to vulnerabilities.
  - Examples:
    - CWE-79: Cross-Site Scripting (XSS).
    - CWE-20: Improper Input Validation.
  - Use in Dependency Alerts:
    - Describes the weakness type associated with the CVE.
    - Helps developers understand the root cause of vulnerabilities.
- **Best Practices**:
  - Leverage CVE details to evaluate the severity and scope of an alert.
  - Use CWE classifications to identify patterns and improve coding practices.
  - Document responses to alerts for organizational tracking.

#### Development and Security Roles in Managing Vulnerable Dependencies
- **Development Team Responsibilities**:
  - Review dependency alerts in the repository’s **Security tab**.
  - Assess the impact of vulnerabilities on the application.
  - Apply fixes through:
    - Automated pull requests by Dependabot.
    - Manual updates for dependencies with no available fixes.
  - Collaborate with security teams to validate the resolution of alerts.
  - Refactor or replace libraries if security risks persist.

- **Security Team Responsibilities**:
  - Monitor organization-wide dependency vulnerabilities.
  - Establish policies for dependency management, such as:
    - Approved dependency versions.
    - Frequency of updates and scans.
  - Validate fixes applied by developers and conduct additional testing.
  - Analyze trends in alerts to identify recurring issues and implement preventative measures.
- **Collaboration Between Roles**:
  - Developers handle immediate fixes during the development lifecycle.
  - Security teams provide oversight and ensure adherence to organizational security standards.
  - Shared dashboards and reports facilitate communication and tracking.



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