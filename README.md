# 2.13_Serverless_2_Assignment

1. Does SNS guarantee exactly once delivery to subscribers?
    - Amazon Simple Notification Service (SNS) does not guarantee exactly once delivery of messages to subscribers.Instead, SNS offers at least once delivery, meaning that a message will be delivered to a subscriber at least once. However, there could be scenarios where a message might be delivered more than once, particularly when there are retries due to temporary issues, such as network failures or problems with the endpoint.

2. What is the purpose of the Dead-letter Queue (DLQ)? This a feature available to SQS/SNS/EventBridge.
    - A Dead-letter Queue (DLQ) is used to collect messages that can't be processed successfully by an application or service. In the context of Amazon SQS, SNS, or EventBridge, if a message cannot be successfully delivered to a subscriber (for example, due to application failure, timeouts, or any other issue), it can be moved to the DLQ for later analysis, investigation, or reprocessing. This allows the main queue or service to continue functioning without being blocked by problematic messages.

3. How would you enable a notification to your email when messages are added to the DLQ?
    - To enable email notifications when messages are added to a Dead-letter Queue (DLQ), we can integrate the DLQ with Amazon SNS to trigger notifications. Here’s how you can do that:

    1. Create an SNS Topic (use to send notification about DLQ messages)
    2. Subscribe to the SNS Topic (subscriber email)
    3. Create an EventBridge Rule (create rule to monitor messages in DLQ)
    4. Set the Target as the SNS Topic (SNS Topic created as target)
    4. Monitor DLQ Events (monitor even in subscriber email)

    
