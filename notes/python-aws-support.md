### Python for AWS Cloud Support: Beginner Cheat Sheet
Designed for macOS users starting their journey into AWS automation and cloud support.

Python Basics (Syntax & Logic)

- Variables & Types  
  name = "AWS_Server"  
  count = 5  
  is_active = True  
  (Stores a string, an integer, and a boolean.)

- Lists  
  regions = ["us-east-1", "us-west-2"]  
  (Stores multiple items in a single variable. Access first item with regions[0].)

- If Statements  
  if count > 0:  
      print("Servers running")  
  else:  
      print("No servers")  
  (Makes decisions. Python uses indentation – spaces – to group code.)

- For Loops  
  for r in regions:  
      print("Checking " + r)  
  (Repeats an action for every item in a list. Great for checking multiple AWS resources.)

- Dictionaries  
  ec2 = {"ID": "i-123", "Type": "t2.micro"}  
  (Stores data in "Key": "Value" pairs. Access ID with ec2["ID"].)

Common Automation Tasks

- Reading a File  
  with open("logs.txt") as f:  
      content = f.read()  
  (Used for analyzing local log files for errors or system status.)

- Environment Variables  
  import os  
  key = os.getenv("AWS_KEY")  
  (Securely access credentials without typing them directly into the code.)

- Error Handling  
  try:  
      # do something  
      ...  
  except Exception as e:  
      print("Error:", e)  
  (Prevents your script from crashing if an AWS service is down or access is denied.)

Cloud Support & AWS Integration (Boto3)

- Authentication  
  import boto3  
  session = boto3.Session()  
  (Uses your AWS CLI credentials to log in via Python.)

- Service Client  
  s3 = boto3.client('s3')  
  (Creates a connection to a specific service like S3 storage.)

- Listing Resources  
  response = s3.list_buckets()  
  print(response)  
  (Fetches and prints a list of all your S3 buckets.)

- Parsing JSON  
  import json  
  data = json.loads(response_text)  
  (AWS and APIs send data in JSON format; this turns it into a Python dictionary.)

Daily Workflow for a Cloud Tech

1) Identify  
   Find a repetitive task, for example:  
   "I have to check these 10 S3 buckets every morning."

2) Script  
   Write a Python script using boto3 to loop through the buckets and print their status.

3) Schedule  
   Run the script via a cron job on your Mac or as an AWS Lambda function.

Troubleshooting Tips

- IndentationError  
  Check your spaces; Python is very strict about alignment.

- ModuleNotFoundError  
  Run: pip3 install <library>  
  Or make sure your virtual environment is activated.

- PermissionError  
  Your AWS IAM user or role doesn’t have the right permissions for the action.

- Print is your friend  
  If you aren’t sure what a variable holds, use:  
  print(variable_name)  
  to see it in the terminal.

