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
- **Code Scanning**:
  - Provides static analysis at critical points in the development workflow:
    - Pull requests
    - Scheduled scans
    - Repository pushes
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
