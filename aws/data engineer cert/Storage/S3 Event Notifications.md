- S3:ObjectCreated, S3:ObjectRemoved...
- Object name filtering possible (*.jpg)
- Use Case: generate thumbnails of images uploaded to S3
- Create as many "S3 Events" as desired
- event notifications typically deliver events in seconds but can sometimes take a minute or longer

IAM Permissions
For example:
- to send messages directly from S3 to SNS we need to attach a SNS resource (Access) policy directly to the sns topic
- Same thing for SQS
- Or a lambda function
- We don't use IAM Roles, rather Access Policies attached to the resource we are sending message to

With EventBridge:
- all events go to EventBridge no matter what. from here you can setup rules to send to over 18 different AWS services as destinations
	- with EventBridge:
	- there's advanced filtering options with JSON rules (metadata, object size, name...)
	- multiple destinations - ex Step Functions, Kinesis Streams / firehose
	- EventBridge Capabilities - Archive, Replay Events, Reliable Delivery