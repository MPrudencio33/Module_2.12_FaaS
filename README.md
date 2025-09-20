# Module_2.12_FaaS
Answers to Assignment on Module 2.12 Function as a Service

Given a Lambda function that is triggered upon the creation of files in an S3 bucket, answer the 
following:
 1. What is the purpose of the execution role on the Lambda function?
    ANSWER: The execution role allows the Lambda function to interact with AWS services, such as reading the uploaded file from S3,
            logging to CloudWatch, or any other service it needs to access to perform its job.
            Without the correct permissions in the execution role, the function will fail when trying to access those resources.

 2. What is the purpose of the resource-based policy on the Lambda function?
    ANSWER: The resource-based policy on a Lambda function grants other services, such as S3, the permission to invoke the function.
            Without this policy, even if S3 is configured to trigger the Lambda, it will not work, i.e. S3 will be denied permission to invoke the function.
    
 3. If the function is needed to upload a file into an S3 bucket, describe (i.e no need for the actual policies)--
    a.  What is the needed update on the execution role?
        ANSWER: To allow a Lambda function to upload files to an S3 bucket, you must update its execution role to include s3:PutObject and related permissions for the target bucket.
            This gives the function the required access to perform the upload operation successfully.
 
     b. What is the new resource-based policy that needs to be added (if any)?
        ANSWER: If uploads are from the same AWS account, no bucket policy is needed — just IAM permissions for the uploader.
                If uploads are from another account, you need a bucket policy with s3:PutObject.
