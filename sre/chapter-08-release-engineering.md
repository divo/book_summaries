# Chapter 8: Release Engineering

## Summary
Release engineering is a distinct discipline focused on building and delivering software reliably at scale. Release engineers combine expertise across source code management, compilers, build tools, package managers, and system administration to enable consistent, repeatable software releases. At Google, release engineering emphasizes self-service models, high velocity deployments, hermetic builds, and policy enforcement through automation.

## Key Concepts

- **Release Engineering as a Discipline**: A specialized field requiring deep technical expertise across the entire software delivery pipeline
- **Self-Service Model**: Teams should be able to release independently through automation without requiring dedicated release engineer involvement
- **High Velocity Releases**: Frequent, smaller releases reduce change scope and simplify testing and rollback
- **Hermetic Builds**: Builds must be reproducible across any machine by depending only on versioned tools, not environmental libraries
- **Cherry Picking**: Bug fixes apply to older release branches without pulling in unintended mainline changes
- **Policy Enforcement**: Security and approval controls integrated into automated workflows

## Section Summaries

### The Role of a Release Engineer
Release engineers at Google act as bridge professionals who develop metrics for deployment velocity, establish best practices for consistent releases, and collaborate with SREs on deployment strategies. They work to make product teams self-sufficient through tooling and documentation rather than serving as gatekeepers for every release.

### Philosophy
Google's release engineering philosophy centers on four principles: self-service models enabling team independence, high velocity through frequent small releases, hermetic builds ensuring reproducibility, and policy enforcement through automated access controls. These principles work together to enable reliable releases at massive scale while maintaining security and consistency.

### Continuous Build and Deployment

#### Building
Google uses Blaze (open-sourced as Bazel) as their build system, which compiles binaries across multiple languages with automatic dependency resolution. The build system ensures consistent, reproducible outputs regardless of the developer's local environment.

#### Branching
Code branches from the mainline at specific revisions for release preparation. Bug fixes are cherry-picked backward to release branches rather than merged forward, preventing unintended changes from entering stable releases.

#### Testing
Continuous testing systems validate unit tests on all mainline changes automatically. Release branches re-run the full test suite on packaged artifacts to ensure nothing was broken during the packaging process.

#### Packaging
The Midas Package Manager (MPM) distributes versioned, cryptographically signed packages with unique hashes. Packages carry labels indicating their release pipeline stage (dev, canary, production), providing traceability throughout the deployment process.

#### Rapid
Rapid is Google's automated release framework that orchestrates the complete release workflow. It manages branch creation, test execution, package building, and task dispatch across production infrastructure in a coordinated manner.

#### Deployment
Simple deployments are handled directly by Rapid, while Sisyphus manages complex rollouts with graduated cluster deployment. Rollout timelines are configurable to match each service's risk profile, enabling careful production deployments.

### Configuration Management
Organizations choose among four configuration management strategies based on their needs. Mainline configuration keeps config in the head branch, decoupling binaries from configuration but risking version skew. Packaging configuration together with binaries works for tightly coupled scenarios. Separate configuration packages enable independent updates while maintaining version tracking. External stores like Chubby or Bigtable serve dynamic configurations that change frequently.

## Practices

- Budget engineering resources for release processes early in product development
- Establish explicit release policies and procedures before building automation
- Ensure developers, SREs, and release engineers collaborate throughout the product lifecycle
- Build hermetic, reproducible build systems that don't depend on local environments
- Use cherry-picking for bug fixes rather than forward-merging to maintain release stability
- Implement graduated rollouts with canary deployments matching service risk profiles
- Cryptographically sign packages and maintain audit trails through the release pipeline
- Choose configuration management strategies appropriate to how frequently configs change
- Automate policy enforcement rather than relying on manual review processes
- Enable self-service releases through tooling and documentation

## Key Takeaways

1. **Release engineering is a discipline, not an afterthought**: Organizations benefit from treating release engineering as a first-class concern from early in product development, not something bolted on later.

2. **Automation enables velocity and reliability**: Self-service release automation allows teams to deploy frequently and independently while maintaining consistency and policy compliance.

3. **Hermetic builds are foundational**: Reproducible builds that depend only on versioned inputs (not environmental state) are essential for debugging, auditing, and maintaining confidence in releases.

4. **Configuration management requires deliberate strategy**: How configuration is managed relative to binaries has significant implications for deployment flexibility, debugging, and version compatibility.

5. **Collaboration across roles is essential**: Release engineering works best when developers, SREs, and release engineers work together throughout the product lifecycle rather than operating in silos with handoffs.
