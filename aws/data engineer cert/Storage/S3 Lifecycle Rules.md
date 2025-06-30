Moving between Storage Classes
- You can transition objects between storage classes
- For infrequently accessed objects, move them to Standard IA
- For archive objects that you don't need fast access to, move them to Glacier or Glacier Deep Archive
- Moving Objects can be automated using Lifecycle Rules

Lifecycle Rules
- Transition Actions - configure objects to transition to another storage class
	- Move objects to Standard IA class 60 days after creation
	- And move to Glacier for archiving after 6 months
- Expiration Actions - configure objects to expire/delete after specified time
	- Access log files can be set to delete after 365 days
	- can be used to delete old version of files if vers