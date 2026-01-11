# Chapter 28: Accelerating SREs to On-Call and Beyond

## Summary

This chapter addresses how to effectively onboard and train new Site Reliability Engineers to reach on-call readiness while keeping experienced team members engaged. The core premise is that investing upfront in education and technical orientation shapes better engineers.

## Key Concepts

- **Structured learning over chaos**: Clear learning paths with concrete milestones accelerate learning
- **Trust-based progression**: Team members must believe their peers are capable before granting on-call responsibilities
- **Defense-in-depth problem solving**: Mastering multiple diagnostic tools
- **Active vs. passive learning**: Activities range from reading postmortems (passive) to hands-on system breaking (active)
- **Reverse engineering mindset**: Understanding unfamiliar systems through debugging tools, logs, and RPC boundaries

## Section Summaries

### Core Training Philosophy

Effective SRE training requires sequential, concrete learning experiences combined with reverse engineering and fundamental principle-based thinking. "Trial by fire" approaches and menial alert triage are counterproductive.

### Three Essential SRE Attributes

New SREs must develop reverse engineering (understanding unfamiliar systems), statistical thinking (constructing and testing hypotheses), and improvisation ability (mastering multiple tools while challenging assumptions).

### Recommended Training Sequence

For real-time serving stacks, training should progress from query entry points through frontend architecture, mid-tier services, infrastructure and backends, and finally integration scenarios including debugging and emergency response.

### On-Call Learning Checklist

A structured document lists critical systems, dependencies, subject matter experts, essential knowledge requirements, and comprehension questions. This becomes a social contract between the team and new hires.

### Disaster Role-Playing (Wheel of Misfortune)

Weekly exercises with a game master running 30-60 minute simulations based on past outages provide safe practice environments.

### Breaking Real Things

Hands-on experience with staging or QA stacks allows senior SREs to create realistic failures for trainees to diagnose and resolve.

### Shadow On-Call Rotation

New engineers receive page copies during business hours to observe without time pressure, with mentors reviewing reasoning after resolution.

## Practices

- Create structured on-call learning checklists with clear milestones
- Host regular postmortem reading clubs and "tales of fail" presentations
- Run weekly "Wheel of Misfortune" disaster role-playing exercises
- Provide hands-on experience breaking things in staging/QA environments
- Assign documentation updates to new hires with senior SRE peer review
- Implement shadow on-call rotations with business-hours-only page copies initially
- Use reverse shadowing when newbies are ready to be primary on-call
- Record training presentations to build a reusable library

## Key Takeaways

1. **Structure accelerates learning**: Clear learning paths with concrete milestones build confidence faster than unstructured approaches.

2. **Invest upfront in education**: Time spent on structured onboarding pays dividends in engineer quality.

3. **Harness new hire enthusiasm**: Fresh perspectives benefit the entire team.

4. **Build trust through demonstrated competence**: Team members must believe their peers can perform under pressure.

5. **Combine theory with hands-on practice**: Frontload theoretical knowledge, then provide varied learning modalities.
