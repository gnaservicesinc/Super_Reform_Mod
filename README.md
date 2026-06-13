# Super Reform Mod

Prison Architect mod adding reform programs, skill pathways, specialized classrooms, and the Professor staff member.

Current working version: 1.10.0

## Current Scope

This mod is intentionally data-first. It expands reform and training content through `materials.txt`, `reform_programs.txt`, and localization. It does not currently add Lua automation, production chains, grants, custom job-generating objects, or prisoner labor jobs.

Prisoner labor features are held behind runtime proof. Construction-worker and trustee concepts should not ship until qualified prisoners can be shown completing real construction, install, repair, or transfer tasks while unqualified prisoners cannot.

## Rooms

| Room | Required research | Primary use |
| --- | --- | --- |
| Medical Classroom | Education | Medical and emergency courses |
| Outdoor Classroom | Education | Lawn care, groundskeeping, horticulture |
| Building Classroom | Education | Repair, wiring, plumbing, construction skills |

## New Programs In 1.10.0

| Program | Room | Teacher | Prerequisite | Purpose |
| --- | --- | --- | --- | --- |
| Emergency Preparedness | Medical Classroom | Doctor | First Aid | Emergency response basics for inmates |
| Facilities Maintenance | Building Classroom | Workman | Basic Home Repair | Maintenance safety and upkeep |
| Outdoor Maintenance Safety | Outdoor Classroom | Gardener | Lawn Care | Safe outdoor work habits |
| Horticulture Education | Outdoor Classroom | Gardener | Outdoor Maintenance Safety | Advanced plant and landscape care |
| Emergency Response Training | Classroom | Chief and Doctor | Ongoing Guard Training | Staff-only emergency response refresher |

## Labor Feasibility Gate

The mod does not currently ship `data/jobs.txt`. The prior practice-job declarations duplicated reform classes without creating a meaningful production or staff-replacement outcome.

Use `BuilderCertificationTraining` as the internal qualification if construction-worker testing resumes. Candidate engine work queues from the vanilla Lua API are `Construction`, `PlaceObject`, and `RepairObject`; only ship a job path if a certified inmate completes real player-created construction, object placement, or repair work during Work or Free time and unqualified inmates do not.

Trustee testing should only use a transfer-oriented path such as `EscortPrisoner`. Do not ship trustees unless they can be isolated to escort/transfer work only, with no patrol, suppression, search, combat, armed, or normal guard duties.

## Existing Program Families

Academic and life-skill programs:
- Prison Policy Education
- SexEd
- First Aid
- Emergency Preparedness
- Money Management
- College Level Education
- Differential Equations Class
- Life Skills Education
- Continuing Education
- Special Education
- Legal Aid
- Legal Education

Building and practical programs:
- Basic Home Repair
- Facilities Maintenance
- Home Wiring Education
- Plumbing Education
- Heating and Cooling Repair
- Builder Certification Training
- Construction Engineering Education
- Construction Management
- Custodial Engineering Education

Outdoor and safety programs:
- Lawn Care
- Outdoor Maintenance Safety
- Horticulture Education
- Prison Safety
- Conduct Review by referral

Staff-only programs:
- Guard Training
- Ongoing Guard Training
- Emergency Response Training

## Validation

Static validation checklist:
- `git diff --check`
- no blank key/value lines in data files
- balanced top-level `BEGIN`/`END` blocks
- custom room `BEGIN Requirement` counts at 10 or fewer
- every `Name` in `data/reform_programs.txt` has `reformprogram_<Name>` and `reformprogram_<Name>_text` localization keys
- if `data/jobs.txt` exists during a spike, every job `Qualification` resolves to a reform program name and every job target maps to a proven in-game labor behavior

Runtime validation:
- launch with `open steam://run/233450`
- enable only Super Reform Mod
- load a small or premade prison
- inspect `/Users/andrewsmith/Library/Application Support/Prison Architect/debug.txt`
- acceptance target: no custom `ReadMaterials` or `ReformProgramManager` parse errors

## Credits

Professor sprite by Gnr.McDude.

German translation by PimpTV.
