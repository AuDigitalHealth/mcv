### Usage scenarios

The following are supported usage scenarios for this profile:
- Query for a consolidated summary of a patient's problems, diagnoses, and health concerns

### Profile specific guidance
- There will be an instance of `Condition.category` that contains a code value of 'problem-list-item'. Some CDA source documents may also contain information about the type of problem or diagnosis that is relevant to a view of medical conditions. If present, this data will be supplied in an additional instance of `Condition.category`, which may be either a coding or a text value.


