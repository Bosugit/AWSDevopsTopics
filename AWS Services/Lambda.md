In how many ways we can call lamda function:

     Generally we need to set metric ,need to put some threshold value based on this metric value is reached it will call SNS topic then Lamda function will triggered by the SNS topic.

          Metrics throshold value reached------>SNS Topic-------->Lambda.

    in second case we can directly call awsconfig rules ,no need through SNS.AWs confign rule directly call the lamda function when the rule is satified.