# Storage Services
## S3 - Simple Storage Service
* Similar to NAS
* Object Storage or File storage
* Distributes across atleast three availablity zone (Except 1A - least expensive)
* Support encryption and automatic data classification 
	* classfication for security
	* classfication for management of data - auto movement to glacier if its older than specfic months
* Big data analytics can run directly against stored data
* Very good for static website hosting

### S3 Terminology
* Buckets (100 default ) - Container to store object 
* Regions - You put bucket to region, ideally its near the user
* Objects - Synonymous to file
* Keys - logical name of objects
* Object URLs - Each object has URL assigned.
* Eventual consistency: Eventaully it will be consistent across all availablity zones.
* Tags: assigned to put permissions or lifecycle management (10 tags can be assigned to object)

### Common S3 Operations
* Creating and deleting buckets
* Writing/Reading/Deleting objects
* Managing object properties
* Listing Keys in bucket
### S3 Features
* Prefixes and delimiters -> S3 doesn't have folder hirearchy, its seperated by prefixes and delimiters
* Storage classes
	* Amazon S3 standard - $$$$
	* Amazon S3 Infrequent Access storage -$$$
	* Amazon S3 Reduced Redundancy Storage (RRS) -$$
	* Glacier - $
* Object life cycle management : Auto movement of objects from one storage to another stoarge class. You can use tags or prefixes to enable lifecycle at object level.
* Encryption
	* Server side encryption(storage security): encryption happens after upload
	* Client side encryption(Transit security): client encrypts and upload
* Versioning
	* by default its disabled
* MFA delete -> delete file can only be done using MFA. You can recover delete file only if versioning is enabled.
* Multipart upload -> Very large file can be uploaded in multiple streams and assembled at server side.
* Cross region replication -> It only replicates new data once replication is enabled.
* Logging
* Event notifications

### Getting data into S3
* API
* Amazon Direct Connect - VPN connect
* Storage Gateway
* Kinesis Firehose
* Transfer Acceleration - use any of edge location using cloud front, so when user uploads data anywhere in the world it gets optimized route to S3 bucket.
* SnowFamily
	* Snowball - Petabyte scale
	* Snowball Edge - 100 TB local storage - you can also run instances on it.
	* Snowmobile - Exabyte scale



## Glacier
* Archival data storage
* Very cheap to store data but retrieval is expensive
* Access methods
	* Expedited (3-5 mins) $$$
	* Standard (3-5 hours) $$
	* Bulk (5-12 hours) $
* Default 256 AES encryption
* S3 cold data can be automatically moved to Glacier
* Snow devices can be used to import data
* Storage Gateway can connect to Glacier
* Max limit: 1000 vaults/region

### Glacier Concepts
* Archives: Data which is archived
* Vaults: Place where archive resides.
* Vault locks
* Data retrieval 
	* Upto 5% is free, no rollover.
	* Vault can be configured to limit costs.

## Elastic Block Store (EBS)
 * EBS is bound to an instance
 * Used for durable storage in EC2 instances
 * Block-level storage from one AWS service to another (hard drive)
 * Similar to SAN
 ### EBS volume types
 * Magnetic (HDD)
 * SSD(Solid State Drive)
	* General Purpose (No guranteed IOPS) Max IOPS: 10000
	* Provisioned IOPS - Guranteed I/O operations per second, MAX: 32000
	* EBS-optimized instance should be used
	
#### comparison
<img src="https://github.com/Mayank-Mehta/AWS-CSA-Associate/blob/master/EBS_VolumeCharaterstics.PNG" />

### Protecting EBS Data
 * Snapshots: Recovery data or create another EBS volume
 * Volume recovery: Attaching volumes from one instance to another
 * Encryption 
 
## Elastic File System (EFS)
* EFS is shareable
* EFS is like NAS storage within the cloud for the cloud
* Hierarchical 
* Can be accessed through NFSv4
* Multiple EC2 instances can use EFS share.
* EFS is NOT supported on windows instances
* EFS share can be limited to a VPC

## Comparison
<img src="https://github.com/Mayank-Mehta/AWS-CSA-Associate/blob/master/StorageComparison.jpeg"/>
 
## Storage Gateway
* Software applicance that creates gateway on customers location
* Its virtual machine image that you download and install on local network and activate to connect with AWS client
* Three types of Gateway
	* File Based gateway - NFS - interface to S3 bucket
	* Volume Based Gateway - Internet SCSI protocol
	* Tape Based Gateway: backups on AWS cloud directly
	
<img src="https://github.com/Mayank-Mehta/AWS-CSA-Associate/blob/master/binaryTerminology.jpeg" />
