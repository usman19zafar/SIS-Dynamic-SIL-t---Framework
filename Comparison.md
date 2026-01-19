1. BASIC ASSUMPTIONS OF A TRADITIONAL SIS (IEC 61508/61511)
These are the implicit assumptions the standards make — the ones that break in real life.

A. Constant Failure Rate Assumption
The SIS is assumed to have a constant λ (hazard rate).
This implies:

no aging

no wear‑out

no environmental drift

no degradation

no stress accumulation

This is the “exponential distribution” assumption.

B. Uniform Aging Assumption
All components in the loop are assumed to:

be the same age

degrade at the same rate

experience the same environment

have the same mission time

This is the assumption your Mosaic Aging Model destroys.

C. Static Architecture Assumption
The architecture (1oo2, 2oo3, etc.) is assumed to remain:

unchanged

balanced

equally healthy across channels

No imbalance, no partial degradation.

D. Proof Test Interval is Fixed
The PFDavg calculation assumes:

fixed test interval

fixed test coverage

fixed repair time

No variation, no deferrals, no backlog.

E. Generic Failure Data is Representative
The model assumes:

manufacturer FMEDA data is accurate

generic databases apply to your plant

failure modes are stable over time

This is rarely true.

F. SIL is a Static Label
Once calculated, SIL is assumed to remain valid until:

next turnaround

next audit

next redesign

This is the core flaw.

2. BASIC PRINCIPLES OF A TRADITIONAL SIS
These are the intended principles of the standard.

Principle 1 — Risk Reduction
SIS exists to reduce risk to tolerable levels.

Principle 2 — Independence
SIS must be independent from BPCS and other layers.

Principle 3 — Functional Integrity
The system must perform its safety function on demand.

Principle 4 — Lifecycle Approach
Safety must be managed from design → operation → decommissioning.

Principle 5 — Verification & Validation
Design assumptions must be checked, but only periodically.

Principle 6 — Systematic Capability
Avoid systematic (design) failures through process discipline.

These principles remain valid — DAIS‑10 strengthens them.

3. BASIC ASSUMPTIONS OF SIL(t) (THE DYNAMIC MODEL)
SIL(t) rejects the static assumptions and replaces them with living data.

A. Failure Rate is Time‑Dependent
λ(t) changes with:

age

cycles

environment

stress

maintenance

diagnostics

degradation

This is the core mathematical shift.

B. Components Age Independently
Each component has its own:

age

hazard rate

mission time

degradation curve

This is the Mosaic Aging Model.

C. Architecture Degrades Over Time
Voting architectures drift:

1oo2 becomes “1 good + 1 weak”

2oo3 becomes “2 mid + 1 bad”

Architecture is no longer static.

D. Proof Test Interval is Dynamic
Test intervals must adapt to:

drift

degradation

failure patterns

backlog

operational stress

E. Real Data Overrides Generic Data
Living data replaces:

FMEDA tables

generic λ

assumed failure modes

DAIS‑10 becomes the source of truth.

F. SIL is a Function of Time
SIL(t) is recalculated continuously:

SIL(t) = f(PFDavg(t), PFH(t), DC(t), SFF(t), β(t))

This is the only mathematically honest model.

4. BASIC PRINCIPLES OF SIL(t)
These are the governing principles of the dynamic model.

Principle 1 — Living Integrity
Safety integrity must reflect the current state of the system, not historical assumptions.

Principle 2 — Continuous Updating
Failure rates, degradation, and diagnostics must be updated continuously.

Principle 3 — Mosaic Evaluation
The loop integrity is determined by the worst‑aging component.

Principle 4 — Drift Detection
Detect when:

λ(t) increases

PFDavg(t) rises

architecture weakens

mission time expires

Principle 5 — Evidence‑Based SIL
SIL(t) must be based on:

real data

real degradation

real operating conditions

Not assumptions.

Principle 6 — Standards Compatibility
SIL(t) does not replace IEC 61508/61511.
It feeds them better data.

5. ONE SENTENCE SUMMARY
Traditional SIS assumes the system is frozen in time.
SIL(t) assumes the system is alive.
