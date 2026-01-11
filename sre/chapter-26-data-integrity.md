# Chapter 26: Data Integrity: What You Read Is What You Wrote

## Summary

This chapter establishes that data integrity requirements are stricter than uptime requirements—while 99.99% uptime may be acceptable, 99.99% "good bytes" in a 2GB file would mean ~200KB of corruption, which is catastrophic. Google SRE addresses data integrity through a three-layer defense strategy: soft deletion, backups with tested recovery, and early detection via out-of-band validation.

## Key Concepts

- **Data integrity vs. uptime**: Data integrity demands are fundamentally stricter than availability requirements
- **ACID vs. BASE**: Applications often combine both transactional approaches, creating referential integrity challenges
- **Backups vs. Archives**: Backups must restore rapidly within SLOs; archives allow extended recovery windows
- **Replication is not recoverability**: Replicated systems propagate corruption across all copies before isolation
- **Trust points**: Immutable data portions established after passage of time to enable incremental backup focus
- **Three-layer defense**: Soft deletion, backups/recovery, and early detection working together

## Section Summaries

### Data Integrity's Strict Requirements

Data integrity requirements are stricter than uptime needs because even small percentages of corruption can be catastrophic. The response strategy centers on proactive detection coupled with rapid repair and recovery.

### Backups Versus Archives

Archives serve long-term compliance storage with extended recovery windows, while backups must restore rapidly within service uptime SLOs. The guiding principle is that "what people really want are restores," not backups themselves.

### Types of Failures Leading to Data Loss

Failures are categorized by root cause (user action, operator error, bugs, infrastructure, hardware, site catastrophe), scope (widespread vs. narrow), and rate (big bang vs. creeping). Most user-visible data loss involves deletion or loss of referential integrity caused by software bugs.

### Replication Misconception

Replication and redundancy are not recoverability—replicated systems propagate corruption across all copies before isolation is possible.

### First Layer: Soft Deletion

Mark deleted data as inaccessible immediately while preserving it for configurable periods (15-60 days). This dramatically reduces user support burden from accidental deletion.

### Second Layer: Backups and Recovery Methods

A tiered backup strategy balances data loss tolerance, recovery speed requirements, and temporal reach. Google uses multiple tiers from frequent local snapshots to nearline/tape storage.

### Third Layer: Early Detection

Out-of-band data validation using MapReduce/Hadoop jobs confirms invariants between and within datastores.

## Practices

- Implement soft deletion with configurable retention periods (15-60 days)
- Design backup strategy around recovery scenarios, not backup processes
- Use tiered backups: local snapshots for quick recovery, distributed storage for medium-term, tape for long-term
- Deploy out-of-band validators to check data integrity independently of application logic
- Test recovery processes continuously through automation
- Monitor for anomalous deletion rates
- Conduct regular emergency preparedness drills

## Key Takeaways

1. **Recovery over backup**: "Backups don't matter; what matters is recovery." Design your backup strategy around how you need to restore.

2. **Defense in depth**: Multiple-tiered approaches (soft deletion, backups, early detection) provide cost-effective protection.

3. **Verify continuously**: Unexercised system components fail when needed most.

4. **Replication is not protection**: Replicated systems propagate corruption before isolation is possible.

5. **Detect early, recover fast**: As recovery speed improves, transition from recovery planning toward prevention planning.
