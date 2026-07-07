---
order: 1050
---

# Patient

## 1. Save patient data

* **id**: datatype - string, description uuid will be required if a resource is created using the bundle, 
* **firstName**: datatype - string containing name first name of the person,
* **middleName**: datatype - string containing name middle name of the person,
* **lastName**: datatype - string containing name last name of the person,
* **identifier**: 
    * **identifierType**: datatype - string, description - url of the identifier that contains a link to refer to unique indetifiecation of the id type,
    * **identifierNumber**: datatype - string, description - id number  ,
    * **code**: code of the identification category from list (http://hl7.org/fhir/R4B/valueset-identifier-type.html)
* **gender**: datatype - string, description -  gender of the person (male|female|other|unknown)
* **active**: datatype - boolean, description - if the user is active (true|false),
* **birthDate**: datatype - date, description - date of birth in yyyy-mm-dd format,
* **permanentAddress**: contains permanent address 
    * **addressLine1**: datatype - string, description - house no, buliding no, society name etc,
    * **addressLine2**: datatype - string, description - locality, area or street number details,
    * **district**: datatype - string, description - district name,
    * **city**: datatype - string, description - city name,
    * **state**: datatype - string, description - state name,
    * **postalCode**: datatype - integer, description - pin code of 6 digits,
    * **country**: datatype - string, description - country name
* **tempAddress**: contains temporary address 
    * **addressLine1**: datatype - string, description -  house no, buliding no, society name etc,
    * **addressLine2**: datatype - string, description - locality, area or street number details,
    * **district**: datatype - string, description - district name,
    * **city**: datatype - string, description - city name,
    * **state**: datatype - string, description - state name,
    * **postalCode**: datatype - integer, description - pin code of 6 digits,
    * **country**: datatype - string, description - country name
* **email**: datatype - string, description - email address of person,
* **mobileNumber**: datatype - integer, description -  mobile number of person

If the user does not want to provide any detail for a particular field, he/she can send it as null.

> POST: /sync/Patient

```json Request body
[
    {
        "id": "b79266ec-bcb6-11ed-9ef5-325096b39f47",
        "resourceType": "Patient",
        "firstName": "Sudhanshu",
        "lastName": "Sharma",
        "identifier": [
            {
                "identifierType": "http://hospital.smarthealthit.org",
                "identifierNumber": "afac0bae-bcb6-11ed-bd14-325096b39f47",
                "code": "MR"
            },
            {
                "identifierType": "https://www.pan.utiitsl.com",
                "identifierNumber": "GAFDI4894F"
            }
        ],
        "gender": "male",
        "active": true,
        "birthDate": "1993-10-11",
        "permanentAddress": {
            "addressLine1": "C 13, near c complex",
            "addressLine2": "Shankar Vihar",
            "district": "South West Delhi",
            "city": "New Delhi",
            "state": "Delhi",
            "postalCode": "110010",
            "country": "India"
        },
        "tempAddress": {
            "addressLine1": "C 22, near c complex",
            "district": "South West Delhi",
            "city": "New Delhi",
            "state": "Delhi",
            "postalCode": "110020",
            "country": "India"
        },
        "email": "sudhanshu12@yahoo.co.in",
        "mobileNumber": "9887584498"
    }
]
```

```json Response
{
  "status": 1,
  "message": "Data saved successfully.",
  "data": [
    {
      "status": "200 OK",
      "fhirId": "116",
      "id": "urn:uuid:urn:uuid:b79266ec-bcb6-11ed-9ef5-325096b39f47",
      "err": null
    }
  ]
}
```

## 2. Get patient list
Get the list of all the patients created.

> GET: /Patient?_sort=-_id

* Query params
    * `_sort`: to sort according to id. ex -_id
    * `_offset`, `_count` parameters can be used for syncing the data using pagination

```json Response
{
  "status": 1,
  "message": "details fetched successfully",
  "total": 1,
  "data": [
    {
      "fhirId": "1",
      "firstName": "Prateek",
      "lastName": "Sharma",
      "identifier": [
        {
          "identifierType": "http://hospital.smarthealthit.org",
          "identifierNumber": "274cc178-133a-4393-95e6-cad2ca6574cc",
          "code": "MR"
        }
      ],
      "id": "274cc178-133a-4393-95e6-cad2ca6574cc",
      "active": true,
      "gender": "male",
      "birthDate": "1984-11-21",
      "mobileNumber": "9955556473",
      "email": "prateek@yahoo.co.in",
      "permanentAddress": {
        "city": "PleasantVille",
        "district": "Rainbow",
        "state": "Vic",
        "postalCode": "3999",
        "addressLine1": "534 Erewhon St"
      },
      "tempAddress": {
        "city": "PleasantVille",
        "district": "Rainbow",
        "state": "Vic",
        "postalCode": "3999",
        "addressLine1": "534 Erewhon St"
      }
    }
  ]
}
```

### Get patient by id
Get the details of a patient by adding search parameter `id`.

> GET: /Patient?_id=2214

* Query params
    * `_id`: id of the patient that needs to be fetched.

```json Response
{
  "status": 1,
  "message": "details fetched successfully",
  "total": 1,
  "data": [
    {
      "fhirId": "2214",
      "firstName": "Prajakta",
      "lastName": "V",
      "identifier": [
        {
          "identifierType": "https://www.thelattice.in/",
          "identifierNumber": "2c710171-df3b-4912-a4e1-5d021483d99d",
          "code": "MR"
        },
        {
          "identifierType": "https://www.passportindia.gov.in",
          "identifierNumber": "222222222222",
          "code": null
        }
      ],
      "id": "2c710171-df3b-4912-a4e1-5d021483d99d",
      "active": true,
      "gender": "female",
      "birthDate": "1977-11-28",
      "mobileNumber": "9999872345",
      "email": "prajaktav@gmail.com",
      "permanentAddress": {
        "city": "New Delhi",
        "district": "South West Delhi",
        "state": "Delhi",
        "postalCode": "110010",
        "country": "India",
        "addressLine1": "P 111-D4, near c complex",
        "addressLine2": "Shankar Vihar"
      },
      "tempAddress": {
        "city": "New Delhi",
        "district": "South West Delhi",
        "state": "Delhi",
        "postalCode": "110020",
        "country": "India",
        "addressLine1": "P 111-D4, near c complex"
      }
    }
  ]
}
```

## 3. Patch patient data
**Operations**: 
1. **add** - performed to add a detail which is not already present in the resource
2. **remove** - removes any field or detail from the resource
3. **replace** - replace any existing data in the field

There can be only 3 types of values in the value field : 
* A variable (string or integer, boolean or decimal, char etc)
* An object such as permanent address
* An array


If any field in patch api is to be removed such as district in parmanentAddress then it should be provided as null, not as an empty string. For example

```
"permanentAddress": {
    "operation": "replace",
    "value": {
        "addressLine1": "C-416",
        "addressLine2": "Sarita Vihar",
        "city": "South Delhi",
        "country": "India",
        "district": null,
        "postalCode": "989898",
        "state": "Andhra Pradesh"
    }
}
```

> PATCH: /sync/Patient

```json Request body
[
    {
        "resourceType": "Patient",
        "id": 108,
        "firstName": {
            "operation": "replace",
            "value": "Arpita"
        },
        "lastName": {
            "operation": "replace",
            "value": "Ghosh"
        },
        "middleName": {
            "operation": "replace",
            "value": "Sen"
        },
        "gender": {
            "operation": "replace",
            "value": "female"
        },
        "active": {
            "operation": "replace",
            "value": true
        },
        "birthDate": {
            "operation": "replace",
            "value": "1996-05-12"
        },
        "permanentAddress": {
            "operation": "replace",
            "value": {
                "addressLine1": "C 64, near c complex",
                "addressLine2": "Shankar Vihar",
                "district": "South West Delhi",
                "city": "New Delhi",
                "state": "Delhi",
                "postalCode": "110020",
                "country": "India"
            }
        },
        "email": {
            "operation": "replace",
            "value": "arpita@gmail.com"
        },
        "mobileNumber": {
            "operation": "replace",
            "value": "9985643276"
        }
    }
]
```

```json Response
{
  "status": 1,
  "message": "Data updated successfully.",
  "data": [
    {
      "status": "200 OK",
      "fhirId": "108",
      "id": null,
      "err": null
    }
  ]
}
```