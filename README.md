# Super Reform Mod

Prison Architect mod adding reform programs, skill pathways, specialized classrooms, and the Professor staff member.

Current working version: 1.10.0

## Current Scope

This mod is intentionally data-first. It expands reform and training content through `materials.txt`, `reform_programs.txt`, `jobs.txt`, and localization. It does not currently add Lua automation, production chains, grants, or custom job-generating objects.

The new job declarations are workgroup hooks for prisoners who pass the matching courses. They are intended to expose a clean skill/job pathway without claiming that inmates can fully replace gardeners, workmen, doctors, or construction crews. True replacement behavior likely needs job-generating objects and/or Lua.

## Rooms And Workgroups

| Room | Required research | Work qualification | Workgroup | Primary use |
| --- | --- | --- | --- | --- |
| Medical Classroom | Education | First Aid | MedicalClassroom | Medical and emergency courses |
| Outdoor Classroom | Education | Lawn Care | OutdoorClassroom | Lawn care, groundskeeping, horticulture |
| Building Classroom | Education | Basic Home Repair | BuildingClassroom | Repair, wiring, plumbing, construction skills |

## New Programs In 1.10.0

| Program | Room | Teacher | Prerequisite | Purpose |
| --- | --- | --- | --- | --- |
| Emergency Preparedness | Medical Classroom | Doctor | First Aid | Emergency response basics for inmates |
| Facilities Maintenance | Building Classroom | Workman | Basic Home Repair | Supervised maintenance pathway |
| Outdoor Maintenance Safety | Outdoor Classroom | Gardener | Lawn Care | Safe outdoor work habits |
| Horticulture Education | Outdoor Classroom | Gardener | Outdoor Maintenance Safety | Advanced plant and landscape care |
| Emergency Response Training | Classroom | Chief and Doctor | Ongoing Guard Training | Staff-only emergency response refresher |

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
- every job qualification in `data/jobs.txt` resolves to a reform program name
- every workgroup used by `data/jobs.txt` resolves to a room workgroup in `data/materials.txt`

Runtime validation:
- launch with `open steam://run/233450`
- enable only Super Reform Mod
- load a small or premade prison
- inspect `/Users/andrewsmith/Library/Application Support/Prison Architect/debug.txt`
- acceptance target: no custom `ReadMaterials`, `ReformProgramManager`, or mod `jobs.txt` parse errors

## Credits

Professor sprite by Gnr.McDude.

German translation by PimpTV.
