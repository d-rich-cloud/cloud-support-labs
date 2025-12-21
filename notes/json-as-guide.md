### JSON Cheat Sheet for New AWS Support Engineers

What JSON Is and Why It Matters

JSON = JavaScript Object Notation.

In AWS support, JSON is:

- A standard way to write structured data as text.  
- Like a digital form with labels (keys) and answers (values).  
- Used by AWS for policies, logs, configurations, and API requests/responses.

Example:

{  
  "name": "Alice",  
  "age": 30,  
  "isCustomer": true  
}

Read as:

- name -> "Alice"  
- age -> 30  
- isCustomer -> true

In AWS support, you mainly:

- Read JSON to understand what is happening.  
- Check JSON when there is an error.  
- Make small edits (change a value, add/remove an item).

Where You’ll See JSON in AWS

1) IAM Policies  
   Define what users and roles are allowed or denied to do. All IAM policies are JSON.

2) CloudWatch Logs and Events  
   Many services write log messages and events in JSON format.

3) Service Configurations  
   API Gateway, Lambda, Step Functions, EventBridge, and others commonly use JSON for configuration and event payloads.

4) AWS CLI / SDK Output  
   Command results and API responses often come back in JSON.

JSON Basics: Building Blocks

1) Key-Value Pairs

{  
  "userName": "alice",  
  "loginCount": 5  
}

- Key = label or field name (always in double quotes).  
- Value = the data for that key.  
- Multiple pairs are separated by commas.

2) Objects – curly braces {}

{  
  "userName": "alice",  
  "loginCount": 5,  
  "isAdmin": false  
}

- { starts the object.  
- } ends the object.  
- Inside: "key": value entries.

3) Arrays – square brackets []

[ "apple", "banana", "orange" ]

Array of objects (very common in AWS):

[  
  { "name": "Alice", "role": "Admin" },  
  { "name": "Bob", "role": "User" }  
]

4) Main JSON Data Types

- String (text, in double quotes)        -> "region": "us-east-1"  
- Number (no quotes)                     -> "maxRetries": 3  
- Boolean (true/false, no quotes)        -> "enabled": true  
- Null (no value / empty)                -> "description": null  
- Object (group of key-value pairs)      -> {...}  
- Array (list of values)                 -> [...]

5) JSON Syntax Rules That Often Cause Errors

- Keys must be in double quotes  
  Correct: "Action": "s3:GetObject"  
  Incorrect: Action: "s3:GetObject"

- Strings must be in double quotes  
  Correct: "Version": "2012-10-17"  
  Incorrect: 'Version': '2012-10-17'

- Commas  
  Use commas between items, but not after the last item in an object or array.

- Matching brackets  
  Every { must have a matching }.  
  Every [ must have a matching ].

Most "invalid JSON" errors come from these issues.

Example: Simple IAM Policy – Read-only S3 Bucket

{  
  "Version": "2012-10-17",  
  "Statement": [  
    {  
      "Effect": "Allow",  
      "Action": [  
        "s3:GetObject",  
        "s3:ListBucket"  
      ],  
      "Resource": [  
        "arn:aws:s3:::example-bucket",  
        "arn:aws:s3:::example-bucket/*"  
      ]  
    }  
  ]  
}

How to read this:

- "Version": "2012-10-17"  
  Policy language version.

- "Statement": [ ... ]  
  An array (list) of statement objects.

Inside the statement object:

- "Effect": "Allow"  
  This statement allows the listed actions. (Could also be "Deny".)

- "Action": [  
    "s3:GetObject",  
    "s3:ListBucket"  
  ]  
  List of allowed actions on S3.

- "Resource": [  
    "arn:aws:s3:::example-bucket",  
    "arn:aws:s3:::example-bucket/*"  
  ]  
  List of resources (the bucket and all objects in that bucket).

Step-By-Step Strategy to Read JSON

1) Format / pretty-print it using a JSON formatter.  
2) Scan the top-level keys (e.g., Version, Statement, timestamp, message).  
3) Open nested objects ({...}) and arrays ([...]) only as needed.  
4) Ignore non-essential fields at first; focus on what relates to the problem.

Safely Editing JSON (Without Breaking It)

Golden rules:

1) Keep braces and brackets intact.  
2) Watch commas: between items but never after the last item.  
3) Always use double quotes for keys and strings.  
4) Use a JSON validator (JSON lint, etc.) before saving changes.

Tiny Edit Example – Add One More Action

Original:

"Action": [  
  "s3:GetObject",  
  "s3:ListBucket"  
]

Goal: add s3:PutObject.

Result:

"Action": [  
  "s3:GetObject",  
  "s3:ListBucket",  
  "s3:PutObject"  
]

Common JSON Problems in AWS

- Trailing comma  
  {  
    "Effect": "Allow",  
    "Action": "s3:ListBucket",  
  }  <- last comma is invalid.

- Misspelled keys  
  "Resorce": "arn:aws:s3:::example-bucket"  
  (Should be "Resource".)

- Wrong data type  
  "enabled": "true"  
  (String instead of boolean true.)

- Unmatched braces/brackets  
  Often happens when lines are deleted or added carelessly.

Quick Symbol Reference

- {} -> Object (group of key-value pairs)  
- [] -> Array (list)  
- :  -> Between key and value  
- ,  -> Between items  
- "" -> Around all keys and string values

If you can recognize objects {}, arrays [], read small policies/log entries, and avoid basic syntax mistakes, you’re in good shape for entry-level cloud/AWS support work.
