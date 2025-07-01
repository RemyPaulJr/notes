What's an EBS Volume?
- EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data, even after their termination
- They are bound to a specific availability zone
- Analogy: Think of them as a "network usb sitck"
- Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month
- It's a network drive (not a physical drive)
	- It uses the network to communicate the instance, which means there might be a bit of latency
	- It can be detached from an EC2 instance and attached to another one quickly
- It's locked to an Availability Zone (AZ)
	- An EBS volume in us-east-1a cannot be attached to use-east-1b
	- to move volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs, and IOPS)
	- Billed for all the provisioned capacity
	- Can increase the capacity of the drive over time
---
There is a Delete on Termination attribute
- Controle the EBS behaviour when an EC2 instance terminated
	- By default, the root EBS volume is deleted (attribute enzabled)
	- 