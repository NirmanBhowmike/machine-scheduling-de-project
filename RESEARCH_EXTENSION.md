# Research Extension: Disruption-Severity-Aware Rescheduling

## Research question

Can disruption-severity-aware rescheduling reduce unnecessary schedule nervousness while maintaining acceptable tardiness in dynamic parallel-machine scheduling?

## Baseline

The baseline policy reschedules after each relevant event. The original baseline is preserved on the `baseline-v1` branch.

## Proposed extension

For machine failures, reduced-capacity events, and recoveries, the system first evaluates the effect of keeping the current schedule. It then generates candidate rescheduled solutions and compares the potential tardiness reduction with the schedule nervousness introduced by the candidate.

The interface reports:

- disruption severity;
- tardiness if the current schedule is kept;
- best candidate rescheduled tardiness;
- tardiness reduction;
- candidate nervousness;
- final decision to absorb the disruption or reschedule.

## Decision logic

For each candidate schedule:

```
relative_tardiness_benefit =
    (keep_schedule_tardiness - candidate_tardiness)
    / max(1, keep_schedule_tardiness)

decision_score =
    relative_tardiness_benefit
    - stability_preference * candidate_nervousness
```

In severity-aware mode, a candidate is accepted only when the decision score is positive and the candidate reduces tardiness. Otherwise the disruption is absorbed without changing job sequence or machine assignment.

The stability preference is editable in the GUI. Larger values place more emphasis on avoiding schedule changes.

## Severity indicator

Severity is based on the maximum relative tardiness reduction available from the candidate set:

- Low: less than 10%
- Moderate: 10% to less than 25%
- High: 25% or greater

This indicator describes the potential operational impact. The final rescheduling decision still uses both tardiness benefit and nervousness.

## Experimental comparison

The research version includes two selectable policies:

1. **Always Reschedule (Baseline)**
2. **Severity-Aware**

Both can be run on the same predefined event scenario. This supports a controlled comparison of:

- total tardiness;
- nervousness;
- number of rescheduling events;
- number of disruptions absorbed;
- number of jobs moved.

The extension is intended as an implementable research prototype, not as a claim that the current thresholds or decision rule are universally optimal.
