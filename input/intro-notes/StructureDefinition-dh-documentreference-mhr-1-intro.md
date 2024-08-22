### Usage scenarios

The following are supported usage scenarios for this profile:
- Reference the location of a CDA document in the My Health Record system

### Profile specific guidance
- The system will map `docStatus` as 'Final' if the 'Extrinsic object status' is 'Approved'. The system may not populate `docStatus` for other scenarios.
- The `author` element will reference a contained resource if it is a 'Practitioner', and direct reference if it is a 'Patient'



