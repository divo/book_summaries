# Chapter 32: The Evolving SRE Engagement Model

## Summary

This chapter explores how Site Reliability Engineering teams engage with services at different lifecycle stages, recognizing that few services begin with SRE support. It presents three engagement models that evolved to address the challenges of scaling SRE practices across growing numbers of services, ultimately advocating for framework-based approaches that embed reliability best practices directly into reusable infrastructure.

## Key Concepts

- **Production Readiness Review (PRR)**: A structured process for evaluating whether a service meets operational standards before SRE takes responsibility
- **Early Engagement**: Involving SREs during design and build phases rather than post-launch
- **Frameworks and Platforms**: Standardized infrastructure that codifies SRE best practices into reusable components
- **Scalable Engagement**: Approaches that allow SRE teams to support many more services than traditional models permit
- **Shared Responsibility Model**: Division of labor where SREs maintain infrastructure while development teams handle application logic

## Section Summaries

### The Simple PRR Model

The Production Readiness Review model is applied to services that have already launched and consists of five phases: initial engagement, analysis of production shortcomings, prioritization and implementation of improvements, training the SRE team, and progressive transfer of operational responsibility.

### Early Engagement Model

This model introduces SRE involvement during the design and build phases rather than waiting until after launch. Benefits include preventing design-related production incidents, improving implementation quality, and enabling smoother service launches.

### Frameworks and Platform Approach

As microservices architecture became prevalent, traditional engagement models became unsustainable. Google developed language-specific frameworks that encapsulate SRE best practices, providing common control surfaces, automated deployment capabilities, and built-in monitoring.

### Evolution Drivers

The shift toward microservices and the explosion in service count made traditional one-to-one SRE engagement impractical. The organization needed solutions that could scale through codified best practices embedded in reusable code.

## Practices

- Use structured checklists during production readiness reviews
- Engage SRE teams early in the design phase to prevent reliability issues
- Build frameworks that embed reliability best practices
- Create common control surfaces across services to reduce operational complexity
- Automate deployment, monitoring, and other operational tasks through standardized platforms
- Progressively transfer responsibility from development teams to SRE as services mature
- Continuously improve services after onboarding

## Key Takeaways

1. **SRE engagement is a spectrum**: Different services at different lifecycle stages require different engagement strategies.

2. **Early SRE involvement yields better outcomes**: Involvement during design prevents retrofitting reliability into already-launched services.

3. **Framework-based approaches are essential for scaling**: Codifying best practices in reusable code enables SRE to support many services.

4. **Make reliability the default**: Embedding it into platforms and tools means all services benefit without requiring manual SRE intervention.

5. **Shared responsibility enables sustainable scaling**: SREs own infrastructure and frameworks while developers own application logic.
