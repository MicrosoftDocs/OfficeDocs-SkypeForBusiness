---
title: Patients App and EHR integration STU3 interface
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
description: Learn about integrating Electronic Health Records into the Microsoft Teams Patients app and the STU3 interface specification.
ms.custom: seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
---

# STU3 interface specification

> [!NOTE]
> Effective October 30, 2020, the Patients app has been retired and replaced by the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db) in Teams. Patients app data is stored in the group mailbox of the Office 365 group that backs the team. All data associated with the Patients app is retained in this group but can no longer be accessed through the user interface. Users can re-create their lists using the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db).
>
>With Lists, care teams in your healthcare organization can create patient lists for scenarios ranging from rounds and interdisciplinary team meetings to general patient monitoring. Check out the Patients template in Lists to get started. To learn more about how to manage the Lists app in your organization, see [Manage the Lists app](../../manage-lists-app.md).

Setting up or reconfiguring an FHIR server to work with the Microsoft Teams Patients app requires understanding what data the app needs to access. The FHIR server must support POST requests using bundles for the following resources:

- [Patient](#patient)
- [Observation](#observation)
- [Condition](#condition)
- [Encounter](#encounter)
- [Allergy Intolerance](#allergyintolerance)
- [Coverage](#coverage)
- [Medication Statement](#medication-request) (replaces the MedicationOrder in the DSTU2 version of the PatientsApp)
- Location (the information needed from this resource can be included in Encounter)

> [!NOTE]
> The Patient resource is the only mandatory resource (without which the app will not load at all); However, it is recommended that the Partner implement support for all the above mentioned resources per specifications provided below for the best end-user experience with the Microsoft Teams Patients App.

Queries from the Microsoft Teams Patients app for more than one resource shall post a bundle (BATCH) of requests to the FHIR server's URL. The server shall process each request and return a bundle of the resources matched by each request. For more information and examples, see [https://www.hl7.org/fhir/STU3/http.html#transaction](https://www.hl7.org/fhir/STU3/http.html#transaction).

## Capability Statement

These are the minimum required fields:

 - REST

    - Mode
    - Interaction
    - Resource: Type
    - Security: [Extension for OAuth URIs](https://hl7.org/fhir/extension-oauth-uris.html)
    
 - FhirVersion (Our code requires this to understand which version we should pivot to.)

See [https://www.hl7.org/fhir/stu3/capabilitystatement.html](https://www.hl7.org/fhir/stu3/capabilitystatement.html) for other details on this field set.

## Patient

Here are the minimum required fields, which are a subset of the Argonaut patient profile fields:

 - Name.Given
 - Name.Family
 - Gender
 - BirthDate
 - MRN (Identifier)

In addition to the [Argonaut fields](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-patient.html), for a great user experience the Patients app can also read the following fields:

 - Name.Use
 - Name.Prefix
 - [GeneralPractitioner] - The GeneralPractitioner reference should be included in the Patient resource (display field only)

A resource search uses the POST method at /Patient/_search and the following parameters:

 - id
 - family=(searches for all patients whose family name contains the value)
 - given=\<substring>
 - birthdate=(exact match)
 - gender=(values being one of the administrative-gender)
 - \_count (maximum number of results that should be returned) <br> The response should contain the total count of records returned as a result of the search and \_count will be used by the PatientsApp to limit the number of records returned.
 - identifier=\<mrn>

The goal is to be able to search and filter for a patient by the following:

- ID: This is the resource ID that every resource in FHIR has.
- MRN: This is the actual identifier for the patient that clinical staff would know. We understand this MRN is based on the type of identifier inside the identifier resource in FHIR.
- Name
- Birthdate

See the following example of the call:

```
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
				  "system": "https://hl7.org/fhir/v2/0203",
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
```

```
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
			"system": "https://hl7.org/fhir/v2/0203",
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
```

See [https://hl7.org/fhir/stu3/patient.html](https://hl7.org/fhir/stu3/patient.html) for other details on this field set.

## Observation

These are the minimum required fields, which are a subset of the [Argonaut Vital-Signs profile](https://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-vitalsigns.html).

 - Effective (date time or period)
 - Code.Coding.Code
 - ValueQuantity.Value

In addition to the Argonaut fields, for a great user experience the Patients app can also read the following fields:

 - Code.Coding.Display
 - ValueQuantity.Unit

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _sort=-date
 - category (we will query for "category=vital-signs") to retrieve the list of vital signs.

Refer to this example of the call:

```
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
				"system": "https://hl7.org/fhir/observation-category",
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
```

See [https://www.hl7.org/fhir/stu3/observation.html](https://www.hl7.org/fhir/stu3/observation.html) for other details on this field set.

## Condition

Here's the minimum required fields, which are a subset of the [Argonaut condition profile](http://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-condition.html).

 - Code.Coding[0].Display

In addition to the Argonaut fields, for a great user experience the Patients app can also read the following fields:

 - AssertedDate
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
```

See [https://hl7.org/fhir/stu3/condition.html](https://hl7.org/fhir/stu3/condition.html) for other details on this field set.

## Encounter

These are the minimum required fields, which are a subset of the [US Core Encounter profile](https://hl7.org/fhir/us/core/2018Jan/StructureDefinition-us-core-encounter.html) "must have" fields).

 - Status
 - Type[0].Coding[0].Display

In addition, the following fields from US Core Encounter profile's "must support" fields:

 - Period.Start
 - Location[0].Location.Display

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _sort:desc=\<field ex. date>
 - _count=\<max results>

The goal is to be able to retrieve the patient's last known location. Each encounter references a location resource. The reference shall also include the location's display field.

See [https://hl7.org/fhir/stu3/encounter.html](https://hl7.org/fhir/stu3/encounter.html) for other details on this field set.

## AllergyIntolerance

These are the minimum required fields, which are a subset of the [Argonaut AllergyIntolerance](https://www.fhir.org/guides/argonaut/r2/StructureDefinition-argo-allergyintolerance.html) profile:

 - Code.Text
 - Code.Coding[0].Display
 - ClinicalStatus/VerificationStatus (we read both)

In addition to the Argonaut fields, for a great user experience the Patients app can also read the following field:

 - AssertedDate
 - Note.Text
 - Reaction
    - Substance (one coding element)
    - Manifestation (one coding element)

A resource search uses the GET method and the following parameters:

 - Patient =  \<patient id>

See the following example of the call: 

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
```

See [https://hl7.org/fhir/stu3/allergyintolerance.html](https://hl7.org/fhir/stu3/allergyintolerance.html) for other details on this field set.

## Medication Request

These are the minimum required fields, which are a subset of the [US Core Medication Request profile](http://www.hl7.org/fhir/us/core/StructureDefinition-us-core-medicationrequest.html):

 - Medication.Display (if Reference)
 - Medication.Text (if CodableConcept)
 - AuthoredOn
 - Requester.Agent.Display

In addition to the US Core fields, for a great user experience the Patients app can also read the following fields:

 - DosageInstruction[..].Text
 - Text

A resource search uses the GET method and the following parameters:

 - patient=\<patient id>
 - _count=\<max results>

See [https://www.hl7.org/fhir/medicationrequest.html](https://www.hl7.org/fhir/medicationrequest.html) for other details on this field set.

## Coverage

These are the minimum required fields, not covered by either US Core or Argonaut profiles:

 - Grouping, at least one element with
    - GroupDisplay
    - PlanDisplay
 - Period
 - SubscriberId

A resource search uses the GET method and the following parameters:

 - Patient = \<patient id>

See [https://hl7.org/fhir/stu3/coverage.html](https://www.hl7.org/fhir/medicationrequest.html) for other details on this field set.
