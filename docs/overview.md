# Overview

## Authentication

Basic Authentication is used to authneticate users.

Username can be either the username or email address registered for the ML Accessories website account.

## Error Codes & Responses

When an error occurs JSON will be returned with a message and the HTTP code will indicate the type of error.

```JSON
{
    "message": "Invalid Username/Password"
}
```

HTTP Code | Description           | Reason
----------|-----------------------|--------
400       | Bad Request           | Invalid request path, invalid JSON, or invalid JSON structure.
401       | Unauthorized          | Username and password details were not provided or were not valid.
404       | Not Found             | Resource wasn't found or is for a different user.
409       | Conflict              | Conflict with performing an operation on a resource or between the resource stored and the one provided e.g. trying to place an order for delivery that is missing required information or trying to update an order that is not open.
422       | Unproccessable Entity | Invalid field data in the request e.g. a field missing or is null but is required.
500       | Internal Server Error | Something unexpected happend on the server. A report will be generated and sent to engineers for analysis.