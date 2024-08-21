### Usage scenarios

The following are supported usage scenarios for this profile:
- Query for a consolidated summary of a patient's problems, diagnoses, and health concerns

### Profile specific guidance
- For FHIR resources in the bundle that contain content for the Medical Conditions View, excluding Composition and Patient, there SHALL be
    - a Provenance resource that references
        - the specific FHIR resource in `Provenance.target.reference`
        - the document ID of the source CDA document in `Provenance.entity.what`
    - a DocumentReference resource that references the location of the source CDA document in `DocumentReference.content.attachment.url`


