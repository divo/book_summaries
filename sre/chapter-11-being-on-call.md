# Chapter 11: Being On-Call

## Summary

This chapter explores how Google SRE approaches on-call duties, emphasizing the balance between operational work and engineering projects. It covers the quantitative and qualitative aspects of on-call rotations, psychological safety considerations, and strategies for managing both operational overload and underload. The core principle is that on-call work should be sustainable, allowing SRE teams to scale through engineering rather than headcount.

## Key Concepts

- **50% Rule**: SREs should spend at least 50% of their time on engineering projects, with operational work (including on-call) capped at the remaining 50%
- **25% On-Call Cap**: Maximum 25% of an SRE's time should be dedicated to on-call duties
- **Incident Definition**: A sequence of events and alerts related to the same root cause that would be discussed in a single postmortem
- **1:1 Alert/Incident Ratio**: Teams should aim for one alert per incident, grouping related alerts together
- **Dual-Site Coverage**: Multi-site teams can provide 24/7 coverage without night shifts while maintaining production familiarity

## Section Summaries

### Life of an On-Call Engineer

On-call engineers serve as guardians of production systems, responsible for managing outages and approving production changes. Response times are tied to service availability requirements—user-facing systems typically require 5-minute responses, while less critical systems allow 30 minutes. Many teams maintain primary and secondary rotations with clear escalation paths.

### Balanced On-Call (Quantity)

Using the 25% on-call cap, single-site teams need at least eight SREs for 24/7 coverage with week-long shifts. Dual-site teams should have minimum six members per site to ensure adequate coverage while avoiding engineer burnout. Multi-site arrangements eliminate night shifts but require careful management of communication overhead.

### Balanced On-Call (Quality)

Average incident resolution requires approximately 6 hours including root-cause analysis, remediation, and postmortem work, suggesting a maximum of two incidents per 12-hour shift. If a component causes daily pages (median > 1 incident/day), this indicates systemic issues that will likely compound with other failures. Quality of on-call experience matters as much as quantity.

### Compensation

Google offers on-call engineers compensation through either time-off-in-lieu or cash payments, capped at certain salary proportions. This structure incentivizes participation in on-call rotations while promoting balanced workload distribution across the team.

### Feeling Safe

Research shows that rational, deliberate thinking produces better incident management outcomes than intuitive reactions. Stress hormones like cortisol impair cognitive function and encourage confirmation bias, making it crucial to create supportive on-call environments. Key resources for reducing stress include clear escalation paths, well-defined incident management procedures, and a blameless postmortem culture.

### Avoiding Operational Overload

Leadership must set concrete, measurable objectives to restore workloads to sustainable levels. Misconfigured monitoring is a common cause of overload—paging alerts should align with SLO threats and be actionable. When developers introduce unreliability, SRE teams can "give back the pager" until systems meet standards.

### Operational Underload

Quiet systems can create false confidence and knowledge gaps that surface only during actual incidents. Teams should ensure every engineer participates in on-call at least quarterly to maintain familiarity with production systems. "Wheel of Misfortune" exercises and annual DiRT (Disaster Recovery Training) events help develop and maintain troubleshooting skills.

## Practices

- Cap on-call time at 25% of total work time to preserve engineering capacity
- Maintain minimum team sizes (8 for single-site, 6 per site for dual-site) for sustainable rotations
- Target maximum two incidents per 12-hour shift for quality on-call experience
- Aim for 1:1 alert-to-incident ratio by grouping related alerts
- Establish clear escalation paths and incident management procedures
- Conduct blameless postmortems to learn from incidents without assigning blame
- Use "Wheel of Misfortune" exercises to develop troubleshooting skills
- Run regular disaster recovery training (like DiRT) to test incident response capabilities
- Ensure every engineer participates in on-call at least quarterly

## Key Takeaways

1. **Engineering First**: The defining characteristic of SRE is the "E"—engineering should be the primary mechanism for scaling reliability, not just adding more operational staff.

2. **Sustainable On-Call**: On-call rotations must be balanced both quantitatively (time spent) and qualitatively (incident volume and complexity) to prevent burnout and maintain effectiveness.

3. **Psychological Safety Matters**: Creating an environment where engineers feel safe to think rationally rather than react intuitively leads to better incident outcomes.

4. **Both Overload and Underload Are Dangerous**: Too many incidents cause burnout, but too few can lead to skill atrophy and false confidence.

5. **Metrics Drive Improvement**: Concrete, measurable goals (incidents per shift, tickets per day, alert/incident ratios) enable teams to quantify problems and track progress.
