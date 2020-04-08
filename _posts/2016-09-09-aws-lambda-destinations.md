---
title: 'AWS Lambda Destinations'
date: 2019-11-26T03:04:00+01:00
draft: false
---

Today we’re announcing [AWS Lambda](https://aws.amazon.com/lambda/) Destinations for asynchronous invocations. This is a feature that provides visibility into Lambda function invocations and routes the execution results to AWS services, simplifying event-driven applications and reducing code complexity.

Asynchronous invocations
------------------------

When a function is invoked asynchronously, Lambda sends the event to an [internal queue](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html). A separate process reads events from the queue and executes your Lambda function. When the event is added to the queue, Lambda previously only returned a 2xx status code to confirm that the queue has received this event. There was no additional information to confirm whether the event had been processed successfully.

A common event-driven microservices architectural pattern is to use a queue or message bus for communication. This helps with resilience and scalability. Lambda asynchronous invocations can put an event or message on [Amazon Simple Notification Service](https://aws.amazon.com/sns/) (SNS), [Amazon Simple Queue Service](https://aws.amazon.com/sqs/) (SQS), or [Amazon EventBridge](https://aws.amazon.com/eventbridge/) for further processing. Previously, you needed to write the SQS/SNS/EventBridge handling code within your Lambda function and manage retries and failures yourself.

With Destinations, you can route asynchronous function results as an execution record to a destination resource without writing additional code. An execution record contains details about the request and response in JSON format including version, timestamp, request context, request payload, response context, and response payload. For each execution status such as _Success_ or _Failure_ you can choose one of four destinations: another Lambda function, SNS, SQS, or EventBridge. Lambda can also be configured to route different execution results to different destinations.

![Asynchronous Function Execution Result](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations1.png)

Success
-------

When a function is invoked successfully, Lambda routes the record to the destination resource for every successful invocation. You can use this to monitor the health of your serverless applications via execution status or build workflows based on the invocation result.

You no longer need to chain long-running Lambda functions together synchronously. Previously you needed to complete the entire workflow within the Lambda 15-minute function timeout, pay for idle time, and wait for a response. Destinations allows you to return a Success response to the calling function and then handle the remaining chaining functions asynchronously.

Failure
-------

Alongside today’s announcement of [Maximum Event Age and Maximum Retry Attempt for asynchronous invocations](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-lambda-supports-max-retry-attempts-event-age-asynchronous-invocations/), Destinations gives you the ability to handle the Failure of function invocations along with their Success. When a function invocation fails, such as when retries are exhausted or the event age has been exceeded (hitting its TTL), Destinations routes the record to the destination resource for every failed invocation for further investigation or processing.

Dead Letter Queues (DLQ) have been [available since 2016](https://aws.amazon.com/about-aws/whats-new/2016/12/aws-lambda-supports-dead-letter-queues/) and are a great way to handle asynchronous failure situations. Destinations provide more useful capabilities by passing additional function execution information, including code exception stack traces, to more destination services.

Destinations and DLQs can be used together and at the same time although Destinations should be considered a more preferred solution. If you already have DLQs set up, existing functionality does not change and Destinations does not replace existing DLQ configurations. If both Destinations and DLQ are used for Failure notifications, function invoke errors are sent to both DLQ and Destinations targets.

How to configure Destinations
-----------------------------

Adding Destinations is a straightforward process. This walkthrough uses the AWS Management Console but you can also use the [AWS CLI](https://aws.amazon.com/cli/), [AWS SAM](https://aws.amazon.com/serverless/sam/), [AWS CloudFormation](https://aws.amazon.com/cloudformation/), or language-specific SDKs for Lambda.

1.  Open the Lambda console [Functions page](https://console.aws.amazon.com/lambda/home#/functions). Choose an existing Lambda function, or create a new one. In this example, I create a new Lambda function. Choose **Create Function**.
2.  Enter a _Function name_, select **Node.js 12.x** for _Runtime_, and _Choose or create an execution role_. Ensure that your Lambda function execution role includes access to the destination resource.  
    ![Basic information](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations2.png)
3.  Choose **Create function**.
4.  Within the _Function code_ pane, paste the following Lambda function code. The code generates a function execution result of either _Success_ or _Failure_ depending on a JSON input (`"Success": true` or `"Success": false`).```
    // Lambda Destinations tester, Success returns a json blob, Failure throws an error  
       
     exports.handler = function(event, context, callback) {  
     var event_received_at = new Date().toISOString();  
     console.log('Event received at: ' + event_received_at);  
     console.log('Received event:', JSON.stringify(event, null, 2));  
       
     if (event.Success) {  
     console.log("Success");  
     context.callbackWaitsForEmptyEventLoop = false;  
     callback(null);  
     } else {  
     console.log("Failure");  
     context.callbackWaitsForEmptyEventLoop = false;  
     callback(new Error("Failure from event, Success = false, I am failing!"), 'Destination Function Error Thrown');  
     }  
     }; 
    ```
5.  Choose **Save**.
6.  To configure Destinations, within the _Designer pane_, choose **Add destination**.  
    ![Designer pane](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations3.png)
7.  Select the _Source_ as **Asynchronous invocation**. Select the _Condition_ as **On failure** or **On success**, depending on your use case. In this example, I select **On Success**.
8.  Enter the _Amazon Resource Name (ARN)_ for the _Destination SQS_ queue, SNS topic, Lambda function, or EventBridge event bus. In this example, I use the ARN of an SNS topic I have already configured.  
    ![Add destination](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations4.png)
9.  Choose **Save**. The Destination is added to SNS for **On Success**.  
    ![Designer](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations5.png)
10.  Add another Destination for **Failure** to Lambda. Within the Designer pane, choose **Add destination**.  
    ![Add destination](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations6.png)
11.  Select the _Source_ as **Asynchronous invocation**, the _Condition_ as **On failure** and Enter a _Destination_ Lambda function ARN, then choose **Save**.  
    ![Enter a Destination Lambda function ARN, and choose Save](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations7.png)
12.  The Destination is added to Lambda for **On Failure**.  
    ![7. The Destination has been added to Lambda for On Failure.](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2019/11/25/lambda-destinations8.png)

### Success testing

To test invoking the asynchronous Lambda function to generate a Success result, use the AWS CLI:

```
aws lambda invoke --function-name event-destinations --invocation-type Event --payload '{ "Success": true }' response.json
```

The Lambda function is invoked successfully with a response `"StatusCode": 202`.

And an SNS notification email is received, showing the invocation details with `"condition":"Success"` and the `requestPayload`.

```
{  
 "version": "1.0",  
 "timestamp": "2019-11-24T23:08:25.651Z",  
 "requestContext": {  
 "requestId": "c2a6f2ae-7dbb-4d22-8782-d0485c9877e2",  
 "functionArn": "arn:aws:lambda:sa-east-1:123456789123:function:event-destinations:$LATEST",  
 "condition": "Success",  
 "approximateInvokeCount": 1  
 },  
 "requestPayload": {  
 "Success": true  
 },  
 "responseContext": {  
 "statusCode": 200,  
 "executedVersion": "$LATEST"  
 },  
 "responsePayload": null  
 }
```

### Failure testing

The Lambda function can be set to _Failure_ by throwing an exception within the code. To test invoking the asynchronous Lambda function to generate a Failure result, use the AWS CLI:

`aws lambda invoke --function-name event-destinations --invocation-type Event --payload '{ "Success": false }' response.json`

The Lambda function is executed and reports a successful invoke on the Lambda processing queue. If Lambda is not able to add the event to the queue, the error message appears in the command output.

However, due to the exception error within the code, the function invocation will fail. Destinations then routes the invoke failure to the configured destination Lambda function. You can see the failed function invocation information in the [Amazon CloudWatch Logs](https://aws.amazon.com/cloudwatch/) for the Destination function including `"condition": "RetriesExhausted"`, along with the `requestPayload`, `errorMessage`, and `stackTrace`.

```
2019-11-24T21:52:47.855Z d123456-c0dd-4871-a123-a356cb1b3ba6 EVENT  
 {  
 "version": "1.0",  
 "timestamp": "2019-11-24T21:52:47.333Z",  
 "requestContext": {  
 "requestId": "8ea123e4-1db7-4aca-ad10-d9ca1234c1fd",  
 "functionArn": "arn:aws:lambda:sa-east-1:123456678912:function:event-destinations:$LATEST",  
 "condition": "RetriesExhausted",  
 "approximateInvokeCount": 3  
 },  
 "requestPayload": {  
 "Success": false  
 },  
 "responseContext": {  
 "statusCode": 200,  
 "executedVersion": "$LATEST",  
 "functionError": "Handled"  
 },  
 "responsePayload": {  
 "errorMessage": "Failure from event, Success = false, I am failing!",  
 "errorType": "Error",  
 "stackTrace": [ "exports.handler (/var/task/index.js:18:18)" ]  
 }  
 } 
```

### Destination-specific JSON format

*   For SNS/SQS, the JSON object is passed as the `Message` to the destination.
*   For Lambda, the JSON is passed as the payload to the function. The destination function cannot be the same as the source function. For example, if LambdaA has a Destination configuration attached for Success, LambdaA is not a valid destination ARN. This prevents recursive functions.
*   For EventBridge, the JSON is passed as the `Detail` in the PutEvents call. The source is `lambda`, and detail type is either `Lambda Function Invocation Result - Success` or `Lambda Function Invocation Result – Failure`. The resource fields contain the function and destination ARNs.

### AWS CloudFormation configuration

Destinations CloudFormation configuration is created via the following YAML.

```
Resources:   
 EventInvokeConfig:  
 Type: AWS::Lambda::EventInvokeConfig  
 Properties:  
 FunctionName: “YourLambdaFunctionWithEventInvokeConfig”  
 Qualifier: "$LATEST"  
 MaximumEventAgeInSeconds: 600  
 MaximumRetryAttempts: 0  
 DestinationConfig:  
 OnSuccess:  
 Destination: “arn:aws:sns:us-east-1:123456789012:YourSNSTopicOnSuccess”  
 OnFailure:  
 Destination: “arn:aws:lambda:us-east-1:123456789012:function:YourLambdaFunctionOnFailure” 
```

Conclusion
----------

AWS Lambda Destinations gives you more visibility and control of function execution results. This helps you build better event-driven applications, reducing code, and using Lambda’s native failure handling controls.

There are no additional costs for enabling Lambda Destinations. However, calls made to destination target services may be charged.

To learn more, see [Lambda Destinations](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html) in the [AWS Lambda Developer Guide](https://docs.aws.amazon.com/en_pv/lambda/latest/dg/welcome.html).

  
  
from Hacker News https://ift.tt/2ONjI1i