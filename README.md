## :heart: Star :heart: the repo to support the project or :smile:[Follow Me](https://github.com/harsh6768).Thanks!


# aws-lambda-studious

1. Click Create Function After going to Lambda Dashboard.

 <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2010-50-41.png" alt="">
 
2. give the proper name to the lambda function and select the node version and then click create function

 <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2010-54-04.png" alt="">
 
 Now we need to add trigger so that we can manage when will be lambda function called.We will trigger the lambda function whenever any new file will be added to the s3 bucket.
 Before that we need to create the S3 bucket.
 
 3. You can see add Trigger option but before that we need to create the s3 bucket.
 
 <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2011-03-57.png" alt="">
    
 4. Create S3 Bucket after going to S3 dashboard and give the universal unique name to the s3 bucket.
 
  <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2011-06-10.png" alt="">
 
5. After creating the s3 bucket .Go to lambda dashboard and click add Trigger option and select s3 as trigger.Select the bucket name from the Bucket option and also select event type which will handle when to be lambda function called.

<img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2011-07-02.png" alt="">
 
 6. Now we need to create IAM Role that will define the permissions of the Lambda function.
   Go to IAM Dashboard and select Role from the left Navigation and then click create Role .
 
 7. After clicking the create Role button. Select AWS service which will use this role. In our case we are using Lambda functions ,therefore select Lambda .
 
 <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-20%2011-24-55.png" alt="">
 
 8. search s3 all access and cloud watch all logs policies and checked and click on preview button
 
  <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-25%2017-50-08.png" alt="">
  
 9. Provide name to the IAM role and here you can see the policies you have granted to this role.
 
   <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-25%2017-50-35.png" alt="">
 
 
