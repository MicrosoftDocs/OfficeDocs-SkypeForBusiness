---
title:  Patients App and EHR integration DSTU2 interface       
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


# DSTU2 interface specification

The FHIR server must support POST requests using bundles for the following resources:

- [Patient](#patient)
- [Observation](#observation)
- [Condition](#condition)
- [Encounter](#encounter)
- [Allergy intolerance](#allergyintolerance)
- [Coverage](#coverage)
- [Medication Order](#medication-order)
- [Location](#location)

> [!NOTE]
> The Patient resource is the only mandatory resource (without which the app will not load at all. However, it is recommended that the Partner implement support for all the above mentioned resources per specifications provided below for the best end-user experience with the Microsoft Teams Patients App.

Queries from the Patient App for more than one resource post a bundle (BATCH) of requests to the FHIR server's URL. The server processes each request and returns a bundle of the resources matched by each request. For more information and examples, see [https://www.hl7.org/fhir/DSTU2/http.html#transaction](https://www.hl7.org/fhir/DSTU2/http.html#transaction).

All the following FHIR resources should be accessible by direct resource reference. 

## Conformance minimum required field set

See [https://www.hl7.org/fhir/dstu2/conformance.html](https://www.hl7.org/fhir/dstu2/conformance.html). The FHIR Server must implement the conformance statement for us to have a factual summary of its capabilities. We expect the below parameters in a DSTU2 FHIR Server:

1. Rest
   1. Mode
   2. Interaction
   3. Resource: Type
   4. Security: [Extension for OAuth URIs](http://hl7.org/fhir/extension-oauth-uris.html)
2. FhirVersion (Our code requires this to understand which version we should pivot to as we support multiple versions.)

## Patient

See [https://www.hl7.org/fhir/DSTU2/Patient.html](https://www.hl7.org/fhir/DSTU2/Patient.html).

These are the minimum required fields, a subset of the [Argonaut patient profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-patient.html) fields:

1. Name.Family
2. Name.Given
3. Gender
4. BirthDate
5. MRN (Identifier)

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

1. Name.Use
2. Name.Prefix
3. CareProvider (This reference on the Patient resource should include the display fields shown in the following example.)

* * *
    Request:
    GET <fhir-server>/Patient/<patient-id>
    
    Response:
    {
      "resourceType": "Patient",
      "id": "<patient-id>",
      .
      .
      .
      "name": [
        {
          "use": "official",
          "prefix": [ "Mr" ],
          "family": [ "Chau" ],
          "given": [ "Hugh" ]
        }
      ],
      "identifier": [
        {
          "use": "official",
          "type": {
            "coding": [
              {
                "system": "http://hl7.org/fhir/v2/0203",
                "code": "MR"
              }
            ]
          },
          "value": "1234567"
        }
      ],
      "gender": "male",
      "birthDate": "1957-06-05",
      "careProvider": [{ "display": "Jane Doe" }],
    }
* * * 


Resource search using POST method at /Patient/_search and the following parameters:

1. id
2. family:contains=(searches for all patients whose family name contains the value.)
3. given=\<substring>
4. name=\<substring>
5. birthdate=(exact match)
6. \_count (maximum number of results that should be returned) <br> The response should contain the total count of records returned as a result of the search, and \_count will be used by the PatientsApp to limit the number of records returned.
7. identifier=\<mrn>

The goal is to be able to search and filter for a patient by the following:

- ID: This is the resource ID that every resource in FHIR has.
- MRN: This is the actual identifier for the patient that clinical staff would know. We understand this MRN is based on the type of identifier inside the identifier resource in FHIR
- Name
- Birthdate

See the following example  of this call.

* * * 
    Request:
    POST <fhir-server>/Patient/_search
    Request Body:
    given=hugh&family=chau
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      .
      .
      .
      "entry": [
        {
          "resource": {
            "resourceType": "Patient",
            "id": "<patient-id>",
            "name": [
              {
                "text": "Hugh Chau",
                "family": [ "Chau" ],
                "given": [ "Hugh" ]
              }
            ],
            "gender": "male",
            "birthDate": "1957-06-05"
          },
          "search": {
            "mode": "match"
          }
        }
      ]
    }
* * *

## Observation

See [https://www.hl7.org/fhir/DSTU2/Observation.html](https://www.hl7.org/fhir/DSTU2/Observation.html).

These are the minimum required fields, a subset of the Argonaut vital signs profile:

 1. Effective (date time or period)
 2. Code.Coding.Code
 3. ValueQuantity.Value

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

 1. Code.Coding.Display
 2. ValueQuantity.Unit

If using component observations, the same logic applies for each component observation.

Resource search using GET method and the following parameters:

1. patient=\<patient id\>
2. sort:desc=\<field ex. date\>

The goal is to be able to retrieve the latest vital signs for a patient, [VitalSigns.DSTU.saz]  (observation?).

* * *
    Request:
    GET <fhir-server>/Observation?patient=<patient-id>&_sort:desc=date&category=vital-signs
    
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
            "category": {
              "coding": [ { code": "vital-signs" } ],
            },
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "39156-5",
                  "display": "bmi"
                }
              ],
            },
            "effectiveDateTime": "2009-12-01",
            "valueQuantity": {
              "value": 34.4,
              "unit": "kg/m2",
              "system": "http://unitsofmeasure.org",
              "code": "kg/m2"
            }
          },
        },
        .
        .
        .
      ]
    }
* * *

## Condition

See [https://www.hl7.org/fhir/DSTU2/Condition.html](https://www.hl7.org/fhir/DSTU2/Condition.html).

These are the minimum required fields, a subset of the [Argonaut condition profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-condition.html):

1. Code.Coding[0].Display

In addition to the Argonaut fields, for a great user experience, we can also read the following field(s):

1. Date Recorded
2. Severity

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _count=\<max results>

See the following example of this call:

* * *
    Request:
    GET <fhir-server>/Condition?patient=<patient-id>&_count=10
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "type": "searchset",
      "total": 1,
      "entry": [
        {
          "resource": {
            "resourceType": "Condition",
            "id": "<resource-id>",
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "386033004",
                  "display": "Neuropathy (nerve damage)"
                }
              ]
            },
            "dateRecorded": "2018-09-17",
            "severity": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "24484000",
                  "display": "Severe"
                }
              ]
            }
          },
        }
      ]
    }
* * *

## Encounter

See [https://www.hl7.org/fhir/DSTU2/Encounter.htm](https://www.hl7.org/fhir/DSTU2/Encounter.htm).

These are the minimum required fields, a subset of the US Core Encounter profile “must have” fields:

1. Status
2. Type[0].Coding[0].Display

In addition, the following fields from US Core Encounter profile’s “must support” fields

1. Period.Start
2. Location[0].Location.Display

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _sort:desc=\<field ex. date>
3. _count=\<max results>

The goal is to be able to retrieve the patient’s last known location. Each encounter references a location resource. The reference shall also include the location’s display field. See the following example of this call.
* * *
    Request:
    GET <fhir-server>/Encounter?patient=<patient-id>&_sort:desc=date&_count=1
    
    Response:
    {
      "resourceType": "Bundle",
      "type": "searchset",
      "total": 1,
      "entry": [
        {
          "resource": {
            "resourceType": "Encounter",
            "id": "<resource-id>",
            "identifier": [{ "use": "official", "value": "<id>" }],
            "status": "arrived",
            "type": [
              {
                "coding": [{ "display": "Appointment" }],
              }
            ],
            "patient": { "reference": "Patient/<patient-id>" },
            "period": { "start": "09/17/2018 1:00:00 PM" },
            "location": [
              {
                "location": { "display": "Clinic - ENT" },
              }
            ]
          }
        }
      ]
    }
* * *

## AllergyIntolerance

See [https://www.hl7.org/fhir/DSTU2/AllergyIntolerance.html](https://www.hl7.org/fhir/DSTU2/AllergyIntolerance.html).

These are the minimum required fields, a subset of the Argonaut AllergyIntolerance profile:

1. Code.Text
2. Code.Coding[0].Display
3. Status

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

1. RecordedDate
2. Note.Text
3. Reaction[..].Substance.Text
4. Reaction[..].Manifestation[..].Text
5. Text.Div

Resource search using GET method and the following parameters:

1. Patient =  \<patient id>

See the following example of this call.

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
            "recordedDate": "2018-09-17T07:00:00.000Z",
            "substance": {
              "text": "Cashew nuts"
            },
            "status": "confirmed",
            "reaction": [
              {
                "substance": {
                  "text": "cashew nut allergenic extract Injectable Product"
                },
                "manifestation": [
                  {
                    "text": "Anaphylactic reaction"
                  }
                ]
              }
            ]
          }
        }
      ]
    }
* * *

## Medication Order

See [https://www.hl7.org/fhir/DSTU2/MedicationOrder.html](https://www.hl7.org/fhir/DSTU2/MedicationOrder.html).

These are the minimum required fields, a subset of the Argonaut MedicationOrder profile:

1. DateWritten
2. Prescriber.Display
3. Medication.Display (if reference)
4. Medication.Text (if concept)

In addition to the Argonaut fields, for a great user experience, we can also read the following fields:

1. DateEnded
2. DosageInstruction.Text
3. Text.Div

Resource search using GET method and the following parameters:

1. patient=\<patient id>
2. _count=\<max results>

See the following example of this call:

* * *
    Request:
    GET <fhir-server>/MedicationOrder?patient=<patient-id>&_count=10
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "type": "searchset",
      "total": 1,
      "entry": [
        {
          "resource": {
            "resourceType": "MedicationOrder",
            "id": "<resource-id>",
            "dateWritten": "2018-09-17",
            "medicationCodeableConcept": {
              "text": "Lisinopril 20 MG Oral Tablet"
            },
            "prescriber": {
              "display": "Jane Doe"
            },
            "dosageInstruction": [
              {
                "text": "1 daily"
              }
            ]
          }
        }
      ]
    }
* * *  

## Coverage

See [https://www.hl7.org/fhir/DSTU2/Coverage.html](https://www.hl7.org/fhir/DSTU2/Coverage.html).

These are the minimum required fields, not covered by either US Core or Argonaut profiles:

1. Payor

Resource search using GET method and the following parameters:

1. patient=\<patient id>

See the following example of this call:

* * *
    Request:
    GET <fhir-server>/Coverage?patient=<patient-id>
    
    Response:
    {
      "resourceType": "Bundle",
      "type": "searchset",
      "total": 1,
      "entry": [
        {
          "resource": {
            "resourceType": "Coverage",
            "id": "<resource-id>",
            "plan": "No Primary Insurance",
            "subscriber": { "reference": "Patient/<patient-id>" }
          }
        }
      ]
    }
* * *

## Location

See [https://www.hl7.org/fhir/DSTU2/Location.html](https://www.hl7.org/fhir/DSTU2/Location.html).

This resource is only being used as a reference on the [Encounter](#encounter) resource.
