---

# API Documentation – Copy & Paste Ready

This documentation provides all the endpoint details along with JSON-formatted headers and payloads so that you can quickly test the APIs in Postman. Replace `<YOUR_BEARER_TOKEN>` with your bearer key.

---

## Table of Contents

1. [Get Anonymize Prompt](#get-anonymize-prompt)
2. [Get LLM Response](#get-llm-response)
3. [LLM Report (V2)](#llm-report-v2)
4. [Get Reliability Scores](#get-reliability-scores)
5. [Get Compliance Reports V2](#get-compliance-reports-v2)

---

## 1. Get Anonymize Prompt

**Endpoint:**  
`https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-anonymize-prompt`

**Purpose:**  
Retrieve an anonymization prompt for masking PII.

### Request Details

- **Method:** POST  
- **Content-Type:** `multipart/form-data`  
- **Headers (JSON Format):**

```json
{
  "Authorization": "Bearer <YOUR_BEARER_TOKEN>",
  "Origin": "https://demo.zerotrusted.ai",
  "Content-Type": "multipart/form-data; boundary=----WebKitFormBoundaryIfFsBFmd4wKwZg49"
}
```

- **Sample Payload (as form-data):**

| Field                    | Value |
| ------------------------ | ----- |
| pii_entities             | first name, last name, ssn, credit card number, cvv, bank account number, email, phone number, driving license number, passport number, address |
| prompt                   | Generate SQL insert command using the following details: Cardholder Name: Alex Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store |
| anonymize_keywords       | Alex |
| keyword_safeguard        | beartest,bear |
| uploaded_file            | (leave blank) |
| client_api_key           | ApmIQgrYH1SFTX1+WoIBR9I+0ojujfIXIU95tlbZaXSgqld5qzx14ZqdtlV3dDIs056eEeVAsPnHS7Mgb+ObHVX8VtrtfQ7GnRTsHkUxM9yckrb2iCBYWwW64WhjOgJaQIhenZVTHDsOcmGZvRgqCIjRMeEgV/wYGP3yRT+ztmNXQAmHdaX36CeE7dX7vkHh7ftdSsVOAkyJTwGeKqkZhUf/NY6ga+gjHeDjXbCOFq8= |
| llm                      | gpt-4-turbo |
| do_not_anonymize_keywords| happy kid,,1234 5678 9012 3456,12/24,General Hospital |
| is_api_key_encrypted     | true |

### Sample Response

```json
{
  "success": true,
  "data": {
    "anonymized_prompt": " Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 987 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
    "highlighted_original_prompt": " Generate SQL insert command using the following details: Cardholder Name: <pii_text>Alex</pii_text> <pii_text>Johnson</pii_text> Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: <pii_text>123</pii_text> Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
    "highlighted_anonymized_prompt": " Generate SQL insert command using the following details: Cardholder Name: <pii_text>Brian</pii_text> <pii_text>Thompson</pii_text> Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: <pii_text>987</pii_text> Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store\r\n",
    "pii_list": [
      ["Alex", "Brian"],
      ["Johnson", "Thompson"],
      ["123", "987"],
      ["alex", "chris"]
    ],
    "pii_entities": [
      ["Alex", "Firstname"],
      ["Johnson", "Lastname"],
      ["123", "CVV"],
      ["alex", "Custom"]
    ],
    "safe_guard_error_message": "",
    "file_location": "",
    "file_pii_array": []
  },
  "error_message": ""
}
```

---

## 2. Get LLM Response

**Endpoint:**  
`https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-llm-response`

**Purpose:**  
Fetch a response from a Large Language Model based on a prompt.

### Request Details

- **Method:** POST  
- **Content-Type:** `multipart/form-data`  
- **Headers (JSON Format):**

```json
{
  "Authorization": "Bearer <YOUR_BEARER_TOKEN>",
  "Origin": "https://demo.zerotrusted.ai",
  "Content-Type": "multipart/form-data; boundary=----WebKitFormBoundary2dlUoorxjFxNyVVD",
  "Accept": "application/json, text/plain, */*"
}
```

- **Sample Payload (as form-data):**

| Field             | Value |
| ----------------- | ----- |
| llm               | cohere |
| prompt            | Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 981 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store |
| file_pii_array    | [] (empty array) |
| client_api_key    | p1XHsoteATOrW+jJms6x/t9BXO0L8uiW6nyZOUNzV0u7gROmSaGSycYBn/1mUOBu |
| fallback_llm      | true |
| conversation_id   | 1742571573091 |
| uploaded_file     | (leave blank) |
| is_api_key_encrypted | true |

### Sample Response

The response is plain text containing the SQL command:

```
Here is the SQL `INSERT` command based on the provided details, adhering to the instructions:

```sql
INSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name)
VALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');
```

**Note:** Ensure the table `transactions` exists and has the appropriate columns and data types.
```

---

## 3. LLM Report (V2)

**Endpoint:**  
`https://demo-agents.zerotrusted.ai/zt-ml/api/v2/zt-llm-report-llms/V2`

**Purpose:**  
Retrieve a detailed report on LLM responses including rank, score, and explanations.

### Request Details

- **Method:** POST  
- **Content-Type:** `application/json`  
- **Headers (JSON Format):**

```json
{
  "Authorization": "Bearer <YOUR_BEARER_TOKEN>",
  "Origin": "https://demo.zerotrusted.ai",
  "Content-Type": "application/json",
  "Accept": "application/json, text/plain, */*"
}
```

- **Sample Payload (JSON):**

```json
{
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
  "user_location_detail": "{\"ip\":\"223.233.86.127\",\"hostname\":\"example.host\",\"city\":\"Pune\",\"region\":\"Maharashtra\",\"country\":\"IN\",\"loc\":\"18.5196,73.8554\",\"org\":\"Example Org\",\"postal\":\"411001\",\"timezone\":\"Asia/Kolkata\"}",
  "browser_detail": "{\"appName\":\"Netscape\",\"appVersion\":\"5.0\",\"userAgent\":\"Mozilla/5.0 (Windows NT 10.0; Win64; x64)\",\"platform\":\"Win32\"}",
  "device_type": "Desktop"
}
```

### Sample Response

```json
{
  "anonymizedPrompt": " Generate SQL insert command using the following details: Cardholder Name: <ztanonym> Barnes Group </ztanonym> Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
  "highlightedPrompt": " Generate SQL insert command using the following details: Cardholder Name: <privacytext> Alex </privacytext> Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
  "anonymizedFlag": true,
  "llmResponse": "",
  "llmResponseRepl": null,
  "llmResponseTagged": null,
  "piiList": [
    ["Alex", "Barnes Group"]
  ]
}
```

---

## 4. Get Reliability Scores

**Endpoint:**  
`https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-reliability-scores?service=openai`

**Purpose:**  
Fetch reliability scores for the specified service ("openai") across various LLMs.

### Request Details

- **Method:** POST  
- **Content-Type:** `application/json`  
- **Headers (JSON Format):**

```json
{
  "Authorization": "Bearer <YOUR_BEARER_TOKEN>",
  "Origin": "https://demo.zerotrusted.ai",
  "Content-Type": "application/json",
  "Accept": "application/json",
  "Referer": "https://demo.zerotrusted.ai/"
}
```

- **Sample Payload (JSON):**

```json
{
  "client_api_key": "ApmIQgrYH1SFTX1+WoIBR9I+0ojujfIXIU95tlbZaXSgqld5qzx14ZqdtlV3dDIs056eEeVAsPnHS7Mgb+ObHVX8VtrtfQ7GnRTsHkUxM9yckrb2iCBYWwW64WhjOgJaQIhenZVTHDsOcmGZvRgqCIjRMeEgV/wYGP3yRT+ztmNXQAmHdaX36CeE7dX7vkHh7ftdSsVOAkyJTwGeKqkZhUf/NY6ga+gjHeDjXbCOFq8=",
  "llm": "gpt-3.5-turbo",
  "llm_responses": [
    {
      "name": "mixtral-8x7b-32768",
      "response": "Error in processing llm respose : Error code: 400 - {\"error\": {\"message\": \"The model `mixtral-8x7b-32768` has been decommissioned and is no longer supported.\", \"type\": \"invalid_request_error\", \"code\": \"model_decommissioned\"}}"
    },
    {
      "name": "cohere",
      "response": "Here is the SQL `INSERT` command based on the provided details, adhering to the instructions:\n\n```sql\nINSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name)\nVALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');\n```"
    },
    {
      "name": "gpt-4",
      "response": "Here is the SQL `INSERT` command based on your provided information:\n\n```sql\nINSERT INTO transactions (Cardholder_Name, Card_Number, Expiry_Date, CVV, Transaction_Amount, Merchant_Name)\nVALUES ('Brian Thompson', '1234 5678 9012 3456', '12/24', '981', '$200', 'Tech Gadgets Online Store');\n```"
    }
  ],
  "prompt": " Generate SQL insert command using the following details: Cardholder Name: Brian Thompson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 981 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store",
  "is_api_key_encrypted": true
}
```

### Sample Response

```json
{
  "success": true,
  "data": "{\n  \"mixtral-8x7b-32768\": { \"rank\": \"3\", \"score\": \"1\", \"explanation\": \"The response is invalid as it does not provide the SQL insert command requested in the prompt.\" },\n  \"cohere\": { \"rank\": \"1\", \"score\": \"99\", \"explanation\": \"The response is highly relevant, providing the correct SQL insert command with additional notes for execution.\" },\n  \"gpt-4\": { \"rank\": \"2\", \"score\": \"98\", \"explanation\": \"The response is accurate, offering the SQL insert command as requested with a reminder to verify table structure.\" },\n  \"Task_Identification\": [\"Text Generation\"],\n  \"Prompt_Engineering_Method\": [\"Zero Shot\"],\n  \"Sentiment_Analysis\": [],\n  \"Semantic_Novelty_Measurement\": []\n}",
  "error_message": ""
}
```

---

## 5. Get Compliance Reports V2

**Endpoint:**  
`https://demo-agents.zerotrusted.ai/zt-ml/api/v1/get-compliance-reports-v2`

**Purpose:**  
Retrieve detailed compliance reports for provided PII data, including violation scores and compliance texts.

### Request Details

- **Method:** POST  
- **Content-Type:** `application/json`  
- **Headers (JSON Format):**

```json
{
  "Authorization": "Bearer <YOUR_BEARER_TOKEN>",
  "Origin": "https://demo.zerotrusted.ai",
  "Content-Type": "application/json",
  "Accept": "application/json",
  "Referer": "https://demo.zerotrusted.ai/"
}
```

- **Sample Payload (JSON):**

```json
{
  "compliance_array": ["ccpa", "hipaa", "hitech", "hitrust", "pci_dss", "glba", "lgpd"],
  "compliance_report": true,
  "file_pii_array": [],
  "pii_array": [
    [
      ["Alex", "Firstname"],
      ["Johnson", "Lastname"],
      ["123", "CVV"],
      ["alex", "Custom"]
    ],
    "Fictionalize",
    " Generate SQL insert command using the following details: Cardholder Name: Alex Johnson Card Number: 1234 5678 9012 3456 Expiry Date: 12/24 CVV: 123 Transaction Amount: $200 Merchant Name: Tech Gadgets Online Store "
  ],
  "is_api_key_encrypted": true,
  "file_name": ""
}
```

### Sample Response

```json
{
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
              "details": "In various contexts, a Name can represent a person's first name, last name, or both."
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
              "details": "DOB is used in official documents such as IDs and passports."
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
              "details": "In various contexts, a Name can represent a person's first name, last name, or both."
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
              "details": "DOB is used in official documents such as IDs and passports."
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
}
```

---

## How to Use in Postman

1. **Import the Endpoint Details:**  
   Copy the JSON headers and payload sections for the endpoint you wish to test.

2. **Replace the Authorization Header:**  
   Replace `<YOUR_BEARER_TOKEN>` with your actual bearer token.

3. **Set Request Type:**  
   For endpoints using `multipart/form-data`, switch to the "form-data" tab in Postman and paste the provided fields. For JSON payloads, select the "raw" body type and choose "JSON".

4. **Send the Request:**  
   Simply paste the URL, set the method to POST, paste the headers, and payload, then click "Send".

---
