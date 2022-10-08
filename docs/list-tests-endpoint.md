# List assessments

The ```
GET https://app.codescreen.com/api/listassessments
``` endpoint will retrieve the list of assessments that you have created on CodeScreen.


### Request

```
curl -X GET https://app.codescreen.com/api/listassessments -H 'Authorization: apiKey c5793bc0-4176-4dec-b59c-ff47337f01c4' 

```
<br/>For example, if you have the following assessments on CodeScreen:

![assessments Table](assessments.png)

### Response

If the request has succeeded, the response will be a `200 OK` containing JSON with the following properties:

```
[
    {
        "assessmentId": "af401f8e-24d9-4889-ad8b-39cc8366b0ac",
        "assessmentName": "Senior Java Developer assessment"
    },
    {
        "assessmentId": "8bc9bb2e-112b-42d6-86d5-c3bfecf7e994",
        "assessmentName": "Python Developer assessment"
    }
]

```