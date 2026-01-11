# Chapter 18: Software Engineering in SRE

## Summary

This chapter explores how Google's SRE organization develops internal software tools to solve production-scale problems, demonstrating that SREs are uniquely positioned to create engineering solutions for infrastructure challenges. The Auxon capacity planning tool serves as the primary case study, showing how intent-based automation can replace labor-intensive manual processes.

## Key Concepts

- **Intent-Based Computing**: Services describe requirements through abstraction layers rather than specifying exact resource needs
- **Toil Reduction Through Automation**: Software engineering enables SRE teams to avoid linear growth with service proliferation
- **Domain Expertise as Advantage**: SREs possess unique production knowledge that enables scalable, user-focused design
- **Approximation Over Perfection**: Starting with "good enough" solutions enables faster iteration
- **Modularity for Uncertainty**: Abstracting implementation details allows swapping components as understanding improves

## Section Summaries

### Why Software Engineering Within SRE Matters

Google's production environment represents one of the most complex machines humanity has ever built, and SREs are uniquely positioned to develop software solutions due to their deep production knowledge. SRE-developed tools enable the principle that team size shouldn't scale linearly with service growth.

### The Auxon Case Study

Auxon is a capacity planning tool that automates resource allocation by translating service requirements into optimized solutions. Traditional capacity planning suffered from brittleness, labor-intensive manual bin packing, and imprecise resource allocation. Auxon introduces an intent-based approach where services describe requirements at various abstraction levels.

### Auxon's Architecture

The system comprises eight major components including performance data, demand forecast data, resource supply, pricing, intent config, configuration language engine, solver, and allocation plan output. The modular architecture allows each component to be improved or replaced independently.

### Development Lessons

The team initially built a "Stupid Solver" using heuristics rather than waiting for perfect algorithmic solutions, enabling faster iteration. Modularity and abstraction protected against implementation uncertainty. The adoption strategy included targeting early adopters and providing white-glove support.

### Project Selection Criteria

Good project candidates reduce toil, address production reliability, feature domain experts, align with organizational objectives, and enable iterative development. Poor candidates touch too many moving parts simultaneously or require all-or-nothing approaches.

## Practices

- Start with a "Stupid Solver" or MVP rather than waiting for perfect solutions
- Design modular systems that allow component swapping as understanding improves
- Target early adopters who lack existing solutions and are motivated to try new approaches
- Provide white-glove support addressing both technical and emotional concerns during adoption
- Maintain production involvement to prevent engineers from becoming disconnected full-time developers
- Apply the same development rigor (testing, code review, documentation) as product teams

## Key Takeaways

1. **SREs are uniquely qualified software developers**: Their deep production knowledge enables them to build scalable, effective solutions to infrastructure challenges.

2. **Intent-based abstraction enables automation**: By having services describe what they need rather than how to achieve it, complex optimization problems become machine-solvable.

3. **Start simple, iterate quickly**: The "Stupid Solver" approach demonstrates that approximation and iteration outperform waiting for perfect solutions.

4. **Balance software development with production work**: Engineers must maintain their SRE perspective by continuing production involvement.

5. **Software engineering in SRE provides triple benefit**: It benefits the company, the organization, and individual engineers through career development and skill maintenance.
