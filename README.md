## :heart: Star :heart: the repo to support the project or :smile:[Follow Me](https://github.com/harsh6768).Thanks!


# aws-lambda-studious

#### 1. How to use Lambda functions to get the data of Files that added in S3 Bucket.

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
   
 10. Select Use an existin role from Execution Role section and then select IAM ROLE that you have created previously.
 
   <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-25%2018-20-34.png" alt="">
   
 11. Now click add trigger button and search for CloudWatchEvents and add to it.
 
   <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-25%2018-20-44.png" alt="">
 
 12. This lambda used to fetch the data of files everytime any files added to the S3 bucket.
 
         const AWS=require("aws-sdk");

         AWS.config.update({ 
             accessKeyId: "",   //add access key
             secretAccessKey: "",  //add secret key
             region: "us-east-1",
         });

          // const s3=new AWS.S3();
         exports.handler = async (event, context,callback) => {

            let bucketName =event.Records[0].s3.bucket.name;
            let filename = event.Records[0].s3.object.key;
            // let filename='Screenshot from 2020-01-16 11-47-00.png'
            console.log("bucketName ===>",bucketName);
            console.log("fileName ==>",filename);
            const s3 = new AWS.S3({
                params: { Bucket: bucketName}
            });
            let params = { Bucket: bucketName, Key: filename };
            console.log("Params ===>>>>",params);

            const data = await s3.getObject(params).promise();

            const response = {
                statusCode: 200,
                body: data.body.toString(),
            };
            console.log("DATA ====>",response);
  
         };
         
   
   13 Go to Cloud Watch dashboard and select log groups from logs and then select lambda functions for logs. You can see log that will call everytime lambda function get triggered.
   
   <img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-25%2018-34-05.png" alt="">
   
 
 
 ### 2. How to create Layer :
     
   We use layer to use npm libraries which are not provided as a built in libraries inside lambda functions.
   
   1. Make directory in local machine with name nodejs(name is specific) then go to console
   2. npm init -y   generate package.json file
   3. install npm module which you need for lambda functions 
   4. make zip of nodejs folder
   5. Go to Lambda console and click Layer from top left list  and click create Layer
     
<img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-28%2016-16-56.png" alt="">
  
  6. Give the name to the Lambda Layer and import the zip file
  

<img src="https://github.com/harsh6768/aws-lambda-studious/blob/master/Images/Screenshot%20from%202020-01-28%2016-17-22.png" alt="">
 
 7. Now you can require any library in your lambda functions that you have added in lambda layers
 

#### 3. How to call one lambda functions to another

 
    
 
