# Chapter 29: Dealing with Interrupts

## Summary

This chapter addresses how SRE teams should manage operational load - the work required to keep systems functional. It emphasizes that interrupts fragment attention and reduce productivity, so teams should polarize time by dedicating blocks to either interrupt handling or project work.

## Key Concepts

- **Operational Load**: The work that must be done to maintain a system in a functional state
- **Cognitive Flow State**: The productive mental state where engineers can do their best work
- **Polarizing Time**: Dedicating entire days or weeks to either interrupt work or project work
- **Two Types of Flow**: Creative/engaged flow (deep work) and routine task execution flow (completing known tasks)

## Section Summaries

### Categories of Operational Load

Three categories of interrupts: **Pages** are production alerts requiring immediate response. **Tickets** are customer requests with response times measured in hours to weeks. **Ongoing operational responsibilities** include ad hoc tasks like code rollouts and flag deployments.

### The Human Element

Humans are not designed for constant context-switching. Achieving cognitive flow requires clear goals, immediate feedback, and a sense of control - all of which are disrupted by frequent interrupts.

### Polarizing Time

Rather than fragmenting attention, engineers should dedicate entire days or weeks to one category. This dramatically reduces context-switching costs.

### On-Call Management

Primary on-call engineers should focus exclusively on interrupt work during their rotation. A person should never be expected to be on-call and also make progress on projects.

### Ticket Management

Random distribution of tickets across a team is an anti-pattern. Teams should designate dedicated ticket handlers who can achieve flow state in interrupt-handling mode.

### Reducing Interrupt Load

Teams should investigate recurring tickets to find root causes rather than accepting an endless stream of similar issues. Silencing interrupts temporarily while fixing root causes prevents fighting fires while trying to build fire prevention systems.

## Practices

- Assign primary on-call engineers exclusively to interrupt handling during their rotation
- Never expect engineers to be on-call while also making progress on project work
- Designate dedicated ticket handlers rather than randomly distributing tickets
- Conduct regular scrubs to examine interrupt patterns and root causes
- Define formalized roles for pushes, flag rollouts, and other ongoing responsibilities
- Create clear procedures that allow knowledge transfer between shifts
- Push appropriate investigation steps back to requestors when possible

## Key Takeaways

1. **Context-switching is expensive**: Polarizing time into dedicated blocks dramatically improves productivity.

2. **On-call and project work don't mix**: A person should never be expected to do both.

3. **Interrupt handling can be satisfying**: When engineers are dedicated to interrupt work, they can achieve flow state.

4. **Attack root causes**: Rather than accepting constant similar tickets, investigate patterns and fix underlying issues.

5. **Respect both customers and engineers**: Balance responsiveness with protection of engineers' cognitive capacity.
