### Introduction

The Australian Digital Health Agency FHIR Implementation Guide contains HL7™ FHIR® Release 4 (R4) artefacts authored and maintained by the Agency to support the electronic exchange of health information between individuals, healthcare providers, and the My Health Record system infrastructure in Australia.

It also supplements the [My Health Record FHIR Gateway](https://developer.digitalhealth.gov.au/resources/services/my-health-record/my-health-record-fhir-gateway) technical specifications that support developers connect apps and other products to the My Health Record system. The artefacts in this publication describe the data structure of the payload in the API response messages. 


Wherever possible, material in this specification is based on existing standards. All efforts have been made to minimise divergence from the HL7 Australia profiles of HL7 International standards to provide for system interoperability and compatibility with other profiles.

### How to read this guide

This guide is divided into several pages which are listed at the top of each page in the menu bar.

- [Home](index.html): This page provides the introduction and scope for this guide.
- [Conformance](conformance.html): This page describes the expectations for *Must Support* elements in the profiles in this guide.
- [Guidance](guidance.html): This page provides guidance about various artefcs that are defined in this guide.
- [Profile and Extensions](profiles-and-extensions.html): This page lists the FHIR profles and extesions that are defined in this guide.
- [Terminology](terminology.html): This page lists the FHIR terminology that are defined in this guide.
- [Examples](examples.html): This page lists all the examples used in this guide.
- [MHR Gateway API](MHRGatewayAPI.html): This page provides the introduction and scope for this guide.
- [Downloads](downloads.html): This page provides links to downloadable artefacts including the NPM package.
- [Disclaimers](disclaimers.html): This page lists the licensing, copyright, and disclaimers under which this guide is issued. 

### Relationships with other work

This implementation guide builds on other specifications, helping ensure a consistent approach to data sharing that should ease adoption. The specific guides used, and the portions relevant from each of them are as follows:

{% include dependency-table-short.xhtml %}

### Cross version analysis

{% include cross-version-analysis.xhtml %}

### Global profiles

{% include globals-table.xhtml %}

### Intellectual property considerations

This implementation guide and the underlying FHIR specification are licensed as public domain under the [FHIR license](http://hl7.org/fhir/R4/license.html). The license page also describes rules for the use of the FHIR name and logo.

{% include ip-statements.xhtml %}