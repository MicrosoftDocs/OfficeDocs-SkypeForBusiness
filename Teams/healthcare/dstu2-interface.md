---
title:  Patients App DSTU2 interface       
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
- [Medication order](#allergyintolerance)
- [Location](#location)

> [!NOTE]
> The Patient resource is the only mandatory resource (without which the app will not load at all. However, it is recommended that the Partner implement support for all the above mentioned resources per specifications provided below for the best end-user experience with the Microsoft Teams Patients App.

Queries from the Patient App for more than one resource post a bundle (BATCH) of requests to the FHIR server's URL. The server processes each request and returns a bundle of the resources matched by each request. For more information and examples, see [https://www.hl7.org/fhir/DSTU2/http.html#transaction](https://www.hl7.org/fhir/DSTU2/http.html#transaction).

All the following FHIR resources should be accessible by direct resource reference. For example, /Patient/id.

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
      "meta": {
      "versionId": "1",
        "lastUpdated": "2018-09-18T01:28:26.000+00:00"
      },
      "text": {
        "status": "generated",
        "div": "<div><div>Hugh <b>CHAU </b></div><table><tbody><tr><td>Date of birth</td><td><span>05 June 1957</span></td></tr></tbody></table></div>"
      },
      "active": true,
      "name": [
        {
          "text": "Hugh Chau",
          "family": [
            "Chau"
          ],
          "given": [
            "Hugh"
          ]
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

For an example of what the call returns, see the following reply example .

* * * 
    Request:
    POST <fhir-server>/Patient/_search
    Request Body:
    given=hugh&family=chau
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2018-10-30T00:21:34.943+00:00"
      },
      "type": "searchset",
      "total": 1,
      "link": [
        {
          "relation": "self",
          "url": "<fhir-server>/Patient/_search"
        }
      ],
      "entry": [
        {
          "fullUrl": "<fhir-server>/Patient/<patient-id>",
          "resource": {
            "resourceType": "Patient",
            "id": "<patient-id>",
            "meta": {
              "versionId": "1",
              "lastUpdated": "2018-09-18T01:28:26.000+00:00"
            },
            "text": {
              "status": "generated",
              "div": "<div><div>Hugh <b>CHAU </b></div><table><tbody><tr><td>Date of birth</td><td><span>05 June 1957</span></td></tr></tbody></table></div>"
            },
            "active": true,
            "name": [
              {
                "text": "Hugh Chau",
                "family": [
                  "Chau"
                ],
                "given": [
                  "Hugh"
                ]
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
    GET <fhir-server>/Observation?patient=<patient-id>&_sort:desc=date&    category=vital-signs
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2019-04-01T15:41:53.598+00:00"
      },
      "type": "searchset",
      "total": 20,
      "link": [
        {
          "relation": "self",
          "url": "<fhir-server>/Observation?_sort%3Adesc=date&category=vital-signs&patient=<patient-id>"
        }
      ],
      "entry": [
        {
          "fullUrl": "<fhir-server>/Observation/<resource-id>",
          "resource": {
            "resourceType": "Observation",
            "id": "<resource-id>",
            "meta": {
              "versionId": "3",
              "lastUpdated": "2018-01-31T22:43:25.000+00:00"
            },
            "text": {
              "status": "generated",
              "div": "<div>2009-12-01: bmi = 34.4 kg/m2</div>"
            },
            "status": "final",
            "category": {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/observation-category",
                  "code": "vital-signs",
                  "display": "Vital Signs"
                }
              ],
              "text": "Vital Signs"
            },
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "39156-5",
                  "display": "bmi"
                }
              ],
              "text": "bmi"
            },
            "subject": {
              "reference": "Patient/<patient-id>"
            },
            "encounter": {
              "reference": "Encounter/<resource-id>"
            },
            "effectiveDateTime": "2009-12-01",
            "valueQuantity": {
              "value": 34.4,
              "unit": "kg/m2",
              "system": "http://unitsofmeasure.org",
              "code": "kg/m2"
            }
          },
          "search": {
            "mode": "match"
          }
        },
        {
          "fullUrl": "<fhir-server>/Observation/<resource-id>",
          "resource": {
            "resourceType": "Observation",
            "id": "<resource-id>",
            "meta": {
              "versionId": "3",
              "lastUpdated": "2018-01-31T22:43:25.000+00:00"
            },
            "text": {
              "status": "generated",
              "div": "<div>2009-12-01: Blood pressure 100/60 mmHg<div>"
            },
            "status": "final",
            "category": {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/observation-category",
                  "code": "vital-signs",
                  "display": "Vital Signs"
                }
              ],
              "text": "Vital Signs"
            },
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "55284-4",
                  "display": "Blood pressure systolic and diastolic"
                }
              ],
              "text": "Blood pressure systolic and diastolic"
            },
            "subject": {
              "reference": "Patient/<patient-id>"
            },
            "encounter": {
              "reference": "Encounter/<resource-id>"
            },
            "effectiveDateTime": "2009-12-01",
            "component": [
              {
                "code": {
                  "coding": [
                    {
                      "system": "http://loinc.org",
                      "code": "8480-6",
                      "display": "Systolic blood pressure"
                    }
                  ],
                  "text": "Systolic blood pressure"
                },
                "valueQuantity": {
                  "value": 100,
                  "unit": "mmHg",
                  "system": "http://unitsofmeasure.org",
                  "code": "mm[Hg]"
                }
              },
              {
                "code": {
                  "coding": [
                    {
                      "system": "http://loinc.org",
                      "code": "8462-4",
                      "display": "Diastolic blood pressure"
                    }
                  ],
                  "text": "Diastolic blood pressure"
                },
                "valueQuantity": {
                  "value": 60,
                  "unit": "mmHg",
                  "system": "http://unitsofmeasure.org",
                  "code": "mm[Hg]"
                }
              }
            ]
          },
          "search": {
            "mode": "match"
          }
        },
        {
          "fullUrl": "<fhir-server>/Observation/<resource-id>",
          "resource": {
            "resourceType": "Observation",
            "id": "<resource-id>",
            "meta": {
              "versionId": "3",
              "lastUpdated": "2018-01-31T22:43:25.000+00:00"
            },
            "text": {
              "status": "generated",
              "div": "<div>2009-12-01: respiratory_rate = 20.0     {breaths}/min</div>"
            },
            "status": "final",
            "category": {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/observation-category",
                  "code": "vital-signs",
                  "display": "Vital Signs"
                }
              ],
              "text": "Vital Signs"
            },
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "9279-1",
                  "display": "respiratory_rate"
                }
              ],
              "text": "respiratory_rate"
            },
            "subject": {
          "reference": "Patient/<patient-id>"
            },
            "encounter": {
              "reference": "Encounter/<resource-id>"
            },
            "effectiveDateTime": "2009-12-01",
            "valueQuantity": {
              "value": 20.0,
              "unit": "{breaths}/min",
              "system": "http://unitsofmeasure.org",
              "code": "{breaths}/min"
            }
          },
          "search": {
            "mode": "match"
          }
        },
        .....
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

For an example of  the call, see the following sample:

* * *
    Request:
    GET <fhir-server>/Condition?patient=<patient-id>&_count=10
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2018-10-30T01:12:09.182+00:00"
      },
      "type": "searchset",
      "total": 1,
      "link": [
        {
          "relation": "self",
          "url": "<fhir-server>/Condition?_count=10&    patient=<patient-id>"
        }
      ],
      "entry": [
        {
          "fullUrl": "<fhir-server>/Condition/<resource-id>",
          "resource": {
            "resourceType": "Condition",
            "id": "<resource-id>",
            "meta": {
              "versionId": "1",
              "lastUpdated": "2018-09-18T01:17:24.000+00:00"
            },
            "patient": {
              "reference": "Patient/<patient-id>"
            },
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "386033004",
                  "display": "Neuropathy (nerve damage)"
                }
              ],
              "text": "Neuropathy (nerve damage)"
            },
            "clinicalStatus": "active",
            "verificationStatus": "confirmed",
            "onsetDateTime": "2018-09-17T07:00:00.000Z"
          },
          "search": {
            "mode": "match"
          }
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

The goal is to be able to retrieve the patient’s last known location. Each encounter references a location resource. The reference shall also include the location’s display field. For an example of the call, see the following sample.
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
            "class": "outpatient",
            "type": [
              {
                "coding": [
                  {
                    "code": "Appointment",
                    "display": "Appointment"
                  }
                ],
                "text": "Visit Type"
              }
            ],
            "patient": { "reference": "Patient/<patient-id>" },
            "participant": [
              {
                "individual": {
                  "reference": "Practitioner/<practitioner-id>",
                  "display": "John Doe"
                }
              }
            ],
            "period": { "start": "09/17/2018 1:00:00 PM" },
            "location": [
              {
                "location": { "display": "Clinic - ENT" },
                "status": "active"
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

For an example of the call, see the following example.

* * *
    Request:
    GET <fhir-server>/AllergyIntolerance?patient=<patient-id>
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2018-10-30T01:37:08.819+00:00"
      },
      "type": "searchset",
      "total": 1,
      "link": [
        {
          "relation": "self",
          "url": "<fhir-server>/AllergyIntolerance?patient=<patient-id>"
        }
      ],
      "entry": [
        {
          "fullUrl": "<fhir-server>/AllergyIntolerance/<resource-id>",
          "resource": {
            "resourceType": "AllergyIntolerance",
            "id": "8",
            "meta": {
              "versionId": "1",
              "lastUpdated": "2018-09-17T21:00:31.000+00:00"
            },
            "onset": "2018-09-17T07:00:00.000Z",
            "recordedDate": "2018-09-17T07:00:00.000Z",
            "patient": {
              "reference": "Patient/<patient-id>"
            },
            "substance": {
              "coding": [
                {
                  "code": "N0000175503",
                  "display": "sulfonamide antibacterial"
                }
              ],
              "text": "sulfonamide antibacterial"
            },
            "status": "confirmed",
            "criticality": "CRITL",
            "type": "allergy",
            "category": "medication"
          },
          "search": {
            "mode": "match"
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

For an example of the call (Fiddle trace), see the following

* * *
    Request:
    GET <fhir-server>/MedicationOrder?patient=<patient-id>&_count=10
    
    Response:
    {
      "resourceType": "Bundle",
      "id": "<bundle-id>",
      "meta": {
        "lastUpdated": "2018-10-30T02:01:31.148+00:00"
      },
      "type": "searchset",
      "total": 1,
      "link": [
        {
          "relation": "self",
          "url": "<fhir-server>/MedicationOrder?_count=10&patient=<patient-id>"
        }
      ],
      "entry": [
        {
          "fullUrl": "<fhir-server>/MedicationOrder/<resource-id>",
          "resource": {
            "resourceType": "MedicationOrder",
            "id": "<resource-id>",
            "meta": {
              "versionId": "1",
              "lastUpdated": "2018-09-17T20:59:17.000+00:00"
            },
            "dateWritten": "2018-09-17T07:00:00.000Z",
            "status": "active",
            "dateEnded": "2018-09-17T07:00:00.000Z",
            "patient": {
              "reference": "Patient/<patient-id>"
            },
            "medicationCodeableConcept": {
              "coding": [
                {
                  "code": "314077",
                  "display": "Lisinopril 20 MG Oral Tablet"
                }
              ],
              "text": "Lisinopril 20 MG Oral Tablet"
            },
            "dosageInstruction": [
              {
                "text": "1 daily",
                "timing": {
                  "repeat": {
                    "frequency": 1,
                    "period": 1,
                    "periodUnits": "d"
                  }
                }
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

## Coverage

See [https://www.hl7.org/fhir/DSTU2/Coverage.html](https://www.hl7.org/fhir/DSTU2/Coverage.html).

These are the minimum required fields, not covered by either US Core or Argonaut profiles:

1. Payor

Resource search using GET method and the following parameters:

1. patient=\<patient id>

For an example of the call, see the following example:

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
