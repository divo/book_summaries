# Chapter 13: Emergency Response

## Summary

This chapter emphasizes that things will inevitably break, and what defines an organization's resilience is how people respond during emergencies. Effective emergency response requires preparation, training, management support, and a structured approach to learning from incidents. The chapter uses three real Google case studies to illustrate different types of emergencies and the lessons learned from each.

## Key Concepts

- **Non-panic response**: Professionals are trained for emergencies; staying calm and following established processes is critical
- **Collaborative incident response**: Involving additional team members when overwhelmed improves outcomes
- **System interdependencies**: Understanding how systems connect is essential for predicting failure cascades
- **Canary testing**: Gradual rollouts prevent global failures from configuration changes
- **Automation safeguards**: Automated systems need sanity checks to prevent catastrophic errors

## Section Summaries

### What to Do When Systems Break

The chapter advises against panic when systems fail, noting that professionals are trained to handle such situations. When feeling overwhelmed, the recommendation is to involve additional team members and follow established incident response processes.

### Test-Induced Emergency (Case Study 1)

A controlled test blocking access to one database in a MySQL cluster unexpectedly cascaded across dependent services due to insufficient understanding of system interdependencies. SRE immediately aborted the test, restored permissions, and collaborated with developers to fix the underlying library flaws within an hour.

### Change-Induced Emergency (Case Study 2)

A configuration change pushed globally on a Friday caused crash-loop bugs across all externally-facing systems. Monitoring detected the issue within seconds, and the engineer rolled back the change within five minutes, minimizing the impact. This incident highlighted the importance of comprehensive canary testing.

### Process-Induced Emergency (Case Study 3)

An automation bug during server decommissioning sent all machines globally to the Diskerase queue, wiping hard drives across the infrastructure. Traffic was redirected within an hour, but full recovery through manual reinstallation took three days.

### Learning from the Past

Organizations should maintain thorough incident documentation and ensure accountability for follow-up actions to prevent recurrence of documented failures.

### Proactive Testing

Rather than discovering failures during production outages, controlled testing in monitored environments reveals weaknesses while teams are available and focused.

## Practices

- Stay calm and follow established incident response processes when systems break
- Involve additional team members when feeling overwhelmed during incidents
- Maintain and disseminate clear incident response procedures across the organization
- Implement comprehensive canary testing for all changes, regardless of perceived risk
- Build and test rollback procedures in safe environments before they're needed
- Add sanity checks to automated systems to prevent catastrophic errors
- Set up out-of-band communication channels for when primary systems fail
- Document incidents thoroughly and ensure accountability for follow-up actions
- Conduct controlled testing in monitored environments to discover weaknesses proactively

## Key Takeaways

1. **Things will break**: Accept that failures are inevitable and focus on building resilience through preparation, training, and effective response processes.

2. **Calm, collaborative response wins**: Panic is counterproductive. Effective emergency response relies on following established processes and involving the right people.

3. **Canary everything**: Global rollouts of untested changes are a recipe for disaster. Always use incremental rollouts with proper monitoring.

4. **Automation needs guardrails**: Automated systems can cause catastrophic damage at scale if they lack appropriate sanity checks.

5. **Learn continuously**: Every incident is an opportunity to improve. Maintain thorough documentation and conduct proactive testing.
