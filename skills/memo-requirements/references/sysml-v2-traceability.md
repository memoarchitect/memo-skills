# SysML v2 traceability

## Evidence level

State exactly one model-evidence level in the output:

| Level | Meaning | Permitted claim |
| --- | --- | --- |
| `text-inspected` | Model text was read; no syntax or semantic check was performed. | Cite observed text only. |
| `parsed` | A parser accepted the inspected model scope. | Report syntactic structure only. |
| `resolved` | Names and relationships resolved in the inspected model scope. | Report trace links within that checked scope. |
| `compiler-checked` | The project’s compiler checked the inspected model scope. | Report checked trace links within that scope. |

Never claim complete traceability, complete allocation, or model conformance unless the relevant scope was checked and the coverage rule is stated. If no check was performed, state `text-inspected` rather than implying a stronger result.

## Mapping contract

Use explicit project mappings first. Do not translate an element or relationship solely because its name seems similar. If the project has no mapping, leave the target field as `TBD` and report the decision needed.

| Requirement artifact | Acceptable model evidence | Record in output |
| --- | --- | --- |
| User need | Project-defined need/requirement element or externally supplied need ID. | Need ID and qualified model element, if any. |
| System, software, or hardware requirement | A project-defined requirement element, its declared level/allocation, or an external requirement ID. | Requirement ID, level, qualified element, and allocation target. |
| Parent/derived relation | An explicit project-defined parent, derivation, refinement, or trace relation. | Relation type, source ID, target ID, and qualified relation. |
| Allocation | An explicit allocation relation or allocated-to property. | Allocating requirement, target element, and qualified relation/property. |
| Satisfaction | An explicit satisfy relation or project-defined equivalent. | Requirement ID, satisfying element, and qualified relation. |
| Verification or validation | An explicit verify relation, validation evidence link, or project-defined equivalent. | Requirement/need ID, evidence or test ID, method, and qualified relation. |
| Risk control | An approved external risk-management identifier or explicit project mapping. | Risk ID, status, and evidence source. |

Do not invent missing model relations. Report `missing mapping`, `unresolved reference`, or `no evidence supplied` as appropriate.

## Auditable traceability rows

Use one row per trace path or break. Include only populated links; mark unavailable evidence explicitly.

| Source / user need | Requirement | Allocation or satisfaction | Verification / validation evidence | Model reference | Evidence level | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `UN-001` | `SYS-001` | `SWE-014 → Controller` | `TEST-021` | `Package::Element` or `TBD` | `resolved` | linked / gap / proposed |

## Compact example

Input: `UN-001` says a home-use patient must be warned when delivery is interrupted. The available SysML v2 model contains `Pump::Controller` but no checked interruption-detection relation.

```markdown
Model evidence: text-inspected — `Pump::Controller` observed; no parser or compiler check supplied.

ID: SYS-001
Level: System
Requirement: If delivery is interrupted, the infusion pump shall present the defined interruption alarm to the intended user within <TBD> seconds of detection.
Parent links: UN-001
Risk-control status: proposed — pending risk-management approval
Verification: Test with a simulated interruption; pass criterion: <TBD>.
Model link: Pump::Controller (allocation proposed; no explicit allocation relation observed)
Open items: Define interruption, intended user, alarm, detection point, response time, risk-control ID, and test pass criterion.
```

| Source / user need | Requirement | Allocation or satisfaction | Verification / validation evidence | Model reference | Evidence level | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `UN-001` | `SYS-001` | `TBD` | `TBD` | `Pump::Controller` | `text-inspected` | proposed; allocation and evidence gaps |
