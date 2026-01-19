Mosaic Aging Model (MAM) and Time‑Dependent SIL Evaluation
X.1 Scope
This annex defines the requirements, assumptions, and methods for evaluating Safety Instrumented Systems (SIS) using the Mosaic Aging Model (MAM) and the time‑dependent Safety Integrity Level, SIL(t).
This annex supplements IEC 61508 and IEC 61511 by specifying a data‑driven approach for maintaining SIL validity throughout the operational life of a SIS.

This annex does not modify the normative requirements of IEC 61508/61511.
It provides an enhanced data interpretation layer intended to support continuous integrity verification.

X.2 Normative Assumptions
X.2.1 Heterogeneous Aging
A SIS shall be treated as a collection of independently aging components.
Each component shall be assumed to have a unique degradation trajectory influenced by:

operating time

mechanical/functional cycles

environmental exposure

stress and load conditions

maintenance quality

diagnostic performance

repair and replacement history

Uniform aging across components shall not be assumed.

X.2.2 Time‑Dependent Hazard Rate
The failure rate λ of each component shall be treated as a function of time:

λ = λ(t)

Constant failure rate assumptions may be used only as initial design priors and shall not be considered valid for operational verification.

X.2.3 Architecture Degradation
Voting architectures (e.g., 1oo2, 2oo3) shall be assumed to degrade over time due to unequal component aging.
Architecture performance shall be evaluated using component‑specific hazard rates.

X.2.4 Mission Time Variability
Each component shall be assigned an individual mission time Ti.
The mission time of the SIS loop shall be:

T_loop = min(T1, T2, …, Tn)

X.2.5 Data‑Driven Integrity
Operational data shall be considered the authoritative source for updating:

λ(t)

PFDavg(t)

PFH(t)

diagnostic coverage

safe failure fraction

common cause factors

Generic or manufacturer data shall be considered secondary once operational evidence is available.

X.3 Definitions
X.3.1 Mosaic Aging Model (MAM)
A model in which the SIS is represented as a composite of independently aging components, each with its own time‑dependent hazard rate and degradation profile.

X.3.2 SIL(t)
A time‑dependent Safety Integrity Level derived from:

PFDavg(t)

PFH(t)

λ(t)

DC(t)

SFF(t)

β(t)

SIL(t) replaces static SIL as the operational measure of integrity.

X.3.3 Living Data
Operational data continuously collected from:

CMMS

proof tests

diagnostics

condition monitoring

environmental sensors

operational logs

Living data shall be used to update component degradation states.

X.4 Requirements
X.4.1 Component‑Level Hazard Rate
Each component shall have a time‑dependent hazard rate λi(t) defined as:

λi(t) = f(age, cycles, environment, stress, maintenance, diagnostics, degradation)

The function f shall be documented and traceable.

X.4.2 Loop‑Level Hazard Rate
The loop hazard rate shall be computed as:

λ_loop(t) = F(λ1(t), λ2(t), …, λn(t))

The function F shall reflect the actual voting architecture.

X.4.3 Time‑Dependent PFDavg and PFH
PFDavg(t) and PFH(t) shall be recalculated at intervals not exceeding the proof test interval or upon significant operational change.

X.4.4 SIL(t) Determination
SIL(t) shall be determined using the applicable IEC 61508/61511 limits for PFDavg or PFH.

A SIL claim shall be considered valid only for the time interval during which:

SIL(t) ≥ SIL_target

X.4.5 Drift Detection
The system shall detect deviations from design assumptions, including:

increasing λ(t)

rising PFDavg(t)

architecture imbalance

reduced diagnostic coverage

accelerated degradation

Detected drift shall trigger reassessment of SIL(t).

X.4.6 SIL Expiry
A SIL claim shall expire when:

SIL(t) < SIL_target

mission time T_loop is exceeded

drift exceeds allowable thresholds

component degradation invalidates design assumptions

Operation beyond SIL expiry shall require documented risk acceptance or corrective action.

X.5 Data Requirements
X.5.1 Minimum Data Set
The following data shall be collected for each component:

operating hours

cycle counts

environmental conditions

stress/load indicators

maintenance actions

proof test results

diagnostic events

failure history

X.5.2 Data Quality
Data shall be:

complete

time‑stamped

traceable

validated

auditable

X.5.3 Data Integration
All data sources shall feed a unified degradation model for each component.

X.6 Computational Requirements
X.6.1 Update Frequency
λ(t), PFDavg(t), PFH(t), and SIL(t) shall be updated:

continuously, or

at intervals not exceeding the proof test interval, or

upon significant operational change

X.6.2 Model Transparency
All computational models shall be:

documented

version‑controlled

reproducible

traceable to data sources

X.6.3 Architecture Awareness
Calculations shall reflect:

actual voting logic

channel imbalance

partial failures

bypasses and overrides

X.7 Compliance with IEC 61508/61511
X.7.1 Non‑Interference
This annex does not modify the normative requirements of IEC 61508/61511.

X.7.2 Enhancement
This annex enhances compliance by:

improving accuracy of λ inputs

validating mission time

maintaining SIL validity

detecting risk drift

supporting lifecycle integrity

X.7.3 Alignment
All outputs of SIL(t) shall be mapped to the existing SIL bands defined in IEC 61508/61511.

X.8 Formal Statement
A SIS shall be evaluated as a mosaic of independently aging components.
The integrity of the SIS shall be determined using time‑dependent hazard rates, risk metrics, and SIL(t), supported by continuous operational data.
Static SIL claims shall not be considered valid beyond their last successful time‑dependent verification.
