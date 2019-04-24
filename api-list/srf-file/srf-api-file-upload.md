# Service Request Form API - File Upload

### Method 1

LOS System users can upload files via a time delayed process where the details and security for the files are uploaded with the Service Request in the SRF API. 

By providing a new data envelop called "**files**", the LOS API will parse and queue the file(s) to be uploaded. 

| Data Object Name | Type | Description |
| :--- | :--- | :--- |
| fileName | String | Name of File |
| fileType | Type | Mime Type of file |
| - pdf | Adobe Portable Document Format (PDF) | application/pdf |
| - ppt | Microsoft PowerPoint | application/vnd.ms-powerpoint |
| - docx | Microsoft Word (OpenXML) | application/vnd.openxmlformats-officedocument.wordprocessingml.document |
| - other formats |  | [List](srf-api-file-upload-type-list.md) of other formats |
| fileURI | String | File location |
| token | String | Security Token for File Retrieval: null or token |

LOS System users can implement a layer of security by providing an access token with each file. Access tokens can be unique to each file, or an access token for a whole service request. 

If LOS System user opts to not provide a security access token, no token will be used. Simply return a null for "**token**" or do not provide a token object. 


```json
{
  "meta": {
    "cabinet": "Example Cabinet Name",
    "currency": "USD",
    "requestedBy": "creator@example.com"
  },
  "data": {
    "transaction": {
      "exampleTransactionField": "Example Value"
    },
    "collaterals": [
      {
        "exampleCollateralField": "Example Value",
        "services": [
            {
                "siteType": "Appraisal"
            },
            {
                "siteType": "Environmental"
            }
        ],
        "files": [
            {
                "fileName": "{name of file}",
                "fileType": "{mime type of file uploaded}",
                "token": "{access token for file retrieval}",
                "fileURI": "https://somedomain.com/file/somefilename"
            },
            {
                "fileName": "{name of file}",
                "fileType": "{mime type of file uploaded}",
                "token": "{access token for file retrieval}",
                "fileURI": "https://somedomain.com/file/somefilename"
            },
            ...
        ]
      },
      ...
    ]
  }
}
```

### Method 2

LOS System users can upload files by using the File Upload API. After submitting a Service Request and getting the serviceRequestID, a user can submit files for that specific Service Request, by referencing the serviceRequestID. 

