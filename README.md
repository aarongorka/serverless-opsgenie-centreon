# Serverless OpsGenie Centreon Integration
This Lambda function allows acknowledgements to propogate from OpsGenie to Centreon.

Requirements:
  * Network access to Centreon's web interface
  * Credentials for an account that can acknoweldge hosts and services in OpsGenie
  * OpsGenie configured for `Outgoing Amazon SNS` to the topic created by this serverless deployment

How it Works:
  * SNS messages are sent on every action in OpsGenie
  * Lambda is configured trigger on new SNS messages
  * If the message indicates that an incident has been acknowledged/closed, the Lambda function invokes a series of steps to log in to Centreon and submit an acknowledgement.
