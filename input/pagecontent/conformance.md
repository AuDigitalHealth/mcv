### Must support and Obligation

Labelling an element [MustSupport]( https://www.hl7.org/fhir/conformance-rules.html#mustSupport) means that implementations that produce or consume resources **SHALL** provide support for the element in some meaningful way. The specifications and/or profiles that define a particular implementation context **SHALL** make clear the required support for that context. 

This implementation guide follows the usage of `mustSupport` and `obligation` established in [AU Core](https://build.fhir.org/ig/hl7au/au-fhir-core/general-requirements.html#must-support-and-obligation), in which the meaning of `mustSupport` is specified in terms of [Obligation Codes](https://hl7.org/fhir/extensions/CodeSystem-obligation.html) in [obligation extensions](https://hl7.org/fhir/extensions/StructureDefinition-obligation.html) on the element definition. Another key component is the `actor` that plays a role in data exchange. Implementers need to be aware that profiles deriving from AU Core will inherit AU Core `mustSupport`, `obligation` and `actor` definitions.

The following actors exhibit these behaviours in the context of this implementation guide:
- Systems connecting to the My Health Record system via the My Health Record FHIR Gateway 
    - **SHALL** act as a [MHR Gateway Requester](ActorDefinition-mhr-gw-actor-requester.html)
    - **MAY** act as an [AU Core Requester](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-requester.html)

- The My Health Record system **MAY NOT** act as an [AU Core Responder](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-responder.html)


The obligation codes used to define the minimum obligations of Must Support elements in this implementation guide are reiterated below.

Actor | Code | Display | Definition | Notes
--- | --- | --- | --- | ---
[MHR Gateway Requester](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-requester.html) | [SHALL:handle](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-SHALL.58handle) | SHALL correctly handle | Conformant applications SHALL handle the meaning of this element correctly. | This rule is vague in that doesn't specify any particular handling of the element. But it's important because an application that ignores this element is non-conformant. A good example would be a status code of 'entered-in-error' - how exactly a Resource Consumer handles this depends on the use case etc., but the application can never simply ignore such a status code. Note that whether the resource or information from it is stored for later use is irrelevant - when the resource or information in it is processed, the consequences of the element are considered. That may mean not retaining the information for later use, or informing the user, etc. Typically, this obligation marks that there are known patient safety issues that can arise if the element is ignored. Implementers should pay particular attention to the possible range of values for the element from a safety perspective.

*Must Support* on a profile element for a [MHR Gateway Requester](https://build.fhir.org/ig/hl7au/au-fhir-core/ActorDefinition-au-core-actor-requester.html) are reiterated below and **SHALL** be interpreted as follows.

#### MHR Gateway Requester

A MHR Gateway Requester:
-  **SHALL** handle information in elements flagged with *Must Support*.

How the system handles the information depends on local requirements that could align with obligation terms such as [display](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-display), [process](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-process), or [print](https://hl7.org/fhir/extensions/CodeSystem-obligation.html#obligation-print).


#### Presentation of elements labelled MustSupport and Obligation in profile views

When rendered in an implementation publication, each profile is presented different formal views of all the elements in a tree format.

- The elements labelled `mustSupport` are flagged with an <span style="padding-left: 3px; padding-right: 3px; color: white; background-color: red" title="This element must be supported">S</span>.
-  The elements labelled `obligation` are flagged with an <span style="padding-left: 3px; padding-right: 3px; color: white; background-color: red" title="This element has obligations">O</span>.
-  The elements labelled with both `mustSupport` and `obligation` are flagged with an <span style="padding-left: 3px; padding-right: 3px; color: white; background-color: red" title="This element has obligations and must be supported">SO</span>.

To see the full set of elements that must be supported and obligations associated with its use, a reader must use the "Key Elements Table" or "Snapshot Table". Implementers should take note that the "Differential Table" only represents constraints introduced on the base profile.


