---
title: Patients App and EHR integration DSTU2 interface
author: dstrome
ms.author: dstrome
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
search.appverid: MET150
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Healthcare
appliesto: 
  - Microsoft Teams
ms.reviewer: anach
description: Learn about the DSTU2 interface specification in Teams, including setting up or reconfiguring an FHIR server to work with the Microsoft Teams Patients app.
ms.custom: seo-marvel-mar2020
ROBOTS: NOINDEX, NOFOLLOW
---

# DSTU2 interface specification

> [!NOTE]
> Effective October 30, 2020, the Patients app has been retired and replaced by the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db) in Teams. Patients app data is stored in the group mailbox of the Office 365 group that backs the team. All data associated with the Patients app is retained in this group but can no longer be accessed through the user interface. Users can re-create their lists using the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db).
>
>With Lists, care teams in your healthcare organization can create patient lists for scenarios ranging from rounds and interdisciplinary team meetings to general patient monitoring. Check out the Patients template in Lists to get started. To learn more about how to manage the Lists app in your organization, see [Manage the Lists app](../../manage-lists-app.md).

Setting up or reconfiguring an FHIR server to work with the Microsoft Teams Patients app requires understanding what data the app needs to access. The FHIR server must support POST requests using bundles for the following resources:

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

Queries from the Microsoft Teams Patients app for more than one resource post a bundle (BATCH) of requests to the FHIR server's URL. The server processes each request and returns a bundle of the resources matched by each request. For more information and examples, see [https://www.hl7.org/fhir/DSTU2/http.html#transaction](https://www.hl7.org/fhir/DSTU2/http.html#transaction).

All the following FHIR resources should be accessible by direct resource reference.

## Conformance minimum required field set

 The FHIR Server must implement the conformance statement for us to have a factual summary of its capabilities. We expect the below parameters in a DSTU2 FHIR Server:

 - REST

    - Mode
    - Interaction
    - Resource: Type
    - Security: [Extension for OAuth URIs](https://hl7.org/fhir/extension-oauth-uris.html)
   
 - FhirVersion (Our code requires this to understand which version we should pivot to as we support multiple versions.)

See [https://www.hl7.org/fhir/dstu2/conformance.html](https://www.hl7.org/fhir/dstu2/conformance.html) for other details on this field set.

## Patient

These are the minimum required fields, which are a subset of the [Argonaut patient profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-patient.html) fields:

 - Name.Family
 - Name.Given
 - Gender
 - BirthDate
 - MRN (Identifier)

In addition to the Argonaut fields, for a great user experience the Patients app also reads the following fields:

 - Name.Use
 - Name.Prefix
 - CareProvider (This reference on the Patient resource should include the display fields shown in the following example.)

    ```
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
                "system": "https://hl7.org/fhir/v2/0203",
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
    ```

A resource search uses the POST method at /Patient/_search and the following parameters:

 - id
 - family:contains=(searches for all patients whose family name contains the value.)
 - given=\<substring>
 - name=\<substring>
 - birthdate=(exact match)
 - \_count (maximum number of results that should be returned) <br> The response should contain the total count of records returned as a result of the search, and \_count will be used by the PatientsApp to limit the number of records returned.
 - identifier=\<mrn>

The goal is to be able to search and filter for a patient by the following:

- ID: This is the resource ID that every resource in FHIR has.
- MRN: This is the actual identifier for the patient that clinical staff would know. We understand this MRN is based on the type of identifier inside the identifier resource in FHIR
- Name
- Birthdate

See the following example  of this call.

```
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
```

See [https://www.hl7.org/fhir/DSTU2/Patient.html](https://www.hl7.org/fhir/DSTU2/Patient.html) for other details on this field set.

## Observation

These are the minimum required fields, which are a subset of the Argonaut vital signs profile:

 - Effective (date time or period)
 - Code.Coding.Code
 - ValueQuantity.Value

In addition to the Argonaut fields, for a great user experience the Patients app also reads the following fields:

 - Code.Coding.Display
 - ValueQuantity.Unit

If using component observations, the same logic applies for each component observation.

A resource search uses the GET method and the following parameters:

 - patient=\<patient id\>
 - sort:desc=\<field ex. date\>

The goal is to be able to retrieve the latest vital signs for a patient, [VitalSigns.DSTU.saz]  (observation?).

```
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
```

See [https://www.hl7.org/fhir/DSTU2/Observation.html](https://www.hl7.org/fhir/DSTU2/Observation.html) for other details on this field set.

## Condition

These are the minimum required fields, which are a subset of the [Argonaut condition profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-condition.html):

1. Code.Coding[0].Display

In addition to the Argonaut fields, for a great user experience the Patients app can also read the following fields:

 - Date Recorded
 - Severity

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _count=\<max results>

See the following example of this call:

```
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
```

See [https://www.hl7.org/fhir/DSTU2/Condition.html](https://www.hl7.org/fhir/DSTU2/Condition.html) for other details on this field set.

## Encounter

These are the minimum required fields, which are a subset of the US Core Encounter profile "must have" fields:

 - Status
 - Type[0].Coding[0].Display

In addition, the following fields from US Core Encounter profile's "must support" fields

 - Period.Start
 - Location[0].Location.Display

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _sort:desc=\<field ex. date>
 - _count=\<max results>

The goal is to be able to retrieve the patient's last known location. Each encounter references a location resource. The reference shall also include the location's display field. See the following example of this call.

```
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
```

See [https://www.hl7.org/fhir/DSTU2/Encounter.htm](https://www.hl7.org/fhir/DSTU2/Encounter.htm) for other details on this field set.

## AllergyIntolerance

These are the minimum required fields, which are a subset of the Argonaut AllergyIntolerance profile:

 - Code.Text
 - Code.Coding[0].Display
 - Status

In addition to the Argonaut fields, for a great user experience the Patients app also reads the following fields:

 - RecordedDate
 - Note.Text
 - Reaction[..].Substance.Text
 - Reaction[..].Manifestation[..].Text
 - Text.Div

A resource search uses the GET method and the following parameters:

 - Patient =  \<patient id>

See the following example of this call:

```
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
```

See [https://www.hl7.org/fhir/DSTU2/AllergyIntolerance.html](https://www.hl7.org/fhir/DSTU2/AllergyIntolerance.html) for other details on this field set.

## Medication Order

These are the minimum required fields, which are a subset of the Argonaut MedicationOrder profile:

 - DateWritten
 - Prescriber.Display
 - Medication.Display (if reference)
 - Medication.Text (if concept)

In addition to the Argonaut fields, for a great user experience the Patients app can also read the following fields:

 - DateEnded
 - DosageInstruction.Text
 - Text.Div

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _count=\<max results>

See the following example of this call:

```
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
```

See [https://www.hl7.org/fhir/DSTU2/MedicationOrder.html](https://www.hl7.org/fhir/DSTU2/MedicationOrder.html) for other details on this field set.

## Coverage

These are the minimum required fields, not covered by either US Core or Argonaut profiles:

 - Payor

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>

See the following example of this call:

```
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
```
    
See [https://www.hl7.org/fhir/DSTU2/Coverage.html](https://www.hl7.org/fhir/DSTU2/Coverage.html) for other details on this field set.

## Location

This resource is only being used as a reference on the [Encounter](#encounter) resource.

See [https://www.hl7.org/fhir/DSTU2/Location.html](https://www.hl7.org/fhir/DSTU2/Location.html) for other details on this field set.
