## Description : 
> File upload in Facade

## 1. Upload Multiple files : 
> POST  : {baseUrl}/upload/file 

#### Request body : 
- files to be send in form-data : 
```
"files"  : [ file1.pdf, file2.jpeg ] 
``` 
![image](https://github.com/LatticeInnovations/LatticeOnFhirMain/assets/51260196/796032aa-e310-4390-9e84-4dd3ff26b981)

#### Response body :
> Example without error :  
```
{
    "status": 1,
    "message": "files uploaded",
    "data": {
        "files": [
            {
                "originalName": "Screenshot from 2024-06-03 12-09-57.png",
                "filename": "Screenshot from 2024-06-03 12-09-57.png",
                "url": "uploads/Screenshot from 2024-06-03 12-09-57.png"
            },
            {
                "originalName": "Screenshot from 2024-06-03 11-50-03.png",
                "filename": "Screenshot from 2024-06-03 11-50-03.png",
                "url": "uploads/Screenshot from 2024-06-03 11-50-03.png"
            }
        ],
        "errors": []
    }
}
```

> - Example with Error : 
```
{
    "status": 1,
    "message": "files uploaded",
    "data": {
        "files": [
            {
                "originalName": "Screenshot from 2024-06-03 12-09-57.png",
                "filename": "Screenshot from 2024-06-03 12-09-57.png",
                "url": "uploads/Screenshot from 2024-06-03 12-09-57.png"
            }
        ],
        "errors": [
            {
                "filename": "config.js",
                "originalname": "config.js",
                "error": "Invalid file type"
            }
        ]
    }
}
```

## 2. Download ZIP for Multiple files : 
> POST  : {baseUrl}/upload/files

#### Request body : 
```
{
    "files" : ["pic.jpg", "pic2.pdf", "hello.png"]
}
```

#### Response Body : 
- ZIP file will be in response


## 2. Download Single file : 
> GET  : {baseUrl}/upload/file?name=filename.pdf

#### Requests Parameter:
- Need to pass query parameter name = `filename` to download the file

#### Response Body : 
- file will be in response




## 3. Create Prescription (Medication Request)
> POST : {{baseURl}}/sync/MedicationRequest


#### Request body example : 
```

    [
        {
        "appointmentId": "33678",
        "patientId": "33240",
        "generatedOn": "2023-08-04T16:25:45+05:30",
        "prescriptionId": "6a95a6ae-8f21-4e21-9b12-772140b8da44",
        "prescription": [
            {
                "filename"  : "342343242.jpeg",
                "note": "this is note 1"
            },
            {
                "filename"  : "342343242.jpeg",
                "note": "" //send empty string in request body when no note
            }
        ]
    }
]
```

#### Response body example : 
```
{
    "status": 1,
    "message": "Data saved successfully.",
    "data": [
        {
            "status": "200 OK",
            "id": null,
            "err": null,
            "fhirId": "33679"
        }
    ]
}
```


## 4. GET Prescription (Medication Request)
> GET : {{baseURL}}/MedicationRequest

#### Query Params : 
- Filter by patients : subject={patientID}
    - example :  {{baseURL}}/MedicationRequest?subject=333333

#### Response Body : 
```
{
    "status": 1,
    "message": "Data fetched",
    "total": 2,
    "data": [
        {
            "appointmentUuid": "0434a5fe-8f48-4b1e-b95e-5c711c8b2f86",
            "prescriptionId": "7f0dedaa-7d0a-44ca-9307-6529fd754bd7",
            "prescriptionFhirId": "33679",
            "appointmentId": "33678",
            "patientId": "33240",
            "generatedOn": "2023-08-04T16:25:45+05:30",
            "prescription": [
                {
                    "filename": "324324324.jpeg",
                    "note": "This is note 1"
                },
                {
                    "filename": "346287364.jpeg",
                    "note": "" // empty string when note is not available
                }
            ]
        },
        {
            "appointmentUuid": "72177dbc-ef56-4a63-854c-34c80fdde462",
            "prescriptionId": "00f5a231-a953-4bba-b42f-d4ef14111f08",
            "prescriptionFhirId": "33709",
            "appointmentId": "33708",
            "patientId": "33240",
            "generatedOn": "2024-06-03T10:50:14+05:30",
            "prescription": []
        }
    ]
}
```

## 5. Update / Delete Prescription - Images / notes (Medication Request)
> PATCH : {{baseURl}}/sync/MedicationRequest

#### Request body example : 
```

    [
        {
        "appointmentId": "33678",
        "patientId": "33240",
        "generatedOn": "2023-08-04T16:25:45+05:30",
        "prescriptionId": "6a95a6ae-8f21-4e21-9b12-772140b8da44",
        "prescription": [
            {
                "filename"  : "342343242.jpeg", //new file name
                "note": "this is note 1" // new note
            },
            {
                "filename"  : "342343242.jpeg",
                "note": "" //send empty string in request body when no note
            }
        ]
    },
    {
        "appointmentId": "33678",
        "patientId": "33240",
        "generatedOn": "2023-08-04T16:25:45+05:30",
        "prescriptionId": "6a95a6ae-8f21-4e21-9b12-772140b8da44",
        "prescription": [] // send empty array if no images and notes
    }
]
```

#### Response body example : 
```
{
    "status": 1,
    "message": "Data updated successfully.",
    "data": [
        {
            "status": "200 OK",
            "id": null,
            "err": null,
            "fhirId": "34006"
        }
    ]
}
```

