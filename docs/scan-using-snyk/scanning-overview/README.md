# Scanning overview

{% hint style="info" %}
Scans may be limited on your account, depending on your[ Pricing Plan](../../implement-snyk/enterprise-implementation-guide/trial-limitations.md). See [What counts as a scan?](what-counts-as-a-test.md) for more information.
{% endhint %}

Snyk takes a developer-first approach to secure your development work by integrating directly into your IDEs, workflows, and automation pipelines to add security expertise to your toolkit. This approach allows you to:

* Use Snyk to focus on early enablement, not later enforcement.&#x20;
* Run scans while working on a Project, before you commit any code. This minimizes rework by finding issues that require changes early on.
* Add and test packages before writing the code that interfaces with each package.
* &#x20;After writing a major section of code, scan it to find issues before continuing work.

## Snyk scanning methods

Snyk supports scanning methods that correspond to Snyk products. Choose the right scanning method for the job you want to do, to find and fix vulnerabilities early in the Software Development Life Cycle.

* [Snyk Open Source](../snyk-open-source/) provides vulnerability testing, license testing and monitoring for your open-source libraries.
* [Snyk Code](../snyk-code/) scans your code for security vulnerabilities using source code analysis.
* [Snyk Container](../snyk-container/) scans your Projects for issues with container images.
* [Snyk Infrastructure as Code ](../snyk-iac/)scans for issues in your cloud infrastructure configurations before and after deployment.

For more information, see [Start scanning](../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md).

### Running PR checks

Snyk Open Source and Snyk Code allow you to [run PR Checks](../run-pr-checks/) to validate changes submitted to code and open-source packages before merging. Snyk can also retest and alert on the default branch on a scheduled basis and show results. You can use PR checks for the following:

* Code analysis with Snyk Code
* Check for Open source and licensing with Snyk Open Source
  * Check for known vulnerabilities and create Fix Pull Requests (npm/Yarn 1,2,3)
  * Check for license compliance (Snyk Open Source)
  * Address dependency upgrades by positioning updates to address technical debt (Snyk Open Source)

## Learn how to design secure code

The following resources are available for all users:

* [Snyk Advisor](https://snyk.io/advisor): Helps you pick healthy open-source packages or base images to develop code.
* [Snyk Learn](https://learn.snyk.io/): Assists you in learning to code securely, and provides training on how to use Snyk.

## Write and deploy your code

The following capabilities are available for all Snyk users except as noted in the documentation for each capability.

* Using the [Snyk CLI](../../snyk-cli/), you can scan locally on your machine. This is useful in scanning open-source and static code as well as containers and infrastructure as code configurations, including complex files that are templated with variables, such as Terraform plan files.
* Using [Snyk IDE Plugins](../../integrate-with-snyk/ide-tools/), you can test your open-source packages, first-party code, and infrastructure as code (IaC) Kubernetes deployment files in your development environment as you create your Project.
* Using [Git integrations](../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/), you can improve security in your Git repositories for both your code and deployed applications.
* Using [CI/CD integrations](../../integrate-with-snyk/snyk-ci-cd-integrations/), you can fail the build in your integration and deployment pipeline to keep vulnerabilities out of your code.
  * There are options for passive monitoring and establishing a quality assurance gate by failing build checks based on tests for violations of policies.
  * Most CI/CD integrations use the Snyk CLI, allowing you to fail the build based on criteria specified in options or using the [snyk-filter tool](../../snyk-cli/scan-and-maintain-projects-using-the-cli/cli-tools/snyk-filter.md).
  * Snyk CI/CD integrations include Snyk plugins for Jenkins, Circle CI, and other tools, as well as Partner Platforms, including Azure, Bitbucket, and AWS, that offer built-in pipes or components for using Snyk.
  * GitHub[ Actions](../../integrate-with-snyk/snyk-ci-cd-integrations/github-actions-for-snyk-setup-and-checking-for-vulnerabilities/) provide additional means for securing your code in your deployment pipeline. For details and an example, see [Building a secure CI/CD pipeline with GitHub Actions for your Java Application](https://snyk.io/blog/building-a-secure-pipeline-with-github-actions/).

## Monitor your code in production

Before integrating your code into production, use the [`snyk monitor`](../../snyk-cli/commands/monitor.md) or [`snyk container monitor`](../../snyk-cli/commands/container-monitor.md) CLI command to take a snapshot and monitor for vulnerabilities to avoid pushing them into production.

You can use the `snyk monitor` or `snyk container monitor` capabilities to identify issues introduced into open-source and container Projects. During implementation, monitoring helps you to gain recognition of vulnerabilities in your Projects. See [Deployment and rollout recommendations](./#deployment-and-rollout-recommendations) for details.

Using the `snyk monitor` or `snyk container monitor` command allows you to push results from the CLI to the Snyk Web UI, where you can view the information to help in fixing issues. Use the  `--org=` option to indicate the Organization that contains the Project, so you will use the test settings you intend and push the results to the correct Project.

Snyk Enterprise plan customers can monitor container images and their open-source and Linux-based packages being used in production through Kubernetes integration to receive notifications of known vulnerabilities for applications in production.

## Manage and fix issues using Snyk

If you see hundreds or thousands of issues when first scanning your application, prioritization of issues becomes important. For information on prioritizing issues, see [Find and manage priority issues](../find-and-manage-priority-issues/).

Snyk offers capabilities to address issues both reactively and proactively:

* **Being proactive**
  * Use [Snyk Advisor](https://snyk.io/advisor) to identify better packages to begin designing.
  * Use the CLI and IDE plugins to test while developing.
  * Add a package, ensure it is installed, and scan for security before writing your code.
* **Remediation advice**\
  Snyk provides this advice across integrations, calculating the top-level package requiring an update in the package manifest or how to update the line of code to make it secure and displaying the advice on results screens.
* **Automation**
  * You can enable creating automatic fix pull requests when a new vulnerability is detected with a fix available. Snyk suggests enabling automated PRs initially on a key Project you enable globally, to familiarize development with how to interact with Snyk and security issues.
  * When you first import a Project into Snyk, it may already have vulnerabilities. Instead of overwhelming you with fixes, Snyk presents the highest priority known vulnerability for you to fix first. After you fix that vulnerability, Snyk presents the next highest priority known vulnerability. In this way, you can catch up on and fix existing issues. You can speed this process up by fixing all vulnerabilities in a single dependency at one time by enabling **Clear vulnerability backlog faster** in [Snyk Preview](../../snyk-admin/manage-settings/snyk-preview.md).
  * You can enable dependency upgrade-related pull requests created when new versions of a package are available. This helps with technical debt by providing PR nudges to update dependencies.

## Deployment and rollout recommendations

Startups, small teams, individuals, and open-source maintainers typically onboard their applications using Git, getting results in minutes and starting to address issues almost immediately. Small teams benefit from being agile and determining what works best for their workflow.  With large organizations developing hundreds of applications, a slower approach is recommended to get developer buy-in and adoption and to ensure a positive rollout experience.

1. Typically, large organizations start with daily monitoring of applications using Git integration, initially turning on PR checks for a few key applications **at most**. You may use CI/CD scans on key applications for some ecosystems to get a granular view of the exact versions being deployed.
2. As developers become familiar with Snyk capabilities, your company can widen the scope of applications with PR checks for gating or blocking builds if checks fail.
3. Some customers use CI/CD to passively monitor and then turn on gating by using the Snyk CLI `test` command for each product.
4. If you import many legacy applications, you can use [Priority Score](../find-and-manage-priority-issues/priority-score.md) (typically 700 as a starting place). If you would like to have more control over the criteria, you can do the following:
   * Focus on `Critical` to start with for open source, and `High` for first-party code.
   * For open source, try additional criteria like `Known exploit` or `Fix available` to define a starting point for engaging developers in fixing vulnerabilities for key applications.

For more information, see [Implement Snyk](../../implement-snyk/).