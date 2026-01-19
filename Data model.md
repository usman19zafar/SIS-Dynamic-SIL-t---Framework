ANNEX Y — DATA MODEL FOR SIL(t)
Time‑Dependent Safety Integrity Level

Y.1 Scope

This annex defines the data model required to compute, store, update, and verify the time‑dependent Safety Integrity Level, SIL(t).
The model supports continuous integrity evaluation of Safety Instrumented Systems (SIS) using the Mosaic Aging Model (MAM).

The data elements defined herein are mandatory for any system implementing SIL(t).

Y.2 Overview

SIL(t) is derived from time‑dependent values of:

λ(t)  (hazard rate)

PFDavg(t)

PFH(t)

DC(t)  (diagnostic coverage)

SFF(t) (safe failure fraction)

β(t)   (common cause factor)

T(t)   (mission time)

D(t)   (degradation state)

The data model defines the structure, relationships, and update rules for these values.

Y.3 Entity Model

The SIL(t) data model consists of six primary entities:

Component

DegradationState

HazardRateModel

ArchitectureModel

LoopRiskModel

SILResult(t)

Each entity is defined below.

Y.3.1 Entity: Component

Identifier:

ComponentID

Attributes:

Role (sensor, logic, final element, power, network)

BaseLambda (baseline failure rate)

Type (A/B per IEC 61508)

ManufacturerDataReference

InstallationDate

ReplacementHistory[]

ProofTestInterval

DiagnosticCoverageInitial

SFF_Initial

Beta_Initial

Relationships:

HasOne: DegradationState

HasOne: HazardRateModel

Y.3.2 Entity: DegradationState

Identifier:

ComponentID (foreign key)

Attributes (all time‑dependent):

AgeHours(t)

Cycles(t)

EnvironmentFactor(t)

StressFactor(t)

MaintenanceQuality(t)

DiagnosticCoverage(t)

SFF(t)

Beta(t)

ConditionIndicators(t)
(vibration, temperature, corrosion, drift, fouling, etc.)

Purpose:
Represents the living data describing the real condition of the component.

Y.3.3 Entity: HazardRateModel

Identifier:

ComponentID (foreign key)

Attributes:

Lambda(t)

Lambda_DU(t)

Lambda_DD(t)

Lambda_SU(t)

Lambda_SD(t)

Inputs:

DegradationState(t)

BaseLambda

Environmental multipliers

Stress multipliers

Maintenance multipliers

Diagnostic coverage

Outputs:

Updated hazard rate λ(t)

Y.3.4 Entity: ArchitectureModel

Identifier:

LoopID

Attributes:

ArchitectureType (1oo1, 1oo2, 2oo3, 2oo4, mixed)

ChannelAssignments[]

PartialFailureStates[]

BypassStates[]

OverrideStates[]

Relationships:

HasMany: Component

Purpose:
Defines how component hazard rates combine into loop hazard rate.

Y.3.5 Entity: LoopRiskModel

Identifier:

LoopID

Attributes (all time‑dependent):

PFDavg(t)

PFH(t)

RRF(t)

MissionTimeRemaining(t)

DriftIndicators(t)

ArchitectureHealth(t)

Inputs:

HazardRateModel outputs

ArchitectureModel

ProofTestInterval

RepairTime

DiagnosticCoverage(t)

SFF(t)

Beta(t)

Outputs:

Loop‑level risk metrics

Y.3.6 Entity: SILResult(t)

Identifier:

LoopID

Attributes:

SIL(t)

SIL_Target

SIL_Status (Valid / Invalid / Expired)

ValidityInterval [t_start, t_end]

ReasonForChange (drift, degradation, test failure, architecture imbalance)

Inputs:

LoopRiskModel outputs

IEC 61508/61511 SIL bands

Purpose:
Represents the current operational SIL.

Y.4 Data Relationships

Component → DegradationState → HazardRateModel → ArchitectureModel → LoopRiskModel → SILResult(t)

This is a strict dependency chain.

Y.5 Update Rules

Y.5.1 Time‑Dependent Updates
All time‑dependent attributes shall be updated at intervals not exceeding:

the proof test interval, or

the diagnostic reporting interval, or

the DAIS‑10 ingestion cycle

whichever is shortest.

Y.5.2 Degradation Updates
DegradationState(t) shall be updated using:

CMMS data

proof test results

condition monitoring

environmental sensors

operational logs

Y.5.3 Hazard Rate Updates
λ(t) shall be recalculated whenever:

degradation indicators change

maintenance occurs

diagnostics detect drift

environmental conditions shift

Y.5.4 Architecture Updates
ArchitectureModel shall be updated when:

channels degrade unevenly

bypasses occur

overrides occur

partial failures are detected

Y.5.5 Risk Metric Updates
PFDavg(t) and PFH(t) shall be recalculated whenever λ(t) changes.

Y.5.6 SIL(t) Updates
SIL(t) shall be recalculated whenever:

PFDavg(t) changes

PFH(t) changes

architecture changes

degradation exceeds thresholds

Y.6 Data Quality Requirements

All data used in SIL(t) shall be:

time‑stamped

source‑identified

validated

auditable

complete

traceable

Missing or invalid data shall trigger:

SIL(t) uncertainty increase, or

SIL(t) invalidation

Y.7 Compliance Requirements

A SIL claim shall be considered valid only when:

SIL(t) ≥ SIL_Target

All required data elements are present

No drift indicators exceed thresholds

Mission time has not expired

Architecture health is within limits

If any condition fails, SIL_Status = “Expired”.

Y.8 Formal Statement

The SIL(t) data model defines the complete set of entities, attributes, relationships, and update rules required to compute and maintain a time‑dependent Safety Integrity Level.
This model ensures that SIS integrity reflects real operational conditions rather than static design assumptions.
