Is anyone  know how to shutdown and start ec2 servers through script
And Trigger 9 am start and stop 6 pm



You need to use lambda function.. I haven’t implemented this, but heard people use function..

https://saturncloud.io/blog/how-to-auto-shutdown-and-start-amazon-ec2-instance/#:~:text=To%20do%20this%2C%20navigate%20to%20the%20Amazon%20EventBridge%20console%20on,Continue%20to%20create%20a%20rule”

saturncloud.io (https://saturncloud.io/blog/how-to-auto-shutdown-and-start-amazon-ec2-instance/)
How to Auto Shutdown and Start Amazon EC2 Instance | Saturn Cloud Blog
As a data scientist or software engineer you may be working with Amazon EC2 instances on a daily basis While EC2 instances are 



provider "aws" {
  region = "us-west-2"  # Replace with your desired region
}

resource "aws_cloudwatch_event_rule" "shutdown_rule" {
  name                = "EC2ShutdownRule"
  description         = "Schedule EC2 instance shutdown"
  schedule_expression = "cron(0 18 * * ? *)"  # Schedule to shutdown at 6 PM UTC (adjust for your timezone)
}

resource "aws_cloudwatch_event_target" "shutdown_target" {
  rule      = aws_cloudwatch_event_rule.shutdown_rule.name
  target_id = "ShutdownEC2Instance"
  arn       = "arn:aws:lambda:us-west-2:123456789012:function:shutdown_ec2_instance_lambda"  # Replace with your Lambda function ARN
}

resource "aws_cloudwatch_event_rule" "start_rule" {
  name                = "EC2StartRule"
  description         = "Schedule EC2 instance start"
  schedule_expression = "cron(0 9 * * ? *)"  # Schedule to start at 9 AM UTC (adjust for your timezone)
}

resource "aws_cloudwatch_event_target" "start_target" {
  rule      = aws_cloudwatch_event_rule.start_rule.name
  target_id = "StartEC2Instance"
  arn       = "arn:aws:lambda:us-west-2:123456789012:function:start_ec2_instance_lambda"  # Replace with your Lambda function ARN
}