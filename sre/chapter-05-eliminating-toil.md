# Chapter 5: Eliminating Toil

## Summary

This chapter defines toil as the repetitive, manual, automatable operational work that SREs should actively minimize in favor of engineering projects. Google's SRE teams aim to keep toil below 50% of their time, enabling sustainable scaling and preserving the engineering identity of the SRE role. The core message is that consistent investment in automation and engineering work allows organizations to "invent more, and toil less."

## Key Concepts

- **Toil**: Operational work that is manual, repetitive, automatable, tactical, devoid of enduring value, and scales linearly with service growth
- **50% Rule**: SREs should spend at least half their time on engineering work rather than toil
- **Engineering Work**: Activities that produce permanent improvements to the service or reduce future toil
- **Sublinear Scaling**: The goal of growing team capacity more efficiently than service growth through automation

## Section Summaries

### Definition of Toil

Toil is precisely defined by six characteristics: it is manual (requiring human hands-on effort), repetitive (performed multiple times), automatable (a machine could do it), tactical (interrupt-driven and reactive), devoid of enduring value (no permanent improvement), and scales linearly with service size. Not all unpleasant work qualifies as toil; administrative overhead and "grungy work" with long-term benefits are distinct categories.

### Why Toil Is Bad

At the individual level, excessive toil leads to career stagnation, decreased morale, and eventual burnout among engineers. At the organizational level, unchecked toil growth prevents sublinear team scaling, erodes the engineering identity of SRE, and blurs the boundaries between SRE and traditional operations roles.

### Engineering Work Categories

SRE work is classified into four categories: software engineering (writing code and automation), systems engineering (configuration and architecture), toil (repetitive operations), and overhead (administrative tasks). The goal is to maximize the first two categories while minimizing toil and keeping overhead reasonable.

### Measuring Toil

Google's analysis shows that SREs on 6-person on-call rotations have a baseline 33% toil just from on-call duties. Survey data indicates actual toil averages around 33% but varies significantly (0-80%) across individuals. Primary sources include interrupts, on-call response, and release/push activities.

### The Nuance of Toil

Small amounts of toil can provide psychological benefits: it can be calming, build confidence through quick wins, and present relatively low-risk work. However, these benefits diminish rapidly as toil increases, and the negative consequences of excessive toil far outweigh any short-term advantages.

### Consequences of Excessive Toil

When toil exceeds healthy levels, it causes engineer burnout, organizational confusion about SRE's purpose, slower feature development, attrition of top performers, and broken promises to new team members who were sold on an engineering-focused role.

## Practices

- Track and measure toil as a percentage of each team member's time
- Maintain the 50% cap on toil; escalate when approaching this threshold
- Prioritize automation projects that eliminate recurring manual work
- Design systems and processes to be self-service rather than requiring human intervention
- Ensure on-call rotations have enough members to keep baseline toil manageable
- Regularly review and question whether current manual processes could be automated
- Distinguish between true toil and valuable "grungy work" that has long-term benefits

## Key Takeaways

1. **Toil has a precise definition**: Work must meet specific criteria (manual, repetitive, automatable, tactical, no enduring value, linear scaling) to qualify as toil.

2. **The 50% rule is non-negotiable**: SREs must spend at least half their time on engineering work to maintain the value proposition of the SRE model.

3. **Toil is a scaling problem**: Without active management, toil grows linearly with service size, eventually consuming all available engineering capacity.

4. **Small amounts of toil are acceptable**: Some repetitive work provides psychological benefits and low-risk productivity, but this must be carefully managed.

5. **Invest in elimination, not management**: The solution to toil is engineering it away through automation and better system design, not simply learning to cope with it.
