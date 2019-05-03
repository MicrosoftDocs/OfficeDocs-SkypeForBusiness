---
title: Patients App and EHR integration STU3 interface       
author: jambirk           
ms.author: jambirk        
manager: serdars                    
audience: ITPro            
ms.topic: article                   
ms.service: msteams         
search.appverid: MET150
localization_priority: Normal
ms.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: anach
description: Microsoft Teams Patient App EHR integration 
---

# STU3 interface specification

[!INCLUDE [preview-feature](../../includes/preview-feature.md)]

The FHIR server must support POST requests using bundles for the following resources:

- [Patient](#patient)
- [Observation](#observation)
- [Condition](#condition)
- [Encounter](#encounter)
- [Allergy Intolerance](#allergyintolerance)
- [Coverage](#coverage)
- [Medication Statement](#medication-request) (replaces the MedicationOrder in the DSTU2 version of the PatientsApp)
- Location (the information needed from this resource can be included in Encounter)

Note: The Patient resource is the only mandatory resource (without which the app will not load at all); However, it is recommended that the Partner implement support for all the above mentioned resources per specifications provided below for the best end-user experience with the Microsoft Teams Patients App.

Queries from the Patient App for more than one resource shall post a bundle (BATCH) of requests to the FHIR server's URL. The server shall process each request and return a bundle of the resources matched by each request. For more information and examples, see [https://www.hl7.org/fhir/STU3/http.html#transaction](https://www.hl7.org/fhir/STU3/http.html#transaction).

## Capability Statement

See [https://www.hl7.org/fhir/stu3/capabilitystatement.html](https://www.hl7.org/fhir/stu3/capabilitystatement.html).

These are the minimum required fields:

1. Rest
   1. Mode
   2. Interaction
   3. Resource: Type
   4. Security: [Extension for OAuth URIs](http://hl7.org/fhir/extension-oauth-uris.html)
2. FhirVersion (Our code requires this to understand which version we should pivot to.)

## Patient 

See [http://hl7.org/fhir/stu3/patient.html](http://hl7.org/fhir/stu3/patient.html).

Here are the minimum required fields, a subset of the Argonaut patient profile fields:

1. Name.Given
2. Name.Family
3. Gender
4. BirthDate
5. MRN (Identifier)

In addition to the [Argonaut fields](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-patient.html), for a great user experience, we can also read the following field(s):

1. Name.Use
2. Name.Prefix
3. [GeneralPractitioner] - The GeneralPractitioner reference should be included in the Patient resource (display field only)

Resource search using POST method at /Patient/_search and the following parameters:

1. id
2. family=(searches for all patients whose family name contains the value)
3. given=\<substring>
4. birthdate=(exact match)
5. gender=(values being one of the administrative-gender)
6. \_count (maximum number of results that should be returned) <br> The response should contain the total count of records returned as a result of the search and \_count will be used by the PatientsApp to limit the number of records returned.
7. identifier=\<mrn>

The goal is to be able to search and filter for a patient by the following:

- ID: This is the resource ID that every resource in FHIR has.
- MRN: This is the actual identifier for the patient that clinical staff would know. We understand this MRN is based on the type of identifier inside the identifier resource in FHIR
- Name
- Birthdate

See the following example call.

* * *

    Request:
    POST <fhir-server>/Patient/_search
    Request Body:
    given=ruth&family=black
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2019-01-14T23:44:45.052+00:00"
      },
      "type": "searchset",
      "total": 1,
      "link": [
        {
          "relation": "self",
          "url": <fhir-server>/Patient/_search"
        }
      ],
      "entry": [
        {
          "fullUrl": <fhir-server>/Patient/<patient-id>",
          "resource": {
            "resourceType": "Patient",
            "id": "<patient-id>",
            "meta": {
              "versionId": "1",
              "lastUpdated": "2017-10-18T18:32:37.000+00:00"
            },
            "text": {
              "status": "generated",
              "div": "<div>\n        <p>Ruth Black</p>\n      </div>"
            },
            "identifier": [
              {
                "use": "usual",
                "type": {
                  "coding": [
                    {
                      "system": "http://hl7.org/fhir/v2/0203",
                      "code": "MR",
                      "display": "Medical record number",
                      "userSelected": false
                    }
                  ],
                  "text": "Medical record number"
                },
                "system": "http://hospital.smarthealthit.org",
                "value": "1234567"
              }
            ],
            "active": true,
            "name": [
              {
                "use": "official",
                "family": "Black",
                "given": [
                  "Ruth",
                  "C."
                ]
              }
            ],
            "telecom": [
              {
                "system": "phone",
                "value": "800-599-2739",
                "use": "home"
              },
              {
                "system": "phone",
                "value": "800-808-7785",
                "use": "mobile"
              },
              {
                "system": "email",
                "value": "ruth.black@example.com"
              }
            ],
            "gender": "female",
            "birthDate": "1951-08-23",
            "address": [
              {
                "use": "home",
                "line": [
                  "26 South RdApt 22"
                ],
                "city": "Sapulpa",
                "state": "OK",
                "postalCode": "74066",
                "country": "USA"
              }
            ]
          },
          "search": {
            "mode": "match"
          }
        }
      ]
    }

* * *

    Request:
    GET <fhir-server>/Patient/<patient-id>
    
    Response:
    {
      "resourceType": "Patient",
      "id": "<patient-id>",
      "identifier": [
        {
          "use": "usual",
          "type": {
            "coding": [
              {
                "system": "http://hl7.org/fhir/v2/0203",
                "code": "MR",
              }
            ],
            "text": "Medical record number"
          },
          "value": "1234567"
        }
      ],
      "name": [
        {
          "use": "official",
          "family": "Adams",
          "given": [ "Daniel", "X." ]
        }
      ],
      "gender": "male",
      "birthDate": "1925-12-23",
    }

* * *

## Observation

See [https://www.hl7.org/fhir/stu3/observation.html](https://www.hl7.org/fhir/stu3/observation.html).

These are the minimum required fields, a subset of the [Argonaut Vital-Signs profile](https://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-vitalsigns.html).

1. Effective (date time or period)
2. Code.Coding.Code
3. ValueQuantity.Value

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

1. Code.Coding.Display
2. ValueQuantity.Unit

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _sort=-date
3. category (we will query for “category=vital-signs”) to retrieve the list of vital signs.

Refer to this example of the call.

* * *

    Request:
    GET <fhir-server>/Observation?patient=<patient-id>&category=vital-signs
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "type": "searchset",
      "total": 20,
      "entry": [
        {
          "resource": {
            "resourceType": "Observation",
            "id": "<resource-id>",
            "category": [
              {
                "coding": [
                  {
                    "system": "http://hl7.org/fhir/observation-category",
                    "code": "vital-signs"
                  }
                ],
              }
            ],
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "8867-4",
                  "display": "heart_rate"
                }
              ]
            },
            "effectiveDateTime": "2009-04-08T00:00:00-06:00",
            "valueQuantity": {
              "value": 72.0,
              "unit": "{beats}/min",
              "system": "http://unitsofmeasure.org",
            }
          }
        },
        .
        .
        .
      ]
    }

* * *

## Condition

See [http://hl7.org/fhir/stu3/condition.html](http://hl7.org/fhir/stu3/condition.html).

Here's the minimum required fields, a subset of the [Argonaut condition profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-condition.html).

1. Code.Coding[0].Display

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

1. AssertedDate
2. Severity

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _count=\<max results>

See the following example of this call.

* * *

    Request:
    GET <fhir-server>/Condition?patient=<patient-id>&_count=10
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "type": "searchset",
      "total": 2,
      "entry": [
        {
          "resource": {
            "resourceType": "Condition",
            "id": "<resource-id>",
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "185903001",
                  "display": "Needs influenza immunization",
                }
              ]
            },
            "severity": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "24484000",
                  "display": "Severe"
                }
              ]
            },
            "assertedDate": "2018-04-04"
          }
        },
        .
        .
        .
      ]
    }

* * *

## Encounter

See [http://hl7.org/fhir/stu3/encounter.html](http://hl7.org/fhir/stu3/encounter.html).

These are the minimum required fields, a subset of the [US Core Encounter profile](http://hl7.org/fhir/us/core/2018Jan/StructureDefinition-us-core-encounter.html) “must have” fields).

1. Status
2. Type[0].Coding[0].Display

In addition, the following fields from US Core Encounter profile’s “must support” fields:

1. Period.Start
2. Location[0].Location.Display

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _sort:desc=\<field ex. date>
3. _count=\<max results>

The goal is to be able to retrieve the patient’s last known location. Each encounter references a location resource. The reference shall also include the location’s display field.

## AllergyIntolerance

See [http://hl7.org/fhir/stu3/allergyintolerance.html](http://hl7.org/fhir/stu3/allergyintolerance.html).

These are the minimum required fields, a subset of the [Argonaut AllergyIntolerance](https://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-allergyintolerance.html) profile:

1. Code.Text
2. Code.Coding[0].Display
3. ClinicalStatus/VerificationStatus (we read both)

In addition to the Argonaut fields, for a great user experience, we can also read the following field:

1. AssertedDate
2. Note.Text
3. Reaction
    1. Substance (one coding element)
    2. Manifestation (one coding element)

Resource search using GET method and the following parameters:

1. Patient =  \<patient id>

For an example of the call, see the following.

* * *

    Request:
    GET <fhir-server>/AllergyIntolerance?patient=<patient-id>
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "type": "searchset",
      "total": 1,
      "entry": [
        {
          "resource": {
            "resourceType": "AllergyIntolerance",
            "id": "<resource-id>",
            "clinicalStatus": "active",
            "verificationStatus": "confirmed",
            "code": {
              "coding": [
                {
                  "system": "http://rxnav.nlm.nih.gov/REST/Ndfrt",
                  "code": "N0000175503",
                  "display": "sulfonamide antibacterial",
                }
              ],
              "text": "sulfonamide antibacterial"
            },
            "assertedDate": "2018-01-01T00:00:00-07:00",
            "reaction": [
              {
                "manifestation": [
                  {
                    "coding": [
                      {
                        "system": "http://snomed.info/sct",
                        "code": "271807003",
                        "display": "skin rash",
                      }
                    ],
                    "text": "skin rash"
                  }
                ],
              }
            ]
          }
        }
      ]
    }

* * *

## Medication Request

See [https://www.hl7.org/fhir/medicationrequest.html](https://www.hl7.org/fhir/medicationrequest.html).

These are the minimum required fields, a subset of the [US Core Medication Request profile](http://www.hl7.org/fhir/us/core/StructureDefinition-us-core-medicationrequest.html):

1. Medication.Display (if Reference)
2. Medication.Text (if CodableConcept)
3. AuthoredOn
4. Requester.Agent.Display

In addition to the US Core fields, for a great user experience, we can also read the following fields:

1. DosageInstruction[..].Text
2. Text

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _count=\<max results>

## Coverage

See [http://hl7.org/fhir/stu3/coverage.html](https://www.hl7.org/fhir/medicationrequest.html).

These are the minimum required fields, not covered by either US Core or Argonaut profiles:

1. Grouping, at least one element with
    1. GroupDisplay
    2. PlanDisplay
2. Period
3. SubscriberId

Resource search using GET method and the following parameters:

1. Patient = \<patient id>

\* We don't have a sample for Coverage, as it's not available on any open sandbox. However, it should work in a way that's similar to the other resources.
