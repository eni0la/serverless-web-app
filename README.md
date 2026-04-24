<<<<<<< HEAD
Deploying a Serverless Web Application on AWS using S3, Lambda, API Gateway, DynamoDB, and CloudFront



OVERVIEW



This project demonstrates how to build and deploy a serverless static web app using:



Amazon S3 – Static website hosting

AWS Lambda – Backend logic (GET \& POST functions)

Amazon API Gateway – API routing

Amazon DynamoDB – NoSQL database

Amazon CloudFront – Content delivery network for performance



FEATURES

* Add student data (POST request)
* Retrieve all student data (GET request)
* Serverless architecture
* Static frontend website hosted on S3
* API integration using API Gateway
* Data stored in DynamoDB
* Global performance optimization using CloudFront



STEP-BY-STEP IMPLEMENTATION

1\. Created a table in DynamoDB named:

studentData

Defined primary key (studentId)



2\. Created two Lambda Functions (GET \& POST)



* InsertStudent Function (POST)

Inserts student data into DynamoDB

Accepts name, class, age, studentId

* GetStudent Function (GET)

Retrieves all student records

* IAM Role Configuration



During setup, I noticed the Lambda function could not access DynamoDB.



The tutorial did not include IAM role setup

I manually created and attached a role:

AmazonDynamoDBFullAccess



✔ After troubleshooting, the functions worked successfully.



3\. Tested GET and POST functions in AWS Lambda console

✔ Verified data insertion and retrieval worked correctly



4\. Created a REST API using Amazon API Gateway

Integrated Lambda functions with API methods:

Endpoints;

GET /students → Fetch all students

POST /students → Add new student



5\. CORS(Cross Origin Resource Sharing) Configuration

To allow frontend communication with backend:



Enabled CORS in API Gateway

Allowed:

GET

POST

OPTIONS

Fixed cross-origin request errors between frontend and API



6\. Deployed API to a new stage: prod

Tested endpoints successfully after deployment



7\. Host Frontend on S3

Created S3 bucket

Uploaded:

index.html

scripts.js



Enabled static website hosting



Issue Encountered:

Received 403 Forbidden error

Fix:

Disabled “Block Public Access”

Updated bucket policy using AWS policy generator and attached CORS policy

Granted public read access



8\. CloudFront Integration

Created a CloudFront distribution using Amazon CloudFront

Connected it to S3 bucket as origin

Issue Encountered:

Website returned Access Denied

Fix:

Updated distribution settings by adding index.html as Default Root Object

Waited for deployment status



✔ Website successfully loaded via CloudFront domain



CHALLENGES \& TROUBLESHOOTING

* Issue 1: Lambda Access to DynamoDB



✔ Fixed by creating and attaching IAM role manually



* Issue 2: GET Method Error



✔ Fixed by correcting region configuration in Lambda



* Issue 3: CORS Errors



✔ Fixed by enabling CORS in API Gateway



* Issue 4: S3 Access Denied (403)



✔ Fixed by:



Disabling Block Public Access

Updating bucket policy



* Issue 5: CloudFront Access Denied



✔ Fixed by:



Setting default root object (index.html)

=======
# serverless-web-app
>>>>>>> d0c37b9bf0aa2863811a098ebc7dd62af869e92d
