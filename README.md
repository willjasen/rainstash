rainstash
=======

rainstash is an Amazon CloudFormation template for automating the setup of Resilio Sync in the Amazon cloud.

The following information must be supplied as parameters to rainstash:
* **AllowedSubnet** - the subnet allowed to managed the instance via SSH and HTTPS, IPs outside of this subnet will not be able to manage the instance, subnet should be in CIDR form (x.x.x.x/xx)
* **DeviceName** - the name of this device
* **FolderKey** - the encrypted read-only key used to maintain a copy of a folder upon stack setup, must begin with a F followed by 32 uppercase alphanumeric characters
* **InstanceType** - the EC2 instance type (i.e. - the size of the instance); see http://aws.amazon.com/ec2/instance-types/
* **KeyName** - the name of keypair used to setup instance; used to access instance via SSH
* **StorageNeededInGB** - the amount of storage, in gigabytes, needed
* **VolumeType** - the type of volume to configure, standard is the default for lowest cost
* **WebInterfacePassword** - the password for the web interface
* **WebInterfaceUsername** - the username for the web interface

rainstash and Amazon CloudFormation is completely free to use, however, Amazon may charge for the use of resources created with rainstash. rainstash uses the following cost-related services: EC2, S3, and data transfer.

Due to technical and security considerations, rainstash by default only accepts encrypted read-only folder keys for the best security. That encrypted data itself resides on an encrypted virtual disk volume, but the instance is meant to be ephimeral. If the EC2 instance where rainstash is running is shutdown or rebooted, data on that instance is not trivially recoverable. The workaround - the BitTorrent protocol and Resilio Sync are meant to be decentralized and distributed. Always have more than one copy of your folders, whether it's multiple rainstash stacks or running on your own hardware. Please keep this in mind!
