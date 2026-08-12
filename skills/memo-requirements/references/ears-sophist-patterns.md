# EARS and SOPHIST patterns

## EARS sentence patterns

Use the minimum pattern that conveys the condition and response. Replace angle-bracket text with controlled project terminology.

| Situation | Pattern | Example |
| --- | --- | --- |
| Always applicable | `The <system> shall <response>.` | `The infusion controller shall record each confirmed dose event.` |
| Event-driven | `When <trigger>, the <system> shall <response>.` | `When the user confirms a dose, the infusion controller shall record the dose event.` |
| State-driven | `While <state>, the <system> shall <response>.` | `While infusion is active, the infusion controller shall display the elapsed infusion time.` |
| Optional feature | `Where <feature is present>, the <system> shall <response>.` | `Where network export is enabled, the system shall authenticate each export request.` |
| Unwanted behavior | `If <fault or undesired condition>, the <system> shall <response>.` | `If a sensor value is outside its validated input range, the system shall reject the value and record the fault.` |
| Combined | `While <state>, when <trigger>, the <system> shall <response>.` | `While a session is active, when communication is lost, the system shall enter the defined safe state within <TBD> seconds.` |

Avoid `should`, `may`, `support`, `user-friendly`, `fast`, `as appropriate`, `etc.`, and ambiguous pronouns. Do not use an EARS condition to hide an undefined concept; define the state, trigger, and terms in the controlled glossary.

## SOPHIST quality rules

Write a requirement so a reviewer can answer yes to each question:

| Rule | Review question |
| --- | --- |
| Necessary | Is there a source, rationale, user need, risk control, interface contract, or decision requiring it? |
| Atomic | Does it state one independently testable obligation? |
| Unambiguous | Would different readers interpret it the same way? |
| Complete | Are trigger, subject, response, constraints, exceptions, units, and timing stated or linked? |
| Consistent | Does it agree with sibling requirements, definitions, interfaces, and system states? |
| Feasible | Can the allocated element implement it within known constraints? |
| Verifiable | Is there an objective method and pass criterion? |
| Traceable | Does it link to source, parent/child requirements, risk evidence, and verification or validation? |

## SOPHIST-style construction

Build the sentence from these elements:

`<condition> + <subject> + shall + <action verb> + <object/result> + <constraint>`

Use a specific action verb (`store`, `prevent`, `display`, `transmit`, `calculate`, `enter`) and an observable object or result. Define any quantity with unit, resolution or tolerance, range, and reference condition as needed.

### Rewrite examples

| Weak wording | Improved wording | Why |
| --- | --- | --- |
| `The app shall be easy to use.` | `TBD: Define the intended user, critical task, use environment, and validation success criteria.` | A usability claim needs a task and evidence. |
| `The system shall quickly alert the user if there is a problem.` | `If the system detects <defined fault>, the system shall present <defined alert> to the <intended user> within <TBD> seconds of detection.` | Defines condition, response, recipient, and timing. |
| `The device shall store data securely.` | `Where audit logging is enabled, the system shall retain <defined event fields> with <defined access-control and integrity properties>.` | “Securely” must be decomposed into measurable properties. |
