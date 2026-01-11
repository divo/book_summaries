# Chapter 14: Managing Incidents

## Summary

This chapter by Andrew Stribblehill examines effective incident management practices at Google, contrasting chaotic unmanaged incidents with structured responses based on the Incident Command System (ICS). The chapter demonstrates through narrative scenarios how proper role separation, clear communication, and documented procedures transform crisis response from stressful chaos into coordinated resolution.

## Key Concepts

- **Incident Command System (ICS)**: A structured framework adapted from emergency services for managing technical incidents
- **Recursive Role Separation**: Clear assignment of responsibilities that prevents confusion and enables autonomous action within defined boundaries
- **Command Transfer**: Explicit handoff protocols ensuring unambiguous leadership transitions during long-running incidents
- **Incident State Document**: A living document that tracks critical information, decisions, and timeline in real-time
- **Sharp Technical Focus Anti-pattern**: The tendency for engineers to dive deep into problem-solving while neglecting coordination and communication

## Section Summaries

### The Unmanaged Incident

The chapter opens with a narrative about an on-call engineer facing a cascading failure across multiple datacenters. Without proper incident management structure, multiple problems compound: unclear communication, unauthorized changes by well-intentioned staff, and complete lack of coordination.

### Elements That Hamper Incident Resolution

Three critical failures emerge from the unmanaged scenario: sharp technical focus where engineers become consumed by problem-solving without considering broader mitigation; communication breakdown with staff working in silos; and uncoordinated action where well-meaning colleagues deploy changes without consulting the incident lead.

### Elements of Incident Management Process

The chapter recommends a framework with clear roles including Incident Commander (maintains high-level state), Operations Lead (executes technical responses), Communications Officer (updates stakeholders), and Planning Lead (handles logistics and documentation). Teams should coordinate through a designated command post with a live incident state document.

### A Managed Incident

The same scenario is replayed with proper incident management in place. The result is a structured, efficient response with significantly reduced stress and successful resolution.

### When to Declare an Incident

An incident should be declared if multiple teams must coordinate, if customers experience impact, or if issues persist beyond one hour of concentrated analysis. Erring on the side of declaring an incident is preferable to struggling without proper coordination.

## Practices

- Prioritize service restoration over root cause analysis during active incidents
- Prepare procedures in advance and rehearse incident response before crises occur
- Use a centralized communication channel that provides logging and enables distributed coordination
- Maintain a live incident document tracking decisions, actions, and timeline
- Implement explicit command handoffs with verbal confirmation of leadership transfer
- Practice regularly through game days and exercises to build muscle memory
- Rotate roles to ensure multiple team members can fill each incident management role
- Evaluate alternatives continuously to avoid tunnel vision
- Monitor emotional state and recognize when stress affects decision-making

## Key Takeaways

1. **Structure beats chaos**: Even experienced engineers perform poorly in unmanaged incidents; formal processes dramatically improve outcomes regardless of individual skill levels.

2. **Role clarity prevents conflict**: When everyone knows their responsibilities and boundaries, teams can work autonomously without stepping on each other.

3. **Communication is not optional**: Stakeholders need regular updates; failing to communicate creates secondary problems that compound the original incident.

4. **Preparation determines success**: Incident management skills must be practiced before incidents occur; game days and exercises build the muscle memory needed for crisis response.

5. **Declare incidents early**: The overhead of formal incident management is minimal compared to the cost of an uncoordinated response.
