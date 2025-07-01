What's an EBS Volume?
- EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data, even after their termination
- They are bound to a specific availability zone
- Analogy: Think of them as a "network usb sitck"
- Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month
- It's a network drive (not a physical drive3)
	- It uses the network to communicate the instance, which means there might be a bit of latency
	- It can be detached from an EC2 instancve and attached to another one quickly