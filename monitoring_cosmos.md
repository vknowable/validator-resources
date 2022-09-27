# Monitoring a Cosmos chain
###### *created Sep 22, 2022; last updated Sep 22, 2022*
### Warning: this is a work in progress!
----
## Summary
We're invested in the success of a number of Cosmos chains, so we'll want to [monitor](#what-should-we-be-watching-for) security, liveness, crypto, and social metrics. Then we'll want to be after certain events or thresholds--these are our [alert types](#what-kinds-of-alerts-are-there). Knowable has an [alert response procedure](#alert-response-procedure) for knowing how to respond to alerts. Finally we have specific [monitor-alert policies](#monitor-alert-policies) for each community that we are invested in. Our [Agoric alert-monitor policy](#agoric-policy) is the most developed so far. **Please comment / contact us if you have feedback**, we truly value feedback about [how we can improve](#how-can-we-improve).

'

## What should we be watching for?
Security monitoring, liveness metrics, crypto metrics, social events & metrics (eg. emergencies; governance)

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
    - emergencies triggered by core devs or reputable validator operators
    - governance proposals
    
Some of these events/metrics should get our attention immediately, while others we may track to review at regularly scheduled intervals. It will depend on the protocol.

Knowable is running two different mainnet validators, and these are our policies:
- [Agoric policy](#agoric-alert-monitor-policy)
- [Cosmos Hub policy](#cosmos-hub-alert-monitor-policy) (validator inactive)

'

## What kinds of alerts are there?
SOS alerts for emergencies, strong alerts to avoid emergencies, soft alerts for issues that should be addressed during working hours, and there are non-alerted things that we track to review the health of our operations.

1. **SOS alert** wakes our devops person up out of bed for an emergency
    - repeated [PagerDuty](https://www.pagerduty.com) phone calls that bypass the phone's DND mode
    - [PagerDuty](https://www.pagerduty.com) email sent to a dedicated email address
2. **Strong alert** gets our attention outside of normal work hours, giving us time to avoid an emergency
    - priority [PagerDuty](https://www.pagerduty.com) text message
    - [PagerDuty](https://www.pagerduty.com) email sent to a dedicated email address
3. **Soft alert** gets our attention during working hours
    - [PagerDuty](https://www.pagerduty.com) email sent to a dedicated email address
    - bot **tbd** posts message in Knowable team's internal messaging platform
4. **Track** gives no alert, but metrics are recorded to review at regularly scheduled intervals
    - logging **tbd**

There are certain events and conditions that we want to track, and there are thresholds or events that we want notifications for.
In some cases we'll want to be notified immediately (like wake up, there's an emergency). In other cases we'll want a softer warning, so
maybe we'll address the issue at the beginning of the set of working hours. In cases that may lead to an emergency, we'll want a strong alert--enough to interrupt dinner, but not get us up out of bed. Finally, we may not want to be alerted, but still want to collect data for a regular review on the health and performance of our operations.

'

## Alert Response Procedure
- How can the alertee get additional help if they need it?
- How should the alertee document an event?

'

# Monitor-Alert Policies

## Agoric Alert-Monitor Policy

**Note:** This policy is actively being developed on the testnet, and has not yet been implemented on mainnet.

---

**Objective: Stay in the active set**

Falling out of the active set results in a) Knowable delegators' governance voting power not counting in a vote that ends while inactive; b) Knowable delegators not receiving staking income while inactive; and c) reasonable questions about our ability to fulfill our role as validator operators, depending upon what made us inactive. If too many validators (ie. > 33% of stake) go offline at once, the chain will halt.

#### 1. Jail prevention
We must prevent our validator from being jailed and thus removed from the active set, which happens due a failure to sign blocks.
[Agoric parameters](https://bigdipper.live/agoric/params) are set to a window of 5,000 blocks, and at 6s per block, that's 8hr 20min of being offline before being jailed. We won't be slashed, but our delegators won't have governance power, we won't be earning, and it can damage our reputation. If too much voting power goes offline at once, the chain will fail to produces blocks. **How can we ensure that Knowable is signing blocks?**

**Internal monitoring**
- monitor server resources; disk space, memory, CPU, bandwidth and
    - **track tbd**
    - **soft alert tbd**
    - **strong alert tbd**
    - **SOS alert tbd**
- monitor the daemon software and
    - **alert tbd**

**External monitoring**
- monitor missed pre-commit events and
    - **track** 15 missed blocks
    - **soft alert** at 50 missed blocks (5 minutes)
    - **strong alert** at 2500 missed blocks
    - **SOS alert** at 3200 missed blocks (gives us 3hrs to fix the issue eg. a corrupt database)
- monitor jail events and **SOS alert** upon jailing
- monitor internet connection 
    - **alert tbd**

#### 2. Rank sustainability
We must ensure that our validator stays above Rank 101 by voting power in order to remain in the active set. Since our rank is conditional upon our cumulative token delegation amount, relative to other validators, we can only control this by either a) **self-funding a delegation** that reactivates our validator or by b) **soliciting delegation(s)** from others.

Since neither option will be possible for us to execute as an emergency action, _delegators should be aware that we will likely need time to react, and during this time they won't earn or have governance power from their delegations to Knowable's validator._ You can either redelegate to an active validator (list of validator friends tbd), or you can try to help us return to the active set. Please do what is in your best interest.

- **strong alert** when falling below the 100 validator ranking
- **soft alert tbd** (when getting close to Rank 100, but tbd for how to codify that)
- **track tbd** (for watching for trends to ensure sustainable ranking)

'

## Cosmos Hub Alert-Monitor Policy

---

Since the Knowable validator is currently inactive, developing this policy is lower priority and is TBD (to be determined).

## How can we improve?
- What else are we missing?
