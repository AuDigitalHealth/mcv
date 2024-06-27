### Must support and Obligation

Labelling an element [MustSupport]( https://www.hl7.org/fhir/conformance-rules.html#mustSupport) means that implementations that produce or consume resources **SHALL** provide support for the element in some meaningful way. The specifications and/or profiles that define a particular implementation context **SHALL** make clear the required support for that context. 

This implementation guide inherits the definitions of `mustSupport` and `obligation` from AU Core, in which the meaning of `mustSupport` is specified in terms of [Obligation Codes](https://hl7.org/fhir/extensions/CodeSystem-obligation.html) in [obligation extensions](https://hl7.org/fhir/extensions/StructureDefinition-obligation.html) on the element definition. Another key component are the ActorDefinitions that define the systems that play a role in data exchange. In the context of this implementation guide, the My Health Record system acts as the [AU Core Responder](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-responder.html), and systems connecting to the My Health Record system via the My Health Record FHIR Gateway act as the [AU Core Requester](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-requester.html).

*Must Support* elements are treated differently between AU Core Responder and AU Core Requester actors. *Must Support* on a profile element for an AU Core Requester are reiterated below and **SHALL** be interpreted as follows.

An AU Core Requester:
- **SHALL** accept resources containing any valid value for `mustSupport` elements without error.
- **SHALL** accept resources containing `mustSupport` elements with [Missing Data](https://build.fhir.org/ig/hl7au/au-fhir-core/general-requirements.html#missing-data) or [Suppressed data](https://build.fhir.org/ig/hl7au/au-fhir-core/general-requirements.html#suppressed-data) without error.

When a `mustSupport` element requires a more tightly stated obligation, this obligation is specified in the AU Core Responder obligation extension on the element definition. In addition to `mustSupport` and `obligation` inherited from AU Core, this implementation guide includes the following obligations on AU Core Requesters.

Actor | Code | Display | Definition | Notes
--- | --- | --- | --- | ---
[AU Core Requester](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-requester.html) | [SHALL:handle](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-SHALL.58handle) | SHALL correctly handle | Conformant applications SHALL handle the meaning of this element correctly. | This rule is vague in that doesn't specify any particular handling of the element. But it's important because an application that ignores this element is non-conformant. A good example would be a status code of 'entered-in-error' - how exactly a Resource Consumer handles this depends on the use case etc., but the application can never simply ignore such a status code. Note that whether the resource or information from it is stored for later use is irrelevant - when the resource or information in it is processed, the consequences of the element are considered. That may mean not retaining the information for later use, or informing the user, etc. Typically, this obligation marks that there are known patient safety issues that can arise if the element is ignored. Implementers should pay particular attention to the possible range of values for the element from a safety perspective.

How the system processes the resource depends on local requirements that could align with obligation terms such as [reject invalid](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-reject-invalid), [correctly handle](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-handle), [persist](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-persist), [display](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-display), or [ignore](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-ignore).


**Presentation of elements labelled MustSupport in profile views**

When viewing the raw JSON of a profile, elements labelled *MustSupport* are flagged as `mustSupport` set to "true". Obligations are specified using the obligation extension.

Example: Medical Conditions View Condition profile showing recordedDate with `mustSupport` and `obligation`
~~~
{
    "resourceType" : "StructureDefinition",
    ...
    "url" : "http://ns.electronichealth.net.au/fhir/StructureDefinition/dh-condition-mcv-1",
    ...
    "type" : "Condition",
    "baseDefinition" : "http://hl7.org.au/fhir/core/StructureDefinition/au-core-condition",     
    ...
           {
              "id" : "Condition.recordedDate",
        "extension" : [
          {
            "extension" : [
              {
                "url" : "code",
                "valueCode" : "SHALL:populate-if-known"
              },
              {
                "url" : "actor",
                "valueCanonical" : "http://hl7.org.au/fhir/core/ActorDefinition/au-core-actor-responder"
              }
            ],
            "url" : "http://hl7.org/fhir/StructureDefinition/obligation"
          },
          {
            "extension" : [
              {
                "url" : "code",
                "valueCode" : "SHALL:no-error"
              },
              {
                "url" : "actor",
                "valueCanonical" : "http://hl7.org.au/fhir/core/ActorDefinition/au-core-actor-requester"
              }
            ],
            "url" : "http://hl7.org/fhir/StructureDefinition/obligation"
          },
          {
            "extension" : [
              {
                "url" : "code",
                "valueCode" : "SHALL:handle"
              },
              {
                "url" : "actor",
                "valueCanonical" : "http://hl7.org.au/fhir/core/ActorDefinition/au-core-actor-requester"
              }
            ],
            "url" : "http://hl7.org/fhir/StructureDefinition/obligation"
          }
        ],
        "path" : "Condition.recordedDate",
        "min" : 1,
        "mustSupport" : true
           },

    ...
}
~~~

When rendered in an implementation publication, each profile is presented different formal views of all the elements in a tree format.

- The elements labelled `mustSupport` are flagged with an <span style="padding-left: 3px; padding-right: 3px; color: white; background-color: red" title="This element must be supported">S</span>.
-  The elements labelled `obligation` are flagged with an <span style="padding-left: 3px; padding-right: 3px; color: white; background-color: red" title="This element has obligations">O</span>.

To see the full set of elements that must be supported and obligations associated with its use, a reader must use the "Key Elements Table" or "Snapshot Table". Implementers should take note that the "Differential Table" only represents constraints introduced on the base profile.


