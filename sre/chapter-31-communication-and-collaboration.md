# Chapter 31: Communication and Collaboration in SRE

## Summary

This chapter examines how SRE teams at Google maintain effective communication and collaboration across their distributed, diverse organizational structure. The authors emphasize that successful SRE operations depend on reliable information flow, structured communication mechanisms like production meetings, and strong partnerships both within SRE and with product development teams.

## Key Concepts

- **Two Masters Model**: SRE teams maintain dual accountability to their assigned services and to the broader SRE culture/reporting structure
- **Production Meetings**: Structured weekly sessions focused on service state rather than individual status updates
- **Cross-Site Collaboration**: Distributed teams require exceptional written communication and periodic in-person interaction
- **Early Engagement**: SRE involvement during initial design phases yields better outcomes than retrofitting reliability later
- **Ownership and Churn**: Contributor turnover creates ownership dilution and onboarding costs

## Section Summaries

### Organizational Context

SRE operates across multiple models including infrastructural teams, service teams, and horizontal product teams. Teams contain people with diverse backgrounds spanning systems engineering, software engineering, and project management.

### Production Meetings

Production meetings serve as the primary structured communication mechanism, typically running 30-60 minutes weekly with a focus on service state. Standard agenda items include upcoming production changes, core metrics, outage postmortems, paging and non-paging events, and action item tracking.

### Meeting Leadership and Attendance

Many SRE teams rotate the chair role among members to distribute ownership and develop facilitation skills. Remote participants are accommodated through representatives, pre-populated agendas, and real-time collaborative documents.

### Collaboration Within SRE

SRE's globally distributed structure creates fluid team definitions that require attention to role clarity and communication practices. Cross-timezone collaboration necessitates either exceptional written communication or periodic in-person interaction.

### Case Study: Viceroy Project

The Viceroy monitoring dashboard framework demonstrates the challenges of cross-site SRE collaboration. Key challenges included misinterpretation of written communication, high contributor churn, and difficulty maintaining components with distributed ownership.

### Cross-Site Project Recommendations

Teams should only undertake cross-site development when truly necessary. Projects benefit from prioritizing motivated contributors, dividing work into components assignable to single sites, and establishing clear decision-making processes. In-person project summits prove invaluable.

### Collaboration Outside SRE

Effective SRE-product development collaboration works best during initial design phases before code commitment, when SREs can contribute infrastructure and architecture expertise.

## Practices

- Hold regular production meetings focused on service state, not individual status updates
- Rotate meeting chair responsibilities to develop skills and distribute ownership
- Include product development partners in production meetings when possible
- Use pre-populated agendas and real-time collaborative documents for distributed meetings
- Define clear team roles while maintaining flexibility
- Invest in written communication skills for distributed collaboration
- Schedule periodic in-person interaction to maintain relationship quality
- Divide cross-site projects into components that can be owned by single sites
- Engage SRE early in the design phase

## Key Takeaways

1. **Structure enables communication**: Production meetings with consistent agendas create reliable information flow.

2. **Written communication has limits**: Even excellent writers eventually become "just an email address" without periodic face-to-face engagement.

3. **Cross-site projects carry hidden costs**: Communication overhead, contributor churn, and ownership dilution mean they should only be undertaken when truly necessary.

4. **Early SRE engagement pays dividends**: SRE involvement during initial design phases yields expertise that is difficult to retrofit later.

5. **Clear interfaces enable parallel work**: Well-defined boundaries between components and teams allow concurrent development.
