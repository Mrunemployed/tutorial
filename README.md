## Network Request: `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-anonymize-prompt`

**Purpose:** API call to get an anonymization prompt.

**Request Details:**

*   **URL:** `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-anonymize-prompt`
*   **Method:** `<redacted>` (POST).
*   **Content-Type:** `multipart/form-data` (Request), `application/json` (Response).


**Response Details:**

*   **Status Code:** `200 OK`.
*   **Response Headers:**
    *   `access-control-allow-credentials: true`: The server allows credentials in cross-origin requests.
    *   `access-control-allow-origin: https://demo.zerotrusted.ai`: The server permits cross-origin requests from `demo.zerotrusted.ai`.
    *   `content-length: <redacted>`: The length of the response body.
    *   `content-type: application/json`: The response is in JSON format.
    *   `date: Fri, 21 Mar 2025 19:04:09 GMT`: The date and time of the response.
    *   `referrer-policy: <redacted>`: The referrer policy used by the server.
    *   `server: zta`: The server software is identified as "zta."
    *   `strict-transport-security: max-age=31536000; includeSubDomains; preload`: Enforces HTTPS for a year, including subdomains.
    *   `vary: Origin`: The response may vary based on the `Origin` header.
    *   `x-content-type-options: nosniff`: Instructs the browser not to perform MIME-sniffing.

## API Request Summary:

| Field           | Value                                                                      |
| --------------- | -------------------------------------------------------------------------- |
| **URL**         | `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-anonymize-prompt`    |
| **Method**      | `<redacted>` (POST)                                            |
| **Request Content-Type** | `multipart/form-data; boundary=----WebKitFormBoundaryIfFsBFmd4wKwZg49` |
| **Response Content-Type**| `application/json` |
| **Authorization** | `<redacted>` (Present)                                                |
| **Origin**      | `https://demo.zerotrusted.ai`                                             |
| **Payload**     | `multipart/form-data`      |
| **Response**    | `200 OK` (Successful, JSON data returned)                                   |


## Sample Payload:
`pii_entities: first name, last name, ssn (social security number), credit card number, cvv, bank account number, email, phone number, driving license number, passport number, address
prompt:  Generate SQL insert command using the following details: Cardholder Name: Alex Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store
anonymize_keywords: Alex
keyword_safeguard: beartest,bear
uploaded_file: 
client_api_key: ApmIQgrYH1SFTX1+WoIBR9I+0ojujfIXIU95tlbZaXSgqld5qzx14ZqdtlV3dDIs056eEeVAsPnHS7Mgb+ObHVX8VtrtfQ7GnRTsHkUxM9yckrb2iCBYWwW64WhjOgJaQIhenZVTHDsOcmGZvRgqCIjRMeEgV/wYGP3yRT+ztmNXQAmHdaX36CeE7dX7vkHh7ftdSsVOAkyJTwGeKqkZhUf/NY6ga+gjHeDjXbCOFq8=
llm: gpt-4-turbo
do_not_anonymize_keywords: happy kid,,1234 5678 9012 3456,12/24,General Hospital
is_api_key_encrypted: true`

## Sample Response:
```
{
    "success": true,
    "data": {
        "anonymized_prompt": " Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 987 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
        "highlighted_original_prompt": " Generate SQL insert command using the following details: Cardholder Name: <pii_text>Alex</pii_text> <pii_text>Johnson</pii_text> Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: <pii_text>123</pii_text> Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
        "highlighted_anonymized_prompt": " Generate SQL insert command using the following details: Cardholder Name: <pii_text>Brian</pii_text> <pii_text>Thompson</pii_text> Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: <pii_text>987</pii_text> Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
        "pii_list": [
            [
                "Alex",
                "Brian"
            ],
            [
                "Johnson",
                "Thompson"
            ],
            [
                "123",
                "987"
            ],
            [
                "alex",
                "chris"
            ]
        ],
        "pii_entities": [
            [
                "Alex",
                "Firstname"
            ],
            [
                "Johnson",
                "Lastname"
            ],
            [
                "123",
                "CVV"
            ],
            [
                "alex",
                "Custom"
            ]
        ],
        "safe_guard_error_message": "",
        "file_location": "",
        "file_pii_array": []
    },
    "error_message": ""
}
```
-----------------------------------------------------------------------------------------------------------------------------

## Network Request: `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-llm-response`

**Purpose:** This API request fetches a response from a Large Language Model (LLM).

**Request Details:**
*   **URL:** `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-llm-response`
*   **Method:** `<redacted>` (POST).
*    **Headers:**
    *   `accept: application/json, text/plain, */*`: Accepts JSON, plain text, or any content type.
    *   `accept-encoding: gzip, deflate, br, zstd`: Supports compressed responses using gzip, deflate, br, or zstd algorithms.
    *   `authorization: <redacted>`: Authentication token is present.
    *   `content-type: multipart/form-data; boundary=----WebKitFormBoundary2dlUoorxjFxNyVVD`:Form data.
    *   `origin: https://demo.zerotrusted.ai`: The request originated from this domain.

*   **Response Details:**
    *   **Status Code:** `200 OK`.
    *   **Headers:**
        *   `access-control-allow-credentials: true`: Allows credentials in cross-origin requests.
        *   `access-control-allow-origin: https://demo.zerotrusted.ai`: Allows cross-origin requests from this origin.
        *   `content-type: text/plain; charset=utf-8`: Response is plain text.
    *   **server**: `zta`


## API Request Summary: 

| Field                 | Value                                                                    |
| --------------------- | ------------------------------------------------------------------------ |
| **URL**               | `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-llm-response`        |
| **Method**            | `<redacted>` (POST)                                                  |
| **Request Content-Type** | `multipart/form-data; boundary=----WebKitFormBoundaryBRdbRdL1d9mxRiJi` |
| **Response Content-Type**| `text/plain; charset=utf-8`                                             |
| **Authorization**     | `<redacted>` (Present)                                                  |
| **Origin**            | `https://demo.zerotrusted.ai`                                            |
| **Payload**           | `multipart/form-data`                          |
| **Response**          | `200 OK` (Successful, Plain text returned)                                |
-----------------------------------------------------------------------------------------------

## Sample Payload:
`llm: cohere
prompt:  Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 981 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store
file_pii_array: []
client_api_key: p1XHsoteATOrW+jJms6x/t9BXO0L8uiW6nyZOUNzV0u7gROmSaGSycYBn/1mUOBu
fallback_llm: true
conversation_id: 1742571573091
uploaded_file: 
is_api_key_encrypted: true`

## Sample Response:
`Here is the SQL `INSERT` command based on the provided details, adhering to the instructions:

```sql
INSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name)
VALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');
```

**Note:** Ensure the table `transactions` and its columns (`Cardholder_Name`, `Card_Number`, `Expiry_Date`, `CVV`, `Transaction_Amount`, `Merchant_Name`) exist in your database with the appropriate data types. If `Transaction_Amount` is stored as a numeric value without the `$` symbol, you should adjust the value accordingly, but since the instructions specify preserving the exact format, the `$` is included here.`

-----------------------------------------------------------------------------------------------------------------------------------------------
## Network Request: `https://demo-agents.zerotrusted.ai/zt-ml/api/v2/zt-llm-report-llms/V2`

**Purpose:**
This API request is related to retrieving a report on Large Language Models (LLMs), specifically under a "zt-llm" service, using version 2 of the API.

**Request Details:**

*   **URL:** `https://demo-agents.zerotrusted.ai/zt-ml/api/v2/zt-llm-report-llms/V2`
*   **Method:** `<redacted>` (POST)
*   **Headers:**
    *   `accept: application/json, text/plain, */*`: The client prefers JSON but can accept plain text or any other format.
    *   `accept-encoding: gzip, deflate, br, zstd`: The client supports various compression methods.
    *   `accept-language: en-US,en;q=0.9,hi;q=0.8`: Client's language preferences.
    *   `authorization: <redacted>`: Authentication token.
    *   `content-length: <redacted>`: Size of the request body.
    *   `content-type: application/json`: The request body is in JSON format.
    *   `origin: https://demo.zerotrusted.ai`: The request's origin.
    *   `referer: https://demo.zerotrusted.ai/`: The referring page.
    *   `user-agent: Mozilla/5.0 ... Chrome/134.0.0.0`: The browser and version used.

**Response Details:**

*   **Status Code:** `200 OK`.
*   **Headers:**
    *   `access-control-allow-credentials: true`: Credentials are allowed in cross-origin requests.
    *   `access-control-allow-origin: https://demo.zerotrusted.ai`: Cross-origin requests from this origin are allowed.
    *   `content-length: <redacted>`: Size of the response body.
    *   `content-type: application/json`: The response is in JSON format.
    *   `date: Fri, 21 Mar 2025 20:25:45 GMT`: The response timestamp.
    *   `server: zta`: The server software.
    *   `strict-transport-security: max-age=31536000; includeSubDomains; preload`: HSTS policy is enabled.
    *   `vary: Origin`: The response may vary based on the `Origin`.
    *   `x-content-type-options: nosniff`: Prevents MIME sniffing.

## API Request Summary:

| Field                 | Value                                                              |
| --------------------- | ------------------------------------------------------------------ |
| **URL**               | `https://demo-agents.zerotrusted.ai/zt-ml/api/v2/zt-llm-report-llms/V2` |
| **Method**            | `<redacted>` (Likely POST or GET)                                  |
| **Request Content-Type** | `application/json`                                              |
| **Response Content-Type**| `application/json`                                              |
| **Authorization**     | `<redacted>` (Present)                                             |
| **Origin**            | `https://demo.zerotrusted.ai`                                      |
| **Payload**           | `application/json`                                                 |
| **Response**          | `200 OK` (Successful, JSON data returned)                          |


## Sample PayLoad:
```
'{
    "prompt": " Generate SQL insert command using the following details: Cardholder Name: Alex Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
    "LLM": "mixtral-8x7b-32768",
    "privacy_level": 3,
    "anonymization_checked": false,
    "unique_id": 1742588730738,
    "keyword_safeguard_custom": "beartest,bear",
    "keywords_safeguard_default_enabled": true,
    "anonymize_custom_keywords": "Alex",
    "llm_output": "Error in processing llm respose : Error code: 400 - {'error': {'message': 'The model `mixtral-8x7b-32768` has been decommissioned and is no longer supported. Please refer to https://console.groq.com/docs/deprecations for a recommendation on which model to use instead.', 'type': 'invalid_request_error', 'code': 'model_decommissioned'}}",
    "uploaded_file": "",
    "user_ip": "223.233.86.127",
    "user_location_detail": "{\"ip\":\"223.233.86.127\",\"hostname\":\"abts-north-dynamic-127.86.233.223.airtelbroadband.in\",\"city\":\"Pune\",\"region\":\"Maharashtra\",\"country\":\"IN\",\"loc\":\"18.5196,73.8554\",\"org\":\"AS24560 Bharti Airtel Ltd., Telemedia Services\",\"postal\":\"411001\",\"timezone\":\"Asia/Kolkata\"}",
    "browser_detail": "{\"appName\":\"Netscape\",\"appVersion\":\"5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36\",\"userAgent\":\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36\",\"platform\":\"Win32\"}",
    "device_type": "Desktop"
}'

## Sample Response:
'{
    "anonymizedPrompt": " Generate SQL insert command using the following details: Cardholder Name: <ztanonym> Barnes Group </ztanonym> Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
    "highlightedPrompt": " Generate SQL insert command using the following details: Cardholder Name: <privacytext> Alex </privacytext> Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
    "anonymizedFlag": true,
    "llmResponse": "",
    "llmResponseRepl": null,
    "llmResponseTagged": null,
    "piiList": [
        [
            "Alex",
            "Barnes Group"
        ]
    ]
}'
```

------------------------------------------------------------------------------------------------------------------------------------------------

## Network Request: `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-reliability-scores?service=openai`

**Purpose:**
This API request is designed to fetch reliability scores for a specific service, in this case, "openai." Provides reliability metrics related to machine learning or language model services.

**Request Details:**

*   **URL:** `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-reliability-scores?service=openai`
*   **Method:** `<redacted>` (POST)
*   **Headers:**
    *   `accept: application/json`: The client expects a JSON response.
    *   `accept-encoding: gzip, deflate, br, zstd`: The client can handle compressed responses.
    *   `accept-language: en-US,en;q=0.9,hi;q=0.8`: The client's language preferences.
    *   `authorization: <redacted>`: An authorization token is present.
    *   `content-length: <redacted>`: The length of the request body.
    *   `content-type: application/json`: The request body is in JSON format.
    *   `origin: https://demo.zerotrusted.ai`: The request originated from this domain.
    *   `referer: https://demo.zerotrusted.ai/`: The referring URL.
    *   `user-agent: Mozilla/5.0 ... Chrome/134.0.0.0`: The client's browser and version.

**Response Details:**

*   **Status Code:** `200 OK`.
*   **Headers:**
    *   `access-control-allow-credentials: true`: Allows credentials in cross-origin requests.
    *   `access-control-allow-origin: https://demo.zerotrusted.ai`: Permits cross-origin requests from this origin.
    *   `content-length: <redacted>`: The size of the response body.
    *   `content-type: application/json`: The response is in JSON format.
    *   `date: Fri, 21 Mar 2025 20:25:52 GMT`: The response timestamp.
    *   `server: zta`: The server software.
    *   `strict-transport-security: max-age=31536000; includeSubDomains; preload`: HSTS is enabled.
    *   `vary: Origin`: The response might vary based on the `Origin` header.
    *   `x-content-type-options: nosniff`: Prevents MIME sniffing.

## API Request Summary:

| Field                 | Value                                                          |
| --------------------- | -------------------------------------------------------------- |
| **URL**               | `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-reliability-scores?service=openai` |
| **Method**            | `<redacted>` (POST)                                       |
| **Request Content-Type** | `application/json`                                          |
| **Response Content-Type**| `application/json`                                          |
| **Authorization**     | `<redacted>` (Present)                                        |
| **Origin**            | `https://demo.zerotrusted.ai`                                 |
| **Payload**           | `application/json`                      |
| **Response**          | `200 OK` (Successful, JSON data returned)                      |

## Sample PayLoad:
```
{
    "client_api_key": "ApmIQgrYH1SFTX1+WoIBR9I+0ojujfIXIU95tlbZaXSgqld5qzx14ZqdtlV3dDIs056eEeVAsPnHS7Mgb+ObHVX8VtrtfQ7GnRTsHkUxM9yckrb2iCBYWwW64WhjOgJaQIhenZVTHDsOcmGZvRgqCIjRMeEgV/wYGP3yRT+ztmNXQAmHdaX36CeE7dX7vkHh7ftdSsVOAkyJTwGeKqkZhUf/NY6ga+gjHeDjXbCOFq8=",
    "llm": "gpt-3.5-turbo",
    "llm_responses": [
        {
            "name": "mixtral-8x7b-32768",
            "response": "Error in processing llm respose : Error code: 400 - {'error': {'message': 'The model `mixtral-8x7b-32768` has been decommissioned and is no longer supported. Please refer to https://console.groq.com/docs/deprecations for a recommendation on which model to use instead.', 'type': 'invalid_request_error', 'code': 'model_decommissioned'}}"
        },
        {
            "name": "cohere",
            "response": "Here is the SQL `INSERT` command based on the provided details, adhering to the instructions:\n\n```sql\nINSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name)\nVALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');\n```\n\n**Note:** Ensure the table `transactions` and its columns (`Cardholder_Name`, `Card_Number`, `Expiry_Date`, `CVV`, `Transaction_Amount`, `Merchant_Name`) exist in your database with the appropriate data types. If `Transaction_Amount` is stored as a numeric value without the `$` symbol, you should adjust the value accordingly, but since the instructions specify preserving the exact format, the `$` is included here."
        },
        {
            "name": "gpt-4",
            "response": "Here is the SQL `INSERT` command based on your provided information:\n\n```sql\nINSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name) \nVALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');\n```\n\n**Note:** Make sure that the table structure matches with the column names and their data types in your SQL Database before executing this command."
        }
    ],
    "prompt": " Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 981 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
    "is_api_key_encrypted": true
}
```
## Sample Response:
```
{
    "success": true,
    "data": "{\n  \"mixtral-8x7b-32768\": {\n            \"rank\": \"3\",\n            \"score\": \"1\",\n            \"explanation\": \"The response is invalid as it does not provide the SQL insert command requested in the prompt.\"\n        },\n\"cohere\": {\n            \"rank\": \"1\",\n            \"score\": \"99\",\n            \"explanation\": \"The response is highly relevant, providing the correct SQL insert command with additional notes for execution.\"\n        },\n\"gpt-4\": {\n            \"rank\": \"2\",\n            \"score\": \"98\",\n            \"explanation\": \"The response is accurate, offering the SQL insert command as requested with a reminder to verify table structure.\"\n        },\n  \"Task_Identification\": [\"Text Generation\"],\n  \"Prompt_Engineering_Method\": [\"Zero Shot\"],\n  \"Sentiment_Analysis\": [],\n  \"Semantic_Novelty_Measurement\": []\n}",
    "error_message": ""
}
```
------------------------------------------------------------------------------------------------------------------------------------------------


## Network Request Analysis: `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-compliance-reports-v2`

**Purpose:**

This API request is to retrieve compliance reports. The presence of "v2" in the path suggests it's the second version of this endpoint. 

**Request Details:**

*   **URL:** `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-compliance-reports-v2`
*   **Method:** `<redacted>` (POST)
*   **Headers:**
    *   `accept: application/json`: The client expects a JSON response.
    *   `accept-encoding: gzip, deflate, br, zstd`: The client can handle compressed responses.
    *   `accept-language: en-US,en;q=0.9,hi;q=0.8`: Client's language preferences.
    *   `authorization: <redacted>`: Authentication token.
    *   `content-length: <redacted>`: Size of the request body.
    *   `content-type: application/json`: The request body is in JSON format.
    *   `origin: https://demo.zerotrusted.ai`: The request's origin.
    *   `referer: https://demo.zerotrusted.ai/`: The referring page.
    *   `user-agent: Mozilla/5.0 ... Chrome/134.0.0.0`: The client's browser and version.

**Response Details:**

*   **Status Code:** `200 OK`.
*   **Headers:**
    *   `access-control-allow-credentials: true`: Allows credentials in cross-origin requests.
    *   `access-control-allow-origin: https://demo.zerotrusted.ai`: Allows cross-origin requests from this origin.
    *   `content-length: <redacted>`: The size of the response body.
    *   `content-type: application/json`: The response is in JSON format.
    *   `date: Fri, 21 Mar 2025 21:07:41 GMT`: The response timestamp.
    *   `server: zta`: The server software.
    *   `strict-transport-security: max-age=31536000; includeSubDomains; preload`: HSTS policy is enabled.
    *   `vary: Origin`: The response may vary based on the `Origin`.
    *   `x-content-type-options: nosniff`: Prevents MIME sniffing.

## API Request Summary:

| Field                 | Value                                                              |
| --------------------- | ------------------------------------------------------------------ |
| **URL**               | `https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-compliance-reports-v2` |
| **Method**            | `<redacted>` (POST)                                                |
| **Request Content-Type** | `application/json`                                              |
| **Response Content-Type**| `application/json`                                              |
| **Authorization**     | `<redacted>` (Present)                                             |
| **Origin**            | `https://demo.zerotrusted.ai`                                      |
| **Payload**           | `application/json`                                                 |
| **Response**          | `200 OK` (Successful, JSON data returned)                          |

## Sample PayLoad:
```
'{
    "compliance_array": [
        "ccpa",
        "hipaa",
        "hitech",
        "hitrust",
        "pci_dss",
        "glba",
        "lgpd"
    ],
    "compliance_report": true,
    "file_pii_array": [],
    "pii_array": [
        [
            [
                "Alex",
                "Firstname"
            ],
            [
                "Johnson",
                "Lastname"
            ],
            [
                "123",
                "CVV"
            ],
            [
                "alex",
                "Custom"
            ]
        ],
        "Fictionalize",
        " Generate SQL insert command using the following details: Cardholder Name: Alex Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store "
    ],
    "is_api_key_encrypted": true,
    "file_name": ""
}'
```
## Sample Response:
```
'{
    "success": true,
    "data": {
        "compliance_violation": 11.428571428571429,
        "compliance_violation_fixed_by": "Fictionalize",
        "compliance_violation_fixed_percentage": 100.0,
        "compliance_report": [
            {
                "element": "Alex",
                "element_type": "Firstname",
                "violations": 50.0,
                "compliance_text": [
                    {
                        "query": "Firstname",
                        "score": "0.41601932",
                        "complianceInfo": {
                            "id": 2,
                            "compliance": "PII",
                            "dataField": "Name",
                            "controlIds": "AC-2, AC-3, IA-2",
                            "overlays": "CNSSI 1253",
                            "keywords": "name,fullname,full-name,full_name,firstname,lastname,first_name,last_name,first-name,last-name,fname,lname,surname",
                            "description": "Account Management, Identification and Authentication",
                            "documentationLink": "https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-2, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-3, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=IA-2",
                            "gdpr": true,
                            "lgpd": false,
                            "ccpa": true,
                            "hipaa": false,
                            "hitech": false,
                            "hitrust": false,
                            "pcI_DSS": false,
                            "glba": false,
                            "violations": "Unauthorized access to names ,Weak authentication, Lack of audit trails",
                            "details": "In various contexts, a  Name can represent a persons first name, last name, or both, depending on the cultural conventions and specific requirements of the situation."
                        }
                    },
                    {
                        "query": "Firstname",
                        "score": "0.37609094",
                        "complianceInfo": {
                            "id": 43,
                            "compliance": "Employee Records",
                            "dataField": "Date of Birth",
                            "controlIds": "AC-2, AC-3, AC-16, AC-18",
                            "overlays": "CNSSI 1253",
                            "keywords": "dob,birthdate,dateofbirth",
                            "description": "Account Management, Authentication, Access Control",
                            "documentationLink": "https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-2, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-3, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-16, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-18",
                            "gdpr": true,
                            "lgpd": false,
                            "ccpa": true,
                            "hipaa": true,
                            "hitech": false,
                            "hitrust": false,
                            "pcI_DSS": false,
                            "glba": false,
                            "violations": "Unauthorized access to DOB, Weak authentication, Inadequate access control",
                            "details": "DOB is commonly used in various official documents, such as identification cards, passports, and medical records, to confirm a person’s age and establish their identity"
                        }
                    }
                ]
            },
            {
                "element": "Johnson",
                "element_type": "Lastname",
                "violations": 50.0,
                "compliance_text": [
                    {
                        "query": "Lastname",
                        "score": "0.48503584",
                        "complianceInfo": {
                            "id": 2,
                            "compliance": "PII",
                            "dataField": "Name",
                            "controlIds": "AC-2, AC-3, IA-2",
                            "overlays": "CNSSI 1253",
                            "keywords": "name,fullname,full-name,full_name,firstname,lastname,first_name,last_name,first-name,last-name,fname,lname,surname",
                            "description": "Account Management, Identification and Authentication",
                            "documentationLink": "https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-2, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-3, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=IA-2",
                            "gdpr": true,
                            "lgpd": false,
                            "ccpa": true,
                            "hipaa": false,
                            "hitech": false,
                            "hitrust": false,
                            "pcI_DSS": false,
                            "glba": false,
                            "violations": "Unauthorized access to names ,Weak authentication, Lack of audit trails",
                            "details": "In various contexts, a  Name can represent a persons first name, last name, or both, depending on the cultural conventions and specific requirements of the situation."
                        }
                    },
                    {
                        "query": "Lastname",
                        "score": "0.46600032",
                        "complianceInfo": {
                            "id": 43,
                            "compliance": "Employee Records",
                            "dataField": "Date of Birth",
                            "controlIds": "AC-2, AC-3, AC-16, AC-18",
                            "overlays": "CNSSI 1253",
                            "keywords": "dob,birthdate,dateofbirth",
                            "description": "Account Management, Authentication, Access Control",
                            "documentationLink": "https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-2, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-3, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-16, https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home?element=AC-18",
                            "gdpr": true,
                            "lgpd": false,
                            "ccpa": true,
                            "hipaa": true,
                            "hitech": false,
                            "hitrust": false,
                            "pcI_DSS": false,
                            "glba": false,
                            "violations": "Unauthorized access to DOB, Weak authentication, Inadequate access control",
                            "details": "DOB is commonly used in various official documents, such as identification cards, passports, and medical records, to confirm a person’s age and establish their identity"
                        }
                    }
                ]
            },
            {
                "element": "123",
                "element_type": "CVV",
                "violations": 0.0,
                "compliance_text": []
            },
            {
                "element": "alex",
                "element_type": "Custom",
                "violations": 0.0,
                "compliance_text": []
            }
        ]
    },
    "error_message": ""
}'
```
