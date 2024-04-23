CloudWatch collects monitoring and operational data in the form of logs, metrics, and events, and visualizes it using automated dashboards so you can get a unified view of your AWS resources, applications, and services that run in AWS.


Monotoring:
      monitoring means weather it is kubernets application moniotoring,infrastrcure monitoring,Databse monitoring,


Metrics:

       metrics in the sense of memeory utiliztion and cpu utilization.

       it will allow you to get the reallife metrics:
         for example how many api requests did my application inside the ec2 instance received.(custom metrics)

           last 30 minutes what is the cpu utilization on my aws ec2 instance .

           can you give the metrics received by the api calls my application received.

notifications:
    if cpu utilization is reached 80% send notifcation to emails.
Alrams:

     if cpu utiliztion is reached 60% send an alaram.


Log insights:
   some of the activities its automatcally capture.

   one service communicate with another services so all these logs caputed here.


Custom metrics:

   By default cloudwatch track the cpu utilization.
   But cloud watch doesn't track the memeory utilization.if you want to track send the custom metrics to cloudwatch.

 
Cloud wathc can't directly provide the cost optimiztion and scaling ,it is intergrates with othe services.
 Cost optimization: 

     using lamda


Scaling:  
   if you are cpu utiliztion is already reached 80%,then cloudwatch will inform or send the notification  to autoscaling group.


IQ)you have an Ec2 instances,sometimes ec2 runs an issue for example consider some issue,if we reboot automatically it resolved,how you will be automated instead of doing manually?

   Set Up CloudWatch Alarms: Create CloudWatch Alarms to monitor the relevant metrics and trigger actions when the thresholds are breached. For example, you could create an alarm to trigger when CPU utilization exceeds a certain threshold for a sustained period.

    Create an SNS Topic: Set up an Amazon Simple Notification Service (SNS) topic to send notifications when the CloudWatch alarm is triggered. This allows you to receive alerts about the detected issues.
    
    Create an AWS Lambda Function: Write a Lambda function that will be triggered by the SNS notification. This function will contain the logic to reboot the EC2 instances in response to the detected issues.


Note:If you want to send your EC2 instance logs to cloudwatch ,need to install in EC2 cloudwatch log agent software.

Cloudwatch doesn't capute all the logs automatically for all the aws services.It will caputres some of the aws services only like Lamda,VPC flogs logs,AWs API gateway logs since in AWS every resource having its own logging mechanisms.


