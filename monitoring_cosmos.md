# Monitoring a Cosmos chain validator
###### *created Sep 22, 2022; last updated Sep 22, 2022*
## Warning: this is a work in progress!
----

### What should we be watching for if we're invested in a Cosmos validator?
1. Security monitoring
    - compromised signing keys
    - compomised accounts
    - compromised infrastructure
2. Liveness metrics
    - server metrics (connectivity, hardware resource use, bandwidth resource use, daemon status)
    - crypto network metrics: failing to sign pre-commits
    - crypto events: dropped rank; jailed;
3. Crypto metrics
    - economic metrics & events
4. Social events & metrics
    - emergencies triggered by core devs
    - governance proposals

Some of these events/metrics should get our attention immediately, while others we may track to review at regularly scheduled intervals.

### What kinds of alerts are there?
1. **SOS alert** wakes you up out of bed for an emergency 
2. **Strong alert** gets your attention outside of normal work hours, giving you time to avoid an emergency
3. **Soft alert** gets your attention during working hours
4. **Tracked** gives no alert, but recorded to review at regularly scheduled intervals

There are certain events and conditions that we want to track, and there are thresholds or events that we want notifications for.
In some cases we'll want to be notified immediately (like wake up, there's an emergency). In other cases we'll want a softer warning, so
maybe we'll address the issue at the beginning of the set of working hours. In cases that may lead to an emergency, we'll want a strong alert--enough to interrupt dinner, but not get us up out of bed. Finally, we may not want to be alerted, but still want to collect data for a regular review on the health and performance of our operations.

### Who gets alerted and how?
- How can the alertee get additional help if they need it?
- How should the alertee document an event? 

### How can we improve/expand our monitoring?
- What else are we missing?
