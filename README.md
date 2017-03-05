rainstash
=======

rainstash is an Amazon CloudFormation template for automating the setup of Resilio Sync in the Amazon cloud.

The following information must be supplied as parameters to rainstash:
* **AllowedSubnet** - the subnet allowed to managed the instance via SSH and HTTPS, IPs outside of this subnet will not be able to manage the instance, subnet should be in CIDR form (x.x.x.x/xx)
* **DeviceName** - the name of this device
* **DiskEncryptionPassword** - the password used to encrypt the disk where btsync runs from and where Sync data is stored; this password should be sufficiently different from all other passwords
* **FolderKey** - the read-only or read/write shared folder key, used to join a folder upon stack setup, must be 33 characters and must be obtained from an existing shared folder
* **InstanceType** - the EC2 instance type (i.e. - the size of the instance); see http://aws.amazon.com/ec2/instance-types/
* **KeyName** - the name of keypair used to setup instance; used to access instance via SSH
* **SSLCertKeyPassword** - the password used to generate the self-signed SSL certificate; this password should be sufficiently different from all other passwords
* **StorageNeededInGB** - the amount of storage, in gigabytes, needed
* **SubnetCIDR** - the subnet within the VPC, subnet should be in CIDR form (x.x.x.x/xx), it must be a part of or all of VPCCIDR
* **VPCCIDR** - the subnet of the entire virtual private cloud, subnet should be in CIDR form (x.x.x.x/xx)
* **WebInterfacePassword** - the username for the web interface
* **WebInterfaceUsername** - the password for the web interface

rainstash and Amazon CloudFormation is completely free to use, however, Amazon may charge for the use of resources created with rainstash. rainstash uses the following cost-related services: EC2, S3, and data transfer.

Due to technical and security considerations, rainstash is designed to be ephimeral. If the EC2 instance where rainstash is running is shutdown or rebooted, data on that instance is not easily recoverable unless you know how to go about doing so. The workaround - the BitTorrent protocol and Resilio Sync are meant to be decentralized and distributed. Always have more than one instance, whether it's multiple rainstash stacks or running on your own hardware. Please keep this in mind!
