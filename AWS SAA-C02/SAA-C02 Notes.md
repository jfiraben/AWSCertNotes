# AWS Certified Solutions Architect – Associate
# Course Fundamentals and AWS Accounts
	• IAM is GLOBAL
	• IAM let's you create three different types of identity objects
		○ User
			§ Represent humans or applications that need access to the account
			§ Used when you can identify the individual thing that will login to that user (person/application)
		○ Group
			§ Collections of related users
		○ Role
			§ Can be used by AWS services or for granting external access to your account
			§ Roles are generally used when you want to grant access to services in your account to an uncertain number of entities
			§ Used when number of things is uncertain
	• IAM policy/policy document
		○ Objects/documents used to allow or deny access to AWS services
		○ Only works when attached to users/groups/roles
	• IAM has 3 main jobs
		○ Manage Identities - An IDP (ID provider)
		○ Authenticate - Prove you are who you claim to be
		○ Authorize - Allow or deny access to resources
			§ Based on policies associated with the identity that you authenticate with
	• No cost associated with creating users/groups/roles
	• Global service / global resilience
		○ Can cope with failure of large sections of AWS infrastructure
	• No direct control on external accounts or users
		○ Only controls local identities in your account
	• Identity Federation and MFA
		○ Lets you take identities you already have (active directory, facebook, google, twitter)
	• IAM user can't have more than 1 username and password
	• IAM user can have two access keys (can have 0, 1, or 2 but never more)
	• Access keys formed from two parts:
		○ Access Key ID
		○ Secret Access Key
			§ Longer and more complex
	• Given both the access key id and secret access key when you create a set of credentials
		○ AWS discards your secret access key (Not stored by AWS)
		○ AWS only keeps the Access Key ID (public)
	• If you're afraid your access keys have been leaked, you must delete the access key and secret access key then recreate it
		○ Gives you a brand new set of credentials (access key id and secret access key)
	• Rotating access keys
		○ Create brand new set and remove the old one
		○ Why IAM user has 2 sets
	• Terminating an instance is not reversible
	• Amazon Machine Image (AMI)
		• Can be used to create an EC2 instance or be created from an EC2 Instance
		• AMI -----> EC2 ------> AMI
		• Contains attached permissions
			§ Control which accounts can/can't use AMI
			§ Can be set as a public AMI - everyone allowed
			§ Owner of AMI is implicitly allowed to create EC2 instances from that AMI
				□ Control fully
			§ Can add explicit permissions to AMI
				□ Owner grants access to the AMI for specific AWS accounts
		• AMI contains the boot/root volume of the instance (C: drive)
		• AMI provides block device mapping
			§ Configuration that links the volumes that AMI has and how they're presented to the OS
			§ Determines which volume is the boot and which is the data volume
	• Connect to Windows instances using RDP
		• Uses port 3389
	• Connect to Linux instances using SSH
		• Uses port 22
		• You login to the instance using an SSH key pair

# Cloud Computing Fundamentals
	• 5 characteristics of cloud computing
		a. On-Demand Self-Service
			i. Provision and Terminate Using UI/CLI without human interaction
		b. Broad Network Access
			i. Access services over networks, on any devices, using standard protocols and methods
		c. Resource Pooling
			i. Economies of scale, cheaper service
		d. Rapid Elasticity
			i. Scale UP (OUT) and DOWN (IN) automatically in response to system load
		e. Measured Service
			i. Usage is measured. Pay for what you consume.
	• Public cloud is cloud environment available to the public
		○ AWS, Azure, Google cloud all public cloud platforms
		○ Must be classified as a cloud environment and also be available to the general public
	• Multi-cloud is using multiple cloud environments
		○ You've got cloud provider level resilience
			§ If one service fails (aws, azure, google), then you can rely on the others
		○ Suggested to use different services to manage the multiple cloud environments
			§ Third party tools must use tools that are in both cloud services
		○ Much simpler to put part of an environment in one cloud service and other part in another cloud service
	• Private Cloud - Solution dedicated to a business and run from business premises
		○ AWS - AWS outpost
		○ Azure - Azure Stack
		○ Google - Anthos
		○ Private cloud still needs to meet the 5 characteristics of cloud computing
		○ Using on-premises (real) cloud
	• Hybrid Cloud - using private cloud in conjunction with public cloud
		○ Only hybrid if you're using public cloud and private cloud cooperating together as a single environment
		○ Not hybrid if you're using public cloud with on-premise infrastructure
	• Infrastructure (Application) Stack is a collection of things that an application needs all stacked onto each other
	• Business must buy all parts of the application stack if using On-Premises system
		○ Very flexible but also very expensive
	• Data Center (DC) hosted
		○ Place your equipment inside building that's owned and controlled by the vendor
	• Infrastructure As A Service (IAAS)
		○ Provider manages the facilities, storage, networking, physical server, and virtualizations
		○ You consume the operating system
			§ You still need to manage the OS and anything above the OS (Container, Runtime, Data, Application)
		○ Generally pay per second, minute, hour fee for the virtual machine
			§ Pay when you use and don't pay when you don't use it
		○ One of the most popular cloud service models
		○ Substantial cost reduction
	• Platform as a service (PAAS)
		○ Aimed at developers that have an application they want to run and not the infrastructure
		○ Mainly used for developers
	• Software as a service (SAAS)
		○ You consume the application
	• Part of the stack is managed by you and the other part managed by the vendor
	
# AWS Fundamentals
	• Public and private services are all about the networking and not the permissions
	• Private zone has no direct connectivity to the public internet or the public AWS zone
		○ Anything created in AWS private zone is isolated by default
	• Can make a AWS private service a public service by taking part  of the private service and projecting it to the public zone
	• By default, private services can only be accessed from the same private networks or any on-premises networks connected to them
	• Each region is separated geographically
		○ Can place infrastructure in one region and it won't be affected by problems in that region
	• You have governance separation from the region you choose
		○ Geopolitical Separation - Different governance
	• Regions:
		○ Can use region code or region names
		○ Ex: ap-southeast-2 or Asia Pacific (Sydney)
	• Inside every region, AWS provides multiple availability zones (AZ)
		○ Given isolated infrastructure inside a region
		○ Availability Zone is a logical thing
	• Globally Resilient Services
		○ Service operates globally with a single database with its data replicated across multiple regions
		○ Would take the world to fail for globally resilient service to fail
		○ IAM and Route 53 are globally resilient
	• Region Resilient
		○ Operate in a single region with one set of data per region
		○ Operate as separate services in each region
		○ Replicate data to multiple AZ in that region
	• AZ resilient
		○ Services run from a single AZ
		○ If that AZ fails, the service will fail
	• Virtual Private Cloud (VPC) = a virtual network inside AWS
	• VPC is withini 1 account & 1 region
	• VPC by default is private and isolated unless you decide otherwise
	• VPC are regionally resilient
	• Two types of VPC: Default VPC and Custom VPC
		○ Can only have ONE default VPC per region
		○ Can have many different custom VPC per region
	• Custom VPC require configuration of everything end-to-end in detail
		○ Custom VPC by default is entirely private
		○ Must be configured to allow traffic between custom VPCs
	• VPC CIDR defines the start and end ranges of all available IP addresses that the VPC can use
	• Custom VPC can have multiple CIDR ranges
	• Default VPC only gets one CIDR range: 172.31.0.0/16
	• /20 subnet in each AZ in the region for Default VPC
	• Internet Gateway (IGW), Security Group (SG), and Network ACL (NACL)
		○ Security features to limit incoming and outgoing data transfers
	• Subnets assign public IPv4 addresses
	• Best practice not to use the default VPC
	
### EC2
	• EC2 = IAAS
		○ Provides Virtual Machines (instances)
	• EC2 is a private AWS service
		○ By default, it runs in the private AWS zone
		○ Configured to launch in a single VPC subnet
		○ Must configure public access if wanted
	• EC2 is AZ resilient - instance fails if AZ fails
	• Can choose different sizes and capabilities when creating an instance
	• EC2 offers on-demand billing - per second
	• Instances can use two types of storage:
		○ Local on-host storage or Elastic Block Store (EBS)
		○ EBS is network storage made available to the instance
	• Different states an instance can be in:
		○ Running
		○ Stopped
		○ Terminated
	• An instance is composed of CPU, memory, disk, and networking
	• When you create an SSH key pair, you download and keep the private copy of the key safe
		○ Public part is kept by AWS
		○ When used, the public key will be placed on the instance
		○ If the public/private part match, then you can connect to the instance

### S3 Simple Storage Service
	• S3 is a global storage platform
		○ Regional based/resilient
		○ Can be accessed anywhere with an internet connection
		○ Never leaves that region unless you configure it to
	• Can tolerate the failure of an AZ
	• Public service
		○ Unlimited data
		○ Multiple users
	• Perfect for hosting large amounts of data
	• Economical and accessed via UI/CLI/API/HTTP
	• Basically the default storage service in AWS
	• S3 delivers 2 main things:
		○ Objects
			§ Data that S3 stores
		○ Buckets
			§ Containers for objects
	• Objects
		○ Like files
		○ Made up of 2 main components and associated metadata
			§ Object Key
				□ Similar to a file name
			§ Value
				□ Data or contents of the object
				□ Can range from 0 bytes to 5 TB in size
				□ Can be an empty value or extremely large (5TB)
		○ Also have
			§ Version ID
			§ Metadata
			§ Access control
			§ Subresources
	• Buckets
		○ Created in a specific AWS region
		○ Data inside bucket has a primary home region
			§ Will not leave region unless configured to leave the region
		○ Blast Radius of a failure is the region the bucket is in
			§ Effect of data corruption will be contained in the region
		○ Bucket name needs to be globally unique
			§ Nobody else can use a bucket name within an AWS account
		○ Name of Aws bucket must be totally unique across all regions and AWS accounts
		○ Buckets can hold an unlimited amounts of objects
		○ An S3 bucket has no complex structure
			§ All objects are stored in the bucket at the same level
			§ Not like a file system where you can have folders within folders
		
### CFN Cloud Formation
	• Cloud Formation uses Templates
	• CFN templates either written in YAML or JSON
		○ Both achieve the same thing and it's easy to convert between them
	• Components of a template
		○ List of resources
			§ Tells CFN what to do
			§ Resources section of a template is the only mandatory part of a CFN template
		○ Description
			§ Free text field that let’s the author add a description
			§ If you have a description, it must immediately follow a template format version
				□ Template format version isn't mandatory unless you have a description
		○ Metadata
			§ Control the UI
				□ How things are presented through the AWS console UI
			§ Forces how the UI presents the template
		○ Parameters
			§ Can add fields which prompt the user for more information
		○ Mappings
			§ Allows you to create lookup tables
		○ Conditions
			§ Allow decision making in the template
			§ Can set certain things in the template that will only occur if a condition is met
			§ Two step process
				□ Create the condition
				□ Use condition
					® Used within the resources section of the CFN template
		○ Outputs
			§ Once template is finished, it can present outputs based on what's being created, updated, or deleted
	• Resources inside a CFN template are called LOGICAL RESOURCES
		○ Have properties that CFN uses to configure the resources in a certain way
		○ Logical resource has a type
			§ CFN uses type to know what to create
		○ Also has properties which CFN uses to configure the resources in a certain way
	• Template given to CFN, CFN will create a stack
		○ Stack contains all of the logical resources that the template tells it to contain
		○ Living representation of a template
	• For any logical resources in the stack, CFN makes a corresponding physical resource in your AWS account
		○ CFN job to keep the logical and physical resources in sync
		○ Stack created with logical resources inside which then is used to create physical resources in the AWS account
	• If you delete a stack, it's logical resources are deleted which forces CFN to delete the physical resources as well

### CloudWatch
	• Collects and manages operational data
	• Collects metrics, monitors metrics
		○ Metrics - AWS products, apps, on-premises
	• Some metrics are gathered natively by AWS
		○ CPU utilization on an EC2 Instance
	• CloudWatch Logs - AWS products, apps, on-premises
		○ Allows for the collection, monitoring, and actions based on logging data
			§ Windows event logs, linux server logs, firewall logs, any kind of logs that can be ingested
	• CloudWatch Events (Event Hub)
		○ Provides two features
			§ If an AWS service does something (EC2 service started, stopped, etc), CloudWatch events will generate an event that will perform another action
			§ Generate an event to do something at a certain time of day or certain days of the week
	• Namespace
		○ Container for monitoring data
		○ A way to separate things into different areas
		○ All AWS data goes into an AWS namespace = AWS/service
			§ EX: AWS/EC2
	• Metric is a collection of related data points in a time ordered structure
		○ EX: CPU usage, network in/out, disk IO
	• Datapoint
		○ Consists of a timestamp and a value
		○ 
	• Dimension
		○ Name value pairs that allows CloudWatch to provide different perspectives of things within a metric
		○ Dimensions separate datapoints for different things or perspectives within the same metric
	• Alarm
		○ Created and linked to a specific metric
		○ Based on how the alarm is configured, it will take action based on that metric
		
### High-Availability vs Fault-Tolerance vs Disaster Recovery
	• High-Availability (HA)
		○ Aims to ensure an agreed level of operational performance, usually uptime, for a higher than normal period
		○ About maximizing a system's online time
		○ Just about minimizing any outages
			§ User disruption is okay and can happen
		○ About fast or automatic recovery from issues
	• Fault-Tolerance (FT)
		○ Is the property that enables a system to continue operating properly in the event of the failure of some (one or more faults within) of its components
		○ If a system has one or more faults, it should continue to operate properly even while those faults are being fixed
		○ Operating through failure
		○ Can be more expensive than HA
	• Disaster Recovery (DR)
		○ A set of policies, tools, and procedures to enable the recovery or continuation of vital technology infrastructure and systems following a natural or human-induced disaster
		○ If HA and FT don't work, what happens then? That is DR
		○ Good DR plan means taking regular backups
			§ Must not store backups at the same site as your system
				□ If main site is damaged, the primary data and backups are damaged
			§ Backups needs to stored offsite and staff needs to know of these backups
		○ Must have copies of all processes available (logins to key systems, etc)
		○ Designed to keep the crucial/non-replaceable parts of your system safe

### Doman Name System (DNS)
	• DNS is a discovery service
		○ Translates machine into human and vice-versa
	• DNS is a huge scale database that's distributed, resilient, and hugely scalable
	• Zone file has DNS record that links the name (www.amazon.com) with the IP address
		○ Www -> 104.98.34.131
		○ Zone file is hosted by a DNS server that's known as a Nameserver (NS)
		○ DNS resolver server sits either on your internet router or the internet service provider
	• DNS client is generally a piece of software running on the OS of the device you're using
	• Job of DNS = Find nameserver which hosts a particular zonefile and then query that nameserver for a record that is in the zonefile
	• DNS Root = starting point of DNS
		○ Period at the end of the URL
			§ www.amazon.com.
		○ DNS Root/Root Zone
			§ Hosted on 13 special name servers known as root servers
			§ Root servers are operated by 12 different organizations
		○ Vendor of OS provides the root hints file
			§ Just a list of root servers / pointer to the DNS root servers
		○ Root Zone managed by IANA
			§ Internet Assigned Numbers Authority
				□ Manage the content of the Root Zone
		○ Root Servers host the Root Zone and IANA manage the Root Zone
	• Time To Live (TTL)
		○ Numeric value in seconds
	
### Route 53
	• AWS' managed DNS product
	• Provides two main services
		○ Allows to register domains
		○ Can host zone files for you on managed nameservers which it provides
	• Global Service with a Single Database
		○ Globally Resilient
		○ Can tolerate the failure of one or more regions
	• Has relationship with all of the major domain registries
	• MX record is how a server can find the mail server for a specific domain

# IAM, Accounts, and AWS Organizations
### IAM Identity Policies
	• IAM policies are attached to identities inside AWS
		○ Identities = IAM groups, users, roles
	• IAM policies are just a set of security statements to AWS
		○ Grants/denies access to AWS products and features to any identity which uses that feature
	• Priority of IAM policies:
		1) Explicit Deny
		2) Explicit Allow
		3) Implicit Deny (denied by default)
	• Inline policies granted to individual users
		○ Used for special or exceptional allow or deny
	• Managed policies are separate and can be assigned to individual users
		○ Reusable
		○ Low management overhead
			§ Changing JSON in managed policy changes for all users attached to it
		○ Two main types:
			§ AWS managed policies
				□ Created and managed by AWS
			§ Customer managed policies
				□ You can create and managed
				□ Define per exact requirements for the business

### IAM Users and ARNs
	• IAM users are an identity used for anything requiring long-term AWS access e.g. Humans, Applications, or Service Accounts
	• Principals make requests to IAM to interact with resources
		○ Needs to authenticate against an identity within IAM
		○ Authentication is the process of the principal proving that it's the identity it claims to be
			§ Username & password
				□ Usually with a human access via the console UI
			§ Access keys
				□ Human using AWS command line tool or an application
		○ Principal that goes through the authentication process known as an authenticated identity
	• Authentication is how a principal can prove to IAM that it is the identity it claims to be
	• Authorization is IAM checking the statements that apply to that identity and allowing/denying access
	• Amazon Resource Name (ARN)
		○ Uniquely identify resources within any AWS accounts

### IAM Groups
	• IAM Groups have no credentials and you cannot login to them
	• Only used to organize/manage IAM users
		○ Containers for users
	• IAM users can be a member of multiple IAM groups
	• Groups can have both inline and managed policies attached to them
	• IAM user can be a member of 10 groups
	• No limit for effective users in a single IAM group
	• Cannot have any nesting within groups (groups within groups)
	• Limit of 300 groups per account
		○ Can be increased with a support ticket
	• Policy resource can reference IAM users/roles by using the ARN
		○ Groups are not a true identity. They can't be referenced as a principal in a policy
	• Groups are just there to group up IAM users and allow permissions to be assigned to those groups which the IAM users inherit
	• Cannot login to groups and cannot reference them from resource policies
	
### IAM Roles
	• IAM roles are assumed…you become that role
	• Generally used on a temporary basis
	• Trust policy can reference identities in the same account or other AWS accounts
		○ Can allow anonymous usage of that role
		○ If a role gets assumed by something that's allowed to assume it, then AWS generates Temporary Security Credentials
			§ Made available to the identity that assumes the role
			§ Time Limited
			§ Once expired, the identity needs to assume them again
			§ Secure Token Service (STS) generates the temporary credentials
	• Roles can be useful with emergency situations
	• Break Glass situation:
		○ IAM user can assume an emergency role when absolutely required
		○ Only used under exceptional circumstances
	• Also good to use roles when adding AWS to an existing corporate environment
		○ Existing identity provider (e.g. Microsoft Active Directory)
		○ Can use Single Sign-On
	• External accounts cannot be used in AWS directly to access AWS resources
	• Giving permissions to an external identity provider and allowing external identities to assume a role is called Identity (ID) Federation
	• Web Identity Federation uses IAM roles
		○ Web Identities: Facebook, Google, Twitter
		○ Using Roles in this situation has advantages:
			§ No AWS credentials stored in the application (secure)
			§ Makes use of existing accounts that your customer already has
			§ Can scale to hundreds of millions of users+

### Organizations
	• Organization created on a Master account
		○ Can invite other AWS accounts to the master account to allow them to become part of the organization
		○ Other AWS accounts are the member accounts
		○ Organizations can have only one master account and zero or more member accounts
	• Organization Root
		○ Root container of the organization
		○ Can contain AWS accounts (member or master)
		○ Or
		○ Can contain other containers known as Organizational Unites (OU)
			§ Can contain member/master accounts as well as other nested Ous
	• Consolidated Billing
		○ Individual billing methods for the member accounts are removed and passed to the master account
		○ Master account becomes the payer account
		○ Covers usage of master and member accounts
		○ Removes financial administration overhead
		○ Consolidation of reservations and volume discounts
	• Service Control Policies (SCP)
		○ Let you restrict what AWS accounts in an Organizations can do
	• Can invite accounts to an organization and create new accounts
		○ No complicated invite process
		○ Create an account inside the organization and everything else is handled
	• Best practice is to have a single AWS account in the organization which is used for logins
		○ Typically have the master account clean and another member account that handles logins
		
### Service Control Policies (SCP)
	• Used to restrict what member accounts in the organization can do
	• Policy Document (JSON Document)
	• Attached to the root container
	• Can be attached to one or more organizational units or one ore more AWS accounts directly
	• Even if a master account has an SCP, it's never affected by SCPs
	• Avoid master account for anything in production
	• SCPs are account permissions boundaries
	• They limit what the account (including root) can do
	• They don't grant any permissions
		○ Defines the limit of what is and isn't allowed in an account
		○ ID's in the account still need permissions
		○ Can use SCPs to apply account-wide limits to services
	• Allow List
		○ Block by default and allow certain services
	• Deny List (Default)
		○ Allow by default and block certain services
	• FullAWSAccess = default policy when SCPs are enabled
		○ Service control policies essentially have no effect because nothing is restricted
		○ Allows all access on all resources
		○ Without FullAWSAccess policy, implicit deny is there
	• Deny Lists are much lower admin overhead

### CloudWatch Logs
	• Public Service - usable from AWS or on-premises
		○ Even other cloud platforms (network connectivity and access)
	• Store, Monitor, and Access logging data
	• AWS integrations
		○ EC2, VPC Flow Logs, Lambda, CloudTrail, Route53, and more
	• Use Unified CloudWatch Agent to log data for anything outside of AWS services
	• Can generate metrics based on logs = Metric Filter
	• Log Events are stored inside log streams
		○ Log Events are a timestamp and message
	• Log Groups are containers for multiple log streams for the same type of login
		○ Log Groups store configuration settings (retention settings and permissions)
		○ Metric filters are defined in log groups
			§ Reviewing any log events for any log streams in that log group looking for certain patterns
			§ When detected, the metric filters increment a metric, and trip an alarm
	• Each log stream is an ordered set of log events for a specific source for a specific thing

### CloudTrail
	• Logs API actions that affect AWS accounts
		○ Stop an instance
		○ Create security group
		○ Create/delete S3 bucket
	• Logs API calls/activities as a CloudTrail Event
	• 90 days stored by default in Event History
	• Enabled by default - no cost for 90 day history
	• To customize the service, create 1 or more Trails
	• Cloudtrail events can be 1 of 2 types:
		○ Management Events
			§ Provide info about management operations that are performed on resources in your AWS account
			§ Known as Control Plain Operations
		○ Data Events
			§ Contain info about resource operations performed on/in a resource
			§ E.G. Objects being uploaded to S3
	• By default, CloudTrail only logs management events
	• Trail logs events for the AWS region that it's created in
		○ REGIONAL SERVICE
	• Can create a trail that's a 1 region trail or ALL regions
	• AWS services either log an event in the region it's in or they log to us-east-1
	• Trail can store events in a definable S3 bucket
		○ Can store events indefinitely
		○ Stored as compressed JSON files
		○ Can be passed by any tool capable of reading these standard format files
	• CloudTrail can be integrated into CloudWatch Logs
	• Can create an organizational trail
		○ Create trail from master account
		○ Can store all info from all accounts within that organization

# Simple Storage Service (S3)
### S3 Security (Resource Policies and ACLs)
	• S3 is private by default
	• The only identity which has any initial access to S3 by default is the account root user of the account which created it (owns that bucket)
		○ Any permissions must be explicitly granted
	• Using an S3 bucket policy (resource policy)
		○ Like identity policies, but attached resources instead of identities (to a bucket)
		○ Resource perspective permissions
	• You can only attach identity policies to identities within your own account
		○ Can only control security in your account
	• Resource policies can allow/deny same or different accounts
	• Resource policies can allow/deny anonymous principals
		○ Can open a bucket to the world by referencing all principals
	• ID policies have to be attached to a valid identities within AWS
	• Resource policies have a principal part to the policy
		○ Principal part defines which principals are affected by the policy
		○ Identity policies don't have this because it's expected that the account is the principal
	• Access Control List (ACL)
		○ Apply security to buckets or objects
		○ A Subresource
		○ Legacy (don't recommend by AWS)
			§ Prefer to use bucket/identity policies
		○ Inflexible & simple permissions
	• Block Public Access
		○ Only apply to an anonymous principal
		○ Function as a final failsafe
		
### S3 Static Hosting
	• Static Website Hosting allows access via HTTP - e.g. Blogs…
	• Enable it and set an Index and Error document
	• When enabled on a bucket, AWS creates a website endpoint (where it can be reached)
		○ Name automatically generated
		○ Can use custom domain for a bucket, but the name of the bucket matters (must match the domain)
		○ Custom Domain via R53 - BucketName Matters
	• S3 much cheaper than compute services for the storage and delivery for any media
	
### Object Versioning and MFA Delete
	• Object Versioning controlled at a bucket level
	• Starts off in a disabled state
		○ You can enable versioning on a bucket but you can NEVER switch back to disabled
		○ You can suspend it though and then enable it afterwards
	• Without versioning, the object is identified by an object key (it's name) which is unique inside the bucket
	• Versioning lets you store multiple versions of objects within a bucket. Operations which would modify objects GENERATE A NEW VERSION.
	• Versioning being off on a bucket means the ID will be NULL
	• You can always specify a version in order to get something other than the latest/current version
	• Delete Marker = new version of that object. Makes an object look deleted but actually just hidden
		○ Deleting the delete marker undeletes the object and returns the object back to normal
		○ In order to delete an object you must delete the object and specify the version you want to remove
	• Object versioning cannot be switched off - only suspended
	• Space is consumed by ALL VERSIONS
	• You are billed for ALL VERSIONS
	• Only way to 0 costs is to delete the bucket
	• When you suspend objects, you are still billed for those objects because they are still present (just hidden)
	• MFA Delete enabled within the versioning configuration on a bucket
		○ MFA is required to change bucket versioning states
		○ MFA is required to fully delete versions
		○ Need to provide the serial number (MFA) and Code passed with API CALLS
		
### S3 Performance Optimizations
	• Single PUT Upload
		○ When you upload an object to S3, it's uploaded as a single blob of data as a single stream
		○ Single data stream to S3
		○ If a stream fails, the entire upload fails
			§ Only recovery requires a full restart
		○ Speed and reliability  = limit of 1 stream
		○ Limited to 5GB of data as a maximum
	• Multipart Upload
		○ Improves the speed/reliability of uploads to S3 by breaking data up into individual parts
		○ Minimum size for using Multipart Upload is 100MB
			§ Cannot use multipart upload with less than 100MB
		○ Upload can be split into a maximum of 10,000 parts and can range in size between 5MB and 5GB
			§ Last part can be smaller than 5MB if needed
		○ Parts can fail and be restarted
		○ Transfer rate = speeds of all parts
	• S3 Accelerated Transfer (OFF)
		○ Uses the network of AWS edge locations
			§ Located in lots of convenient locations globally
		○ Defaulted to switched off and restrictions for enabling it
		○ Restrictions for enabling it:
			§ Bucket Name cannot contain any periods 
			§ Needs to be DNS compatible in it's naming
		○ When enabled, the uploads will travel to the nearest, best performing edge location
		○ Transferred using the AWS global network
		
### Encryption
	• Approaches:
		○ Encryption at Rest
			§ Designed to protect against physical theft/tampering
				□ E.g. user with laptop
			§ Used fairly commonly in cloud environments
		○ Encryption in Transit
			§ Aimed at protecting data while it's being transferred between two places
			§ Generally used when multiple individuals/systems are involved
	• Concepts
		○ Plaintext
			§ Unencrypted data
				□ Can be text, images, applications
			§ Data that you can load into an application and immediately use
		○ Algorithm
			§ Piece of code (math) that takes plaintext and encryption key to generate encrypted data
				□ E.g. Blowfish, AES, RC4, DES, RC5, and RC6
		○ Key
			§ Password but can be much more complex
		○ Ciphertext
			§ When an algorithm takes plaintext and a key, it generates ciphertext
				□ Isn't always text data
				□ Encrypted data
		○ Decryption
			§ Opposite of encryption
	• Symmetric Encryption
		○ Both ends agree on an algorithm to use (e.g. AES-256)
		○ Sender generates a symmetric encryption key
		○ Algorithm used accepts the symmetric encryption key and the data
			§ Outputs ciphertext (encrypted data)
		○ With Symmetric encryption, the same key is used for the encryption and decryption processes
		○ Problem that you need the key in order to decrypt the ciphertext, but you shouldn't send the key across the network to the destination
	• Asymmetric Encryption
		○ Both sender and receiver agree on an asymmetric algorithm to use
		○ Asymmetric encryption keys consist of a public and private key
		○ Public key can be used to create ciphertext which can only be decrypted by the private key
		○ Sender needs the receivers PUBLIC key
			§ Sender can use the public key and plaintext in order to encrypt and create ciphertext
		○ When the receiver gets the ciphertext, they can use their private key and ciphertext with the algorithm to decrypt back to plaintext
		○ Generally used where two or more parties are involved (and when those parties have never met)
		○ Requires much more processing
	• Generally, asymmetric encryption is used initially to agree on a symmetric key to use, then that key is used from that point on
	• Signing uses asymmetric keys
		○ Using private key to sign the message
		○ Receiver uses the senders public key to prove whether the message was signed using the sender's private key
		○ Public key can verify whether it's corresponding private key was used to sign something
	
### Key Management Service (KMS)
	• Regional and Public Service
		○ Separate product in each region
	• Create, store, and manage cryptographic keys
	• Capable of handling both symmetric and asymmetric keys
	• Capable of performing cryptographic operations (encrypt, decrypt)
	• Keys never leave KMS - Provides FIPS 140-2 (L2)
		○ FIPS 140-2 = US security standard
		○ FIPS 140-2 Level 2
	• Customer Master Key (CMK)
		○ Used by KMS within cryptographic operations
		○ Container for the actual physical master keys
		○ CMK is logical - contains key ID, creation date, key policy, description, and a state of the key (active or not)
		○ Backed by physical key material
			§ Can be generated by KMS or imported into KMS
		○ CMKs can be used for up to 4KB of data
	• User runs the CreateKey operation to create a Customer Master Key (CMK)
		○ KMS stores this CMK and manages it
		○ CMK are never stored in a persistent form when not encrypted
		○ KMS encrypts the CMK before it's stored persistently on disk
		○ User then can make an encrypt call to KMS and specifying the key to use and the data to encrypt
			§ If user has permissions to use the CMK, KMS will encrypt that data
		○ User can then decrypt the data using the CMK
			§ User only needs to call decrypt and pass the ciphertext into KMS
		○ KMS decrypts the CMK, uses that key to decrypt the ciphertext, then returns that data back to the user
		○ User must have permissions to use KMS (CreateKey, Encrypt, Decrypt)
			§ Role separation - different people/roles are given different access rights
	• Data Encryption Keys (DEK)
		○ KMS generates these using a customer master key (CMK)
		○ GenerateDataKey - works on data larger than 4KB in size
		○ DEK linked to a specific CMK
			§ KMS does not store the DEK in any way
			§ It provides it to you then discards it
			§ KMS doesn't actually perform the encryption/decryption of data using the DEK
				□ The user does this
		○ KMS provides two versions of the DEK
			§ Plaintext version
				□ Encrypt the plaintext using the plaintext version of the DEK
				□ Generates ciphertext for that data
				□ Then you discard the plaintext version
			§ Ciphertext version
			§ You would then store the encrypted copy of the DEK with the encrypted data (side by side)
			§ You can then pass the encrypted data encryption key back to KMS and use the customer master key that was used to generate it. This will decrypt it
			§ You can then use the decrypted data encryption key that is returned and use that to decrypt the data
			§ You then discard the decrypted data encryption key
	• Customer master keys (CMKs) are isolated to a region and never leave
		○ Stored within the KMS service specific to that region
		○ Never leave the KMS service
	• AWS managed or Customer managed CMKs
		○ AWS managed are created automatically by AWS (S3 for example)
		○ Customer managed CMKs created by customer
	• Customer managed keys are more configurable
		○ Can edit the key policy
			§ Allow other AWS accounts access to the CMKs
	• CMKs support key rotation
		○ AWS managed keys cannot disable this
		○ Customer managed keys this rotation is optional
	• CMK contains the current backing key and all previous backing keys caused by rotating that material
	• Alias
		○ Shortcut to a particular CMK
		○ Per region
	• Key Policies (resource)
		○ Every CMK has a key policy
		○ Customer managed, you can adjust this policy
		
### S3 Encryption
	• Buckets themselves are not encrypted. Objects are.
	• You define encryption at an object level
	• S3 supports two levels of encryption:
		○ Client-side encryption
			§ Encrypted by the client before they ever leave
			§ Data is ciphertext the entire time
			§ Data is seen in scrambled form and stored in scrambled form
		○ Server-side encryption
			§ Three types available:
				□ Server-side encryption with customer-provided keys (SSE-C)
					® Customer is responsible for the encryption keys used for encryption/decryption
					® S3 service manages the actual encryption/decryption process
					® Customer needs to generate and manage the keys that the S3 process uses
					® S3 takes the plaintext and encryption key to create encrypted data and a hash (one way)
					® The hash is taken of the key
					® The key is then discarded and the encrypted object and the hash are stored
					® You need the key to decrypt the object
				□ Server-side encryption with Amazon S3-managed keys (SSE-S3) (AES256)
					® S3 manages encryption and keys
					® User provides the plaintext
					® When an object is uploaded to S3 using SSE-S3 encryption, it's encrypted using a key that's unique to each and every object
					® S3 uses master key to encrypt the unique key
					® Both the encrypted object and the encrypted unique key are stored in S3
					® Very little control over how these keys are used
						◊ Master key and the unique keys are outside of the user's control
					® This is the default type of encryption
					® Presents three significant problems:
						◊ If you're in a regulatory environment where you need to control the keys used and the access to those keys
						◊ If you need to be able to control the rotation of the key material
						◊ If you need role separation
							} If a full S3 administrator, they can decrypt and view data 
							} This may not be allowed within certain organizations (financial)
				□ Server-side encryption with Customer Master Keys (CMKs) stored in AWS Key Management Service (SSE-KMS)
					® Much like SSE-S3
					® KMS handles the customer master key (CMK)
						◊ Used to create one unique data encryption key for every object
					® You can create a customer managed CMK as well
					® Gives fine-grained control over the master key being used and it's rotation
					® CloudTrail shows any calls made against the CMK
				□ 
		○ Refer to encryption at rest
	• Encryption at rest comes standard with S3
	• Bucket Default Encryption
		○ Applies only when you don't specify anything explicitly on a bucket
		○ When uploading, you can specify AES256 for SSE-S3 or aws:kms for SSE-KMS
	
### S3 Object Storage Classes
	• Default storage class = S3 Standard
		○ Objects are stored across at least 3 Azs
		○ Can cope with multiple AZ failure
		○ Provides 11 9s of durability = 99.999999999% durability for 10,000,000 objects, 1 object loss per 10,000 years
		○ Replication over 3 AZ's and Content-MD5 Checksums and Cyclic Redundancy Checks (CRCs) are used to detect and fix any data corruption
		○ When objects are stored, a HTTP/1.1 200 OK response is provided by the S3 API Endpoint
		○ With S3 standard, you are billed a GB/m fee for data stored. A $ per GB charge for transfer OUT (IN is free) and a price per 1,000 requests. No specific retrieval fee, no minimum duration, no minimum size
		○ You don't get any discounts but it's the most balanced class of storage
		○ Makes data accessible immediately
			§ S3 standard has a 'milliseconds' first byte latency and objects can be made publicly available
		○ Should be used for frequently accessed data which is important and non-replaceable
	• S3 Standard Infrequent Access (IA)
		○ Same as S3 Standard except:
			§ S3 Standard-IA has a per GB data retrieval fee, overall cost increases with frequent data access
			§ Minimum duration charge of 30 days
				□ Objects can be stored for less, but the minimum billing always applies
			§ Minimum capacity charge of 128KB per object
		○ Should be used for long-lived data which is important or irreplacable but where data access is infrequent
		○ Don’t use it for lots of small files, temporary data, data that's constantly accessed, data which isn't important or can be easily replaced
	• S3 One Zone-IA
		○ Similar to S3 Standard Infrequent Access
		○ Still the retrieval fee, 30 day billed storage duration, 128KB minimum capacity charge per object
		○ Only stored in 1 AZ within the region
		○ Cheaper access to storage but don't have the multi-AZ storage option
		○ One Zone-IA does not provide the multi-AZ resilience model of Standard or Standard-IA. Instead only one AZ is used within the region
		○ You still get the 11 9s of durability = 99.999999999% durability
			§ Multiple copies of the data but only in one AZ
		○ Should be used for long-lived data which is NON-CRITICAL and REPLACEABLE and where access is INFREQUENT
		○ Don't use this for your only copy of data or for critical data or data which is frequently accessed/changed
	• S3 Glacier
		○ Same 3 AZ architecture as S3 Standard / IA
		○ Same 11 9s durability
		○ Objects stored in Glacier class are cold objects
			§ Not ready for use
			§ Not immediately available and cannot be made public
			§ Just a pointer to that object
		○ Objects cannot be made publicly accessible
			§ Any access of data (beyond object metadata) requires a retrieval process
		○ Data in glacier is retrieved to S3 Standard-IA temporarily
			§ Expedited (1-5 minutes)
			§ Standard (3-5 hours)
			§ Bulk (5-12 hours)
			§ Faster = more expensive
		○ First byte latency = minutes or hours
		○ 40KB min size
		○ 90 day min duration
		○ Used to store archival data where frequent or realtime access isn't needed. Minutes-hours retrieval.
	• S3 Glacier Deep Archive
		○ Approximately 1/4 price of Glacier
		○ 40KB min size and 180 Day min duration
		○ Objects cannot be made publicly accessible
			§ Any access of data (beyond object metadata) requires a retrieval process
		○ Data in Glacier Deep Archive is retrieved to S3 Standard-IA temporarily
			§ Standard (12 hours)
			§ Bulk (up to 48 hours)
		○ First byte latency = hours or days
		○ Restore time is much longer than Glacier
		○ Archival data that rarely if ever needs to be accessed - hours or days for retrieval.
			§ E.g. legal or regulation data storage
	• Intelligent Tiering
		○ Different from all other storage classes
		○ Contains two different sub-storage classes
		○ Stored with frequent or infrequent access tiers
		○ Frequent access like S3 standard and infrequent access like S3 Standard-IA
		○ Intelligent-tiering monitors and automatically moves any objects not accessed for 30 days to a low cost infrequent access tier
		○ As objects are accessed, they are moved back to the frequent access tier. There are no retrieval fees for accessing objects, only a 30 day minimum duration
		○ Has a monitoring and automation cost per 1,000 objects. The frequent access tier costs the same as S3 standard, the infrequent the same as Standard-IA
		○ Should be used for long-lived data, with changing or unknown patterns
### S3 Lifecycle Configuration
	• Set of rules which you apply to a bucket
		○ Consist of actions that apply to an entire bucket or a group of objects
			§ Transition Actions
				□ Change the storage class of whatever objects are affected
			§ Expiration Actions
				□ Delete whatever objects are effected after a certain period of time
	• Transitions flow downward ONLY
	• Most transitions will step down

### S3 Replication
	• Cross-Region Replication (CRR) is the process used when Source and Destination are in different AWS regions
	• Same-Region Replication (SRR) is used when the buckets are in the same region.
	• Both types of replication support different and same AWS account replication
	• 
	• Options:
		○ Can select all objects or a subset of objects
		○ Can also select which storage class - default is to maintain
		○ Can define the ownership - default is the source account
			§ Can override where the destination is the owner
		○ Replication Time Control (RTC)
			§ Adds 15 minute guaranteed SLA
	• Considerations:
		○ Not retroactive and Versioning needs to be ON
			§ Can enable versioning in the process of replicating
		○ One-way replication process only
			§ Source to destination
		○ Capable of handling objects that are unencrypted, SSE-S3, and SSE-KMS (with extra configurations)
		○ Requires that the source bucket owner needs permissions to objects
		○ NO system events, glacier, or glacier deep archive
			§ Only user events are replicated
		○ NO DELETES
			§ Deletes not replicated
	• Why use replication?
		○ SRR - Log Aggregation
		○ SRR - PROD and TEST sync
		○ SRR - implement resilience with strict sovereignty
		○ CRR - global resilience improvements
		○ CRR - latency reduction
	
### S3 Presigned URLs
	• Can be used for downloads (GET) or uploads (PUT)

### S3 Select and Glacier Select
	• Ways you can retrieve part of objects rather than the entire object
	• S3 can store HUGE objects (up to 5TB)
	• You often want to retrieve the entire object
	• Retrieving a 5TB object takes time and uses the 5TB of data
		○ Filtering at the client side doesn't reduce this
	• S3/Glacier select let you use SQL-Like statements to select part of the object, pre-filtered by S3
	• CSV, JSON, Parquet, BZIP2 compression for CSV and JSON
	• Without S3 Select, filtering occurs in-app full amount retrieved and billed by S3
	• SQL-like expression provided to S3 select, selection happens at the S3 service
	• With S3 select, filtering occurs on the service the data delivered by S3 is pre-filtered
		○ Up to 400% faster and 80% cheaper
	
# Virtual Private Cloud Basics
### VPC Sizing and Structure
	• VPC considerations
		○ What size should the VPC be?
		○ Are there any networks we can't use?
		○ Be mindful of ranges of VPCs, Cloud, On-premises, partners, and vendors
		○ Try to predict the future
		○ VPC structure - tiers and resiliency (Availability) Zones
	• Where possible, avoid using the default VPC
	• VPC minimum /28 (16 IP), maximum /16 (65456 IPs)
	• Avoid common ranges
	
### Custom VPCs
	• Regional Service - All AZs  in the region
	• Regionally isolated
	• Nothing IN or OUT without explicit configuration
	• Flexible configuration - simple or multi-tier
	• Hybrid networking - other cloud and on-premises
	• Can pick default or dedicated tenancy
	• Can use IPv4 private CIDR blocks and public IPs
	• Allocated 1 primary private IPv4 CIDR block
	• Min /28 (16 IP) Max /16 (65,536 IP)
	• Optional secondary IPv4 blocks
	• Optional single assigned IPv6 /56 CIDR block
	• VPC offer DNS provided by Route53
	• VPC 'Base IP + 2' address
	• enableDnsHostnames - gives instances DNS names
	• enableDnsSupport - enables DNS resolution in VPC
	
### VPC Subnets
	• AZ resilient
	• A subnetwork of a VPC - within a particular AZ
	• 1 subnet created within a specific AZ within that region
		○ 1 subnet -> 1 AZ, 1 AZ - > 0+ subnets
	• IPv4 CIDR is a subset of the VPC CIDR block
	• Cannot overlap with other subnets
	• Optional IPv6 CIDR (/64 subset of the /56 VPC - space for 256)
	• Subnets can communicate with other subnets in the VPC
		○ Isolation is at the perimeter of the VPC
	• Reserved IP addresses (5 in total)
		○ E.x. 10.16.16.0/20 (10.16.16.0 -> 10.16.31.255)
		○ Network Address (10.16.16.0)
			§ First address of any subnet is the network address (the starting of the range) and cannot be used
		○ 'Network + 1' (10.16.16.1) - VPC Router
			§ Moves data between subnets and in and out of the VPC if it's configured
		○ 'Network + 2' (10.16.16.2) - Reserved (DNS*)
		○ 'Network + 3' (10.16.16.3) - Reserved future use
		○ Broadcast Address 10.16.31.255 (Last IP in Subnet)
	• Dynamic Host Configuration Protocol (DHCP)
		○ How computing devices receive IP addresses automatically
	• DHCP Options Set - Configuration object applied to VPC
	• Options defined at a subnet level:
		○ Auto Assign Public IPv4
		○ Auto Assign IPv6
	
### VPC Routing and Internet Gateway
	• VPC router
		○ available in every VPC by default
		○ Runs in all the AZ that VPC uses
		○ In every subnet.. 'network + 1' address
		○ Routes traffic between subnets in that VPC
		○ Controlled by 'route tables' each subnet has one
			§ Route tables defines what the VPC router will do once data leaves that subnet
		○ A VPC has a main route table - subnet default
			§ If you don't associate a route table with a vpc, it uses the default
		○ Route table is simply a list of routes
		○ Route Tables
			§ Local target means the destination is in the VPC itself
			§ VPC router can forward the traffic directly
			§ Local routes can never be updated
			§ Attached to 0 or more subnets, subnet has to have a route table, and it's either the main route table of the VPC or a custom one that you create, controls what happens to data as it leaves the subnet(s) that the route table is associated with, local routes are always there and uneditable and match the VPC IPv4/IPv6 CIDR range, higher prefix values are more specific and take priority
	• 1 Internet Gateway (IGW) will cover all AZs in a region
		○ Region resilient gateway attached to a VPC
		○ 1 VPC = 0 or 1 IGW, 1 IGW = 0 or 1 VPC
			§ 1 to 1 both ways
		○ Runs from the border of the VPC and the AWS public zone
			§ Runs from within the AWS Public Zone
		○ Gateways traffic between the VPC and the internet or AWS public zone (S3, SQS, SNS, etc)
		○ Managed - AWS handles the performance
	• Operating System is not aware of the public IPv4 address, only the IGW is aware of this
	• All IPv6 addresses AWS uses are natively, publicly routable
	• Bastion Host = Jumpbox
		○ An instance in a public subnet inside a VPC
		○ Incoming management connections arrive here
		○ Then access internal VPC resources
		○ Often the only way IN to a VPC
	
### Network Access Control Lists (NACLs)
	• Can be thought of as firewalls which surround VPC subnets
	• NACL associated with a subnet and not a resource
	• Formed with two sets of rules: inbound and outbound
	• Rules processed in order
	• Low rule numbers processed first
	• Processing stops as soon as one rule applies (for that particular piece of traffic)
	• Always a default implicit deny
		○ Cannot be edited or removed
	
### Security Groups
	• Security Groups (SGs) are another security feature of AWS VPC ... only unlike NACLs they are attached to AWS resources, not VPC subnets.
	• SGs offer a few advantages vs NACLs in that they can recognize AWS resources and filter based on them, they can reference other SGs and also themselves.
	• But.. SGs are not capable of explicitly blocking traffic - so often require assistance from NACLs
	• Security Groups are assigned to a network resource (specifically to a network interface of an AWS product)
	•  Security groups are stateful (opposite of NACLs)
		○ Only one rule is required for inbound communication. Return traffic is automatically included in the allow.
		○ Security Groups understand AWS logical resources
		○ SGs can reference other SGs and even themselves
	• Have a hidden implicit deny
	• Cannot explicitly deny
	• NACLs often used in conjunction with SGs to do EXPLICIT DENY
	
### Network Address Translation (NAT) and NAT Gateways
	• Can adjust IP packets by changing their source/destination addresses
	• IP masquerading - hiding CIDR blocks behind one IP
	• Private IPv4 addresses running out
	• Gives private CIDR range outgoing internet access
	• NAT gateway has a translation tabel which records information (src/dst IP, port, etc)
	• NAT Gateways
		○ Needs to run from a public subnet
		○ Uses Elastic IPs (Static IPv4 Public)
		○ AZ resilient service (HA (high availability) in that AZ)
		○ For region resilience - NATGW in each AZ… Route Table (RT) in for each  AZ with that NATGW as target
		○ Managed, scales to 45 Gbps, $ Duration, and Data Volume
	• NATGW is highly available in the AZ that it's in, but if the whole AZ fails, there is no failover
	• If you use NAT Instance, you need to disable Source/Destination Checks in order to avoid packets being dropped
		○ Can be disabled via the console UI, CLI, or API
	• Not preferred to use EC2 as a NAT instance
	• For maximum availability, you need a NAT gateway in every AZ you use
	• NAT Instance can be cheaper, especially at high volume of data
	• NAT Instance cost is more predictable
	• NATGW is not free tier eligible
	• NATGW cannot be used as a Bastion host or for port forwarding because you cannot connect to it's OS
	• NATGW don't support security groups whereas NAT Instance does and can use Network ACLs
	• Can only use NACLs with NATGWs
	• NAT isn't required for IPv6
	• All IPv6 address in AWS are publicly routable
	• The Internet Gateway works with ALL IPv6 Ips directly
	• NAT Gateways don't work with IPv6
	• ::/0 Route + IGW for bi-directional connectivity
	• ::/0 Route + Egress-Only Internet Gateway - Outbound Only
		○ Use it when you want to give an IPv6 Instance ONLY outbound access to the public internet and AWS public zone
	
# Elastic Compute Cloud (EC2) Basics
### Virtualization 101
	• Virtualization = running more than 1 OS on a piece of physical hardware (server)
	• Small part of OS runs in Privileged Mode (kernel) in order to directly interact with the hardware of the system
	• Applications run in User Mode (unprivileged mode) cannot directly interact with the hardware
		○ Must go through the OS
	• Hypervisor performs process  known as Binary Translation
		○ Any privileged operations which guest OS attempts to make, is intercepted and translated on-the-fly in software by the hypervisor
		○ Binary Translation in Software means guest OS don't need any modifications
	• Para-virtualization
		○ Guest OS modified to make privileged calls in the guest OS into user calls instead of directly calling on the hardware = Hypercalls
		○ Uses paravirtualized drivers in the guest os
	• Hardware Assisted Virtualization
		○ Hardware itself becomes virtualization aware
		○ CPU contains capabilities so hypervisor can perform the support
	• Single Route - IO Virtualization (SR-IOV)
		○ Hardware becomes virtualization aware
		○ Allows network card or any add-on card to present itself as several mini cards
		○ Presented to the OS as real cards dedicated for the Guest OS use
		○ No translation needed by the hypervisor
		○ In EC2 - This is ENHANCED NETWORKING
		
### EC2 Architecture
	• EC2 instances are virtual machines (OS + resources)
	• EC2 instances run on EC2 Hosts (physical servers)
		○ Shared hosts are shared across different AWS customers
			§ Every customer using shared hosts are isolated from each other
			§ Default
		○ Dedicated hosts
			§ You're paying for the entire physical host
			§ Not shared with other customers
	• EC2 is an AZ resilient service
		○ Hosts = 1 AZ
			§ AZ fails, host fails, instances fail
	• EC2 hosts run inside a single AZ
	• Instance Store is temporary and the storage for the EC2 Host
	• EC2 Hosts have storage and data networking
	• Elastic Block Store runs inside a specific AZ
	• If an AZ in AWS experiences issues, it impacts many different things (EBS, volume, ec2 hosts, etc)
	• Instances stay on a host until two things happen:
		○ Host fails or is taken down for maintenance by AWS
		○ If instance stopped then started
		○ If both those happen, the instance will be relocated to another host
		○ Host will also be in  the same AZ
		○ Instances don't move AZs natively
	• You cannot connect network interfaces or EBS storage located in one AZ to an EC2 instance in another AZ
		○ EC2 and EBS are both AZ services and isolated to the AZ
		○ Cannot cross AZs
	• What's EC2 Good For?
		○ Traditional OS + Application compute need
		○ Long-Running compute needs
			§ EC2 designed for persistent, long-running compute requirements
		○ Server style applications
		○ Applications or services that need burst or steady-state load requirements
		○ Monolithic application stacks
		○ Migrated application workloads or DISASTER RECOVERY
	• EC2 tends to be the default compute service in AWS
	• EC2 TIED DOWN TO A PARTICULAR AZ
	
### EC2 Instance Types
	• Choosing an instance type influences the following:
		○ Raw CPU, Memory, Local Storage Capacity, and Type
		○ Resource ratios
		○ Storage and data network bandwidth
		○ System architecture / Vendor
			§ Arm
			§ X86
			§ Intel CPU / AMD CPU
		○ Additional features and capabilities
	• EC2 Categories
		○ General Purpose
			§ Default
			§ Diverse workloads, equal resource ratio
		○ Compute Optimized
			§ Media processing, High Performance Computing, Scientific Modelling, Gaming, Machine Learning
		○ Memory Optimized
			§ Processing large in-memory datasets, some database workloads
		○ Accerlated Computing
			§ Hardware GPU, field programmable gate arrays (FPGAs)
		○ Storage Optimized
			§ Sequential and Random IO
			§ Scale-out transactional databases, data warehousing, Elasticsearch, analytic workloads
	• R5dn.8xlarge
		○ R = Instance Family
		○ 5 = Instance Generation
		○ 8xlarge = Instance Size
			§ Determines how much memory and CPU the instance has allocated
		○ dn = additional capabilities
			§ Can vary
			§ Can also not have this field

### Storage
	• Direct (local) attached storage
		○ Storage on the EC2 host
		○ Physical disk directly attached to the device
		○ Generally super fast but suffers from problems
			§ If disk, hardware fails the storage can be lost
			§ If instance moves between hosts, the storage can be lost
	• Network attached storage
		○ Volumes created and attached to device over the network
		○ Volumes delivered over the network (EBS)
		○ Highly resilient and separate from instance hardware
	• Ephemeral storage
		○ Temporary storage
		○ Can't rely on to be perisistent
		○ Ex. Instance Store - physical storage attached to host
	• Persistent storage
		○ Permanent storage
		○ Lives on past the lifetime of the instance
		○ Ex. Network attached storage delivered by EBS
	• Categories of Storage
		○ Block storage
			§ Volume presented to the OS as a collection of blocks
			§ No structure provided
			§ Mountable and bootable
			§ Presented as a number of blocks - no structure beyond that
			§ Comes in the form of HDD/SSD
			§ Has no in-built structure - up to OS to create and mount a file system
		○ File Storage
			§ Presented as a file share
			§ Has structure
			§ Mountable but NOT bootable
			§ OS doesn't have low-level access to the storage
		○ Object Storage
			§ Collection of objects, flat
			§ NOT Mountable and NOT bootable
			§ Simply store objects, no structure
			§ Object can be anything and can have attached metadata
			§ Super scalable
	• Storage Performance
		○ IO (block) size
			§ Size of the blocks of data that you're writing to disk
		○ IOPS
			§ Measures the number of input/output operations the storage can support in a second
			§ How many reads/writes to a disk a storage system can accommodate in a second
		○ Throughput
			§ Rate of data the storage system can store on a particular piece of storage
		○ IO (block) size x IOPS = Throughput
		
### Elastic Block Storage (EBS) and Volume Types
	• EBS
		○ Allocate block storage (volumes) to instances
		○ Volume = ONE AZ
			§ high availability/resilient in that AZ
		○ Different physical storage types available (SSD/HDD)
		○ Varying levels of performance (IOPS, throughput)
		○ Billed as GB/m (some have IOPS component)
	• Volume Types
		○ General Purpose SSD (gp2)
			§ Focus on IOPS as the dominant performance attribute
			§ Should be default for almost all normal usage
			§ Baseline Performance
				□ 3 IOPS/GiB (min 100, max 16000)
			§ 
		○ Provisioned IOPS SSD (io1)
			§ Focus on IOPS as the dominant performance attribute
			§ IOPS can be controlled separately from size
			§ 50:1 IOPS to GiB ratio..vs.. 3:1 GP2
				□ IOPS to size
				□ Performance level always guaranteed
			§ 
			§ Multi-attach - can attach to multiple instances at the same time
				□ Not available with gp2
			§ High IOPS = io1
			§ Latency or picking performance separate from the size = io1
			§ Small volume sizes with high IO requirements = io1
		○ Throughput Optimized HDD (st1)
			§ Focus on Throughput (MiB/s)
			§ Great Value
			§ Great Throughput
			§ 500 GiB - 16 TiB
			§ Cannot be used for instance boot volumes
				□ NO boot volume
			§ Use if you care more about the price than raw performance and throughput
			§ Designed for frequently accessed, throughput intensive workload
				□ Big data, data warehouse, log processing, streaming style performance
			§ 40 MB/s baseline per TiB
			§ Burst of 250 MB/s per TiB
			§ Max throughput 500MB/s
		○ Cold HDD (sc1)
			§ Focus on Throughput (MiB/s)
			§ Great Value
			§ Great Throughput
			§ 500 GiB - 16 TiB
			§ Cannot be used for instance boot volumes
				□ NO boot volume
			§ Use if you care more about the price than raw performance and throughput
			§ Uses a performance, bucket-style architecture (gp2) based on throughput
			§ Starts off at 1 TiB of credit per TiB of volume size
			§ 12 MB/s baseline per TiB
			§ Burst of 80 MB/s per TiB
			§ Max throughput 250 MB/s
	• Dominant Performance Attribute
		○ Each volume type in EBS focuses on a specific area (block size, IOPS, throughput)
### EC2 Instance Store
	• Provides Block Storage devices
	• Physically connected to one EC2 Host
		○ Each host has its own instance store volumes that are isolated to that specific host
	• Instances on that host can access that instance store
	• Highest storage performance in AWS
	• Included in the instance price
	• Attached ONLY at launch
		○ Cannot be attached later
	• Instance store volumes are Ephemeral volumes (temporary storage)
	• When instances move hosts, they're given new, blank ephemeral volumes
	• If a physical volume fails, then the instance store fails
	• Achieve much higher levels of throughput and IOPS when using Instance Store vs EBS
	• D2 (instance) = 3.5 GBps read and 3.1 GBps write
	• I3 (instance) = 16 GB/second of sequential throughput
	• Instance Stores have more IOPS and Throughput than EBS
	• Can't use Instance Store for anything that requires Secure Persistent Data
	
### EC2 Instance Store vs EBS
	• When to use EBS
		○ Highly Available (inside that AZ) and Reliable storage
		○ Persist independently from the EC2 instance
			§ Exists separately from EC2
			§ Stopping and starting an instance does not destroy data
		○ Clusters - Multi-attach feature of io1
			§ Allows you to attach an io1 volume to multiple instances at the same time
			§ Create clustered, shared volumes
		○ Region Resilient Backups
			§ Snapshots
		○ Require up to 64,000 IOPS and 1,000 MiB/s per volume
		○ Require up to 80,000 IOPS and 2,375 MB/s per instance
	• When to use Instance Store
		○ Value - included in instance cost
		○ More than 80,000 IOPS and 2,375 MB/s
		○ Temp Storage volumes
		○ Stateless services
			§ Servers hold nothing of value (accounts, sessions)
			§ Access to temporary space to manipulate data
		○ Rigid lifecycle link between storage and instance
			§ Guarantee no data is left behind when an instance is stopped/terminated
	• If performance level can be met by EBS, then default to EBS
	
### EBS Snapshots
	• Efficient way to backup EBS volumes to S3
	• Migrate data on EBS volumes between AZs
	• Snapshots are incremental volume copies to S3
		○ Data that snapshots store are region resilient
	• The first snapshot is a full copy of 'data' on the volume
		○ Just copies the data used
	• Future snaps are incremental
		○ Store changes since the last snapshot
	• Volumes can be created (restored) from snapshots
	• Snapshots can be used to move EBS volumes between AZ and Regions
	• New EBS volume = full performance immediately
	• Snaps restore lazily - fetched gradually
		○ Transfers data in the background and takes time
	• Requested blocks are fetched immediately
	• Force a read of all data immediately
	• Fast Snapshot Restore (FSR) - immediate restore
		○ Up to 50 snaps per region
		○ Set on the Snapshot and the AZ
	• Snapshot consumption and billing
		○ Billed using a Gigabyte-month metric
		○ Used data and NOT allocated data
		○ Incremental

### EBS Encryption
	• By default, no encryption is applied
	• Provides at-rest encryption for volumes and snapshots
	• EBS uses KMS and a Customer Master Key (CMK)
		○ AWS CMK is called aws/ebs
		○ Can also be a customer managed CMK that you create and manage yourself
	• All data is ciphertext on the physical disk using the decrypted Data Encryption Key (DEK)
	• If EC2 Instance moves from one host to another, the decrypted DEK that was stored on the EC2 host is discarded
		○ In order for the ciphertext stored in EBS to be used again, the encrypted DEK needs to be decrypted and loaded onto another EC2 Host
	• If snapshot taken from encrypted volume, the snapshot also uses the DEK
		○ If volume created from that snapshot, it also uses that same DEK
		○ All remain encrypted and share the DEK
		
### Network Interfaces, Instance IPs, and DNS
	• EC2 Instance starts off with one network interface = Elastic Network Interface (ENI)
		○ Primary ENI
		○ Can attach 1 or more separate ENIs that can be in different subnets but must be in the same AZ
		○ Eni can have the following:
			§ Mac address
			§ Primary IPv4 Private IP address
			§ 0 or more secondary Ips
			§ 0 or 1 public IPv4 address
			§ 1 elastic IP per private IPv4 address
			§ 0 or more IPv6 addresses
			§ Security Groups
			§ Source/Destination Checks
		○ Secondary ENIs have all of the above
	• Can attach secondary ENIs and move them to other EC2 instances
	
### Amazon Machine Image (AMI)
	• AMI's can be used to launch EC2 instances
	• Can be AWS or community provided
	• Can launch instances from marketplace (can include commercial software)
	• AMIs are regional with unique ID
	• AMIs can only be used in the region they're in
	• AMI controls permissions (public, your account, specific accounts)
	• You can create an AMI from an EC2 instance you want to template
	• AMI Lifecycle:
		○ Launch
		○ Configure
		○ Create Image
		○ Launch
	• When you make an AMI, the snapshots are taken and referenced inside the AMI using a BLOCK DEVICE MAPPING
		○ BDM = table of data with snapshot device ID and other data
	• When launching an AMI, the snapshots are used to create new EBS volumes in the AZ you're launching the instance into
		○ Uses the same Device ID contained in the Block Device Mapping

### Instance Billing Models
	• Four ways to pay for instances
		○ On-Demand Instances
			§ Instances have an hourly rate
			§ Billed while in running state
			§ Billed in seconds (60s minimum) or Hourly
			§ Default pricing model (balanced)
			§ No long-term commitments or upfront payments
			§ Great for new or uncertain application requirements
			§ Good for short-term, spiky, or unpredictable workloads which CAN'T TOLERATE ANY DISRUPTION
		○ Spot Instances
			§ Spot pricing offers up to 90% off vs On-Demand
			§ A spot price is set by EC2
				□ Based on spare capacity
			§ You can specify maximum price you'll pay
			§ If spot price goes above your max price, instances terminate
			§ Applications that have flexible start and end times
			§ Apps which only make sense at low cost
			§ Apps which can tolerate failure and continue later
		○ Reserved Instances
			§ Up to 75% off vs On-Demand in exchange for a commitment
			§ 1 or 3 years, all upfront, partial upfront, no upfront
			§ Reserved in region, or AZ with capacity reservation
			§ Scheduled reservations (specify for a given time period)
			§ If you have a known steady state usage, can lock down cheaper pricing with reserved
			§ Lowest cost for apps which can't handle disruption
			§ Need reserved capacity
		○ Dedicated Hosts

### Instance Status Checks and Auto Recovery
	• 1st status check is the system status and the 2nd is the instance status
	• Failure of system status check:
		○ Loss of System Power
		○ Loss of Network Connectivity
		○ Host Software issues
		○ Host Hardware issues
	• Failure of instance status check:
		○ Corrupted file system
		○ Incorrect Instance Networking
		○ OS Kernel Issues
	• Auto Recovery moves instance to new hosts, starts with exact same configuration

### Horizontal and Vertical Scaling
	• Scaling = systems need to grow/shrink when responding to increases/decreases of load placed upon by customers
		○ Adding or removing resources to a system
	• Vertical Scaling
		○ Resizing an instance
		○ Each resize requires a reboot = customer disruption
			§ Can generally only scale during pre-agreed times
		○ Larger instances often carry a price premium
		○ There is an upper cap on performance = maximum instance size
		○ No application modification required
		○ Works for ALL applications - even monoliths
	• Horizontal Scaling
		○ Adds more instances
		○ More than 1 running copy of application running on several instances
			§ Load balancer
		○ Sessions are everything
		○ Requires application support OR off-host sessions
			§ Servers are stateless (dumb instances of the application)
			§ Session externally hosted somewhere else
		○ No disruption when scaling
		○ No real limits to scaling
			§ Can just keep adding instances
		○ Often less expensive - no large instance premiums
		○ More granular
			§ Can scale by percentages
		
### Instance Metadata
	• EC2 service provides data to instances
		○ Can be used to configure/manage an instance
	• Accessible inside ALL instances
	• The IP address to access the instance metadata is http://169.254.169.254
		○ http://169.254.169.254/latest/meta-data/
	• All info about the environment the instance is in
		○ Networking
		○ Authentication information
		○ User-data
	• Metadata service does not have authentication and not encrypted
	• NOT AUTHENTICATED OR ENCRYPTED
	• Can restrict access with firewall rules
	
# Containers and ECS
### Intro to Containers
	• Containers don't have to have the OS on them
	• They have a container engine that's on the Host OS
	• With virtualization, the virtualized hosts all have the OS on them, taking up resources
	• Docker images are made up of multiple, independent layers
	• Created initially by using a dockerfile
	• Dockerfile - used to build docker images. Each step creates filesystem layers
	• Images are created from a base image or scratch
	• Every change you make in a docker image is layered on top of the existing layers
	• Images contain read-only layers, changes are layerd onto the image using a differential architecture
	• Docker container has an additional read/write layer
	• Each layer is differential and only stores the changes made against it stored in the layers below
	• Container Registry
		○ Hub of container images
		○ E.g. Docker Hub
	• Docker Host
		○ Servers running container engines
		○ Can run many containers based on 1 or more images
	• Dockerfiles are used to build images
	• Containers are portable - self-contained and always run as expected
	• Containers and images are lightweight
		○ Parent OS used
		○ Filesystem layers are shared
	• Container only run the application and environment it needs
	• Provides much of the isolation VMs do
	• Ports are 'exposed' to the host and beyond
	• Application stacks can be multi-container
	
### Elastic Container Service (ECS) Concepts
	• Managed, container-based compute service
	• Runs in two modes:
		○ EC2
		○ Fargate (SP?)
	• ECS lets you create a cluster
	• Clusters are where your containers run from
	• Elastic Container Registry (ECR) is AWS container registry/hub
	• Container Defintion
		○ Tells ECS where your container image is
		○ Tells what port the container uses
		○ Provides just enough info about the single container that's being defined
	• Task Definition
		○ Represents a self contained application
		○ Store the resources used by the task
			§ CPU
			§ Memory
		○ Stores compatibility
		○ Stores the task role
			§ IAM role that a task can assume
			§ Gains credentials to interact with AWS resources
			§ Best practice way of giving containers within ECS permissions to access AWS products and services
	• ECS Service
		○ Configured using a service definition
	• Container Definition defines the image and ports used for the container
	• Task Definition - Security (Task Role), Container(s), Resources
	• Task Role - IAM Role which the TASK assumes
	• Service - How many copies, High Availability, Restarts
		○ Generally what you'll use in business critical application
	
### ECS Cluster Mode
	• EC2 Mode
		○ EC2 Instances are used to run the containers
		○ Auto Scaling Group (ASG) handle horizontal scaling for EC2 instances
		○ ECS uses container registries (ECR, Docker Hub, etc) where your containers are stored
		○ Expected to manage the number of container hosts inside the ECS cluster
	• Fargate Mode
		○ Don't have to manage EC2 instances
		○ No service to manage
		○ Fargate Shared Infrastructure
			§ Offered to all users of fargate
			§ Gain access to resources from a shared pool
			§ Tasks are injected into the VPC
			§ Tasks and services are running from the shared infrastructure platform and injected into the VPC
				□ They're given network interfaces inside the VPC
		○ Hosts costs, capacity, and availability all handled by the Fargate shared infrastructure
		○ Pay for container resources that you use
	• EC2 vs ECS (EC2) vs Fargate
		○ If you use containers then use ECS
		○ Large workload - price conscious then use EC2 Mode
		○ Large workload - overhead conscious then use Fargate
		○ Small / Burst workloads then use Fargate
		○ Batch / Periodic workloads then use Fargate
		
# Advanced EC2
### Bootstrapping EC2 with User Data
	• Bootstrapping = scripts run when instance is launched to automate tasks
		○ Allows a system to self-configure or process self-configuring steps
	• Bootstrapping allows EC2 Build Automation
	• Allows to direct an EC2 instance to do something when launched
		○ Software installations
	• Enabled using User Data
		○ Accessed via the meta-data IP
		○ http://169.254.169.254/latest/user-data
	• Anything in User Data is executed by the Instance OS
	• ONLY ON LAUNCH
	• EC2 doesn't interpret (validate), the OS needs to understand the User Data
	• EC2 service provides User Data to the EC2 Instance when it's launched
	• User Data
		○ It's opaque to EC2
			§ It's just a block of data
		○ It's not secure
			§ Don’t use it for passwords or long term credentials (ideally)
		○ Limited to 16 KB in size
			§ Need to pass in script for anything larger
		○ Can be modified when instance stopped
		○ But only executed once at launch
			§ After launch stage, User data is only used for passing data in
	•  Commands to view all commands executed from User Data
		○ Cd /var/log
		○ Cat cloud-init-output.log
		○ Shows all commands run during launch
	• When giving User Data to EC2, it needs to be encoded in Base64
		○ Done when using console UI
		○ When using CloudFormation Template, you need to specify
			§ Fn::Base64: !Sub |
				□ !Sub |
					® Substitutes variables in User Data with parameters entered in the template
	• AMI Baking
		○ Creating an AMI that already has software installed, configurations applied, etc
		
### Enhanced Bootstrapping with CFN-INIT
	• Much more complex than User Data
	• Cfn-init
		○ Helper script installed on EC2 OS
		○ Simple configuration management system
		○ Procedural (User Data) vs Desired State (cfn-init)
		○ Can make sure packages are installed, manipulate groups and users, download/extract sources, create files with ownerships/permissions, run commands, and control services on an instance
		○ Passed into the instance as part of the User Data
		○ Provided with directives via Metadata and AWS::CloudFormation::Init on a CFN resource
	• Works with stack updates
	• CloudFormation CreationPolicy and Signals
		○ CreationPolicy
			§ Something added to logical resource within CFN template
			§ CFN waits for signal from the resource itself
			§ Signal reports to cloudformation if cfn-init was successful or not
			§ Resource will move into complete state or show an error
			
### EC2 Instance Roles
	• IAM Roles are best practice ways that AWS services can be granted permissions to AWS Services on your behalf
	• Allowing a service to assume a role, grants the service permissions that that role has
	• IAM Role has a Permissions policy attached to it
	• IAM role allows EC2 Service to Assume it
	• InstanceProfile
		○ Wrapper around an IAM role
		○ InstanceProfile is attached to the Instance
		○ Temp Credentials delivered via instance meta-data
	• Application running inside an instance uses these credentials stored in the meta-data
	• Credentials are inside the instance meta-data
		○ Iam/security-credentials/role-name
		○ Automatically rotated - always valid
	• Should always be used rather than adding access keys into an instance
	• CLI tools will use ROLE credentials automatically

### AWS Systems Manager (SSM) Parameter Store
	• Anyone with access to an  instance can access User Data
		○ Parameter store is a way around this
	• Lets you create parameters for storage for configuration and secrets
	• Can store 3 different types of parameters:
		○ String
		○ StringList
		○ SecureString
	• Can store license codes, database strings, full configs, and passwords
	• Uses hierarchies and versioning
	• Can store plaintext parameters (db connection strings and db users) and Ciphertext (passwords, sensitive info)
	• Has public parameters (made available by AWS)
		○ Latest AMIs per region
	• Tightly integrated with IAM for permissions
	• If parameters are encrypted, then KMS is involved
	• Changes to parameters can create events
	
### System and Application Logging on EC2
	• Cloudwatch provides metric logging on the external face of an EC2 Instance
	• CloudWatch is for metrics
	• CloudWatch logs is for logging
	• Neither natively capture data inside an instance
	• CloudWatch Agent is required for the above and needs configuration and permissions
	• Runs on the OS and captures OS visible data to send to CloudWatch and CloudWatch logs
	• Best practice is to create an IAM role with permissons to interact with CloudWatch Logs
		○ Then attach that role to the EC2 instance
		○ Gives permissions to access CloudWatch service
	
### EC2 Placement Groups
	• Three types of placement groups for EC2:
		○ Cluster (performance)
			§ Pack isntances close together
		○ Spread (resilience)
			§ Keep instances separated
		○ Partition (parallel app)
			§ Groups of instances spread apart
	• Cluster
		○ Achieve the absolute highest level of performance inside EC2
		○ Launch all instances within that group at the same time so AWS allocates all capacities at the time
		○ Best Practice: use same type and size
		○ Must belong to the same AZ
		○ Group locked to that AZ when they're launched
		○ All members have direct connections to each other
		○ Can achieve 10 Gbps single stream (vs 5 Gbps)
		○ Lowest latency and max packets per second possible in AWS
		○ Cannot span AZ
			§ One AZ only
		○ Can span VPC peers
			§ But impacts performance
		○ Requires a supported instance type
		○ Use the same type of instance (not mandatory)
		○ Launch at the same time (not mandatory)
		○ 10Gbps single stream performance (only way to do this)
		○ Use case:
			§ performance, fast speeds, low consistent latency
	• Spread
		○ Ensure max availability and resilience for an application
		○ Can spread multiple AZs
		○ Placed on separate, isolated infrastructure racks in each AZ
		○ 7 instances per AZ
			§ Isolated infrastructure limit
		○ Provides the highest level of availability and resilience
		○ Each instance runs from a different rack
		○ Not supported for Dedicated Instance or Hosts
		○ Use Case:
			§ Small number of critical instances that need to be kept separate from each other
	• Partition
		○ Similar architecture to Spread Placement Groups
		○ Designed when you have more than 7 instances per AZ but you still need to separate them into different fault domains
		○ Specify the number of partitions you want to divide with a max of 7 per AZ
			§ Each partition inside placement group has its own racks so no sharing between partitions
			§ Guarantee of no infrastructure sharing between partitions
			§ Can launch as many instances into each partitions
		○ Can see which instances are in which partition
		○ You need to administer partition placement
		○ Important Notes:
			§ 7 partitions per AZ
			§ Instances can be placed in a specific partition or auto placed
			§ Partition placement groups are not supported for Dedicated Hosts
			§ Great for HDFS, HBase, and Cassandra
		○ Allows application (cassandra, etc) to be aware of the distribution that the instances are being placed into
			§ Apps can use this to improve resilience
### Dedicated Hosts
	• EC2 Host dedicated to your AWS account
	• Specific family
		○ a1, c5, m5
	• No instance charges because you pay for the host
		○ Can pay On Demand or Reserved Options
	• Host hardware has physical sockets and cores
	• A1 = 1 Socket and 16 Cores
	• R5 = 2 Socket and 48 Cores
	• AMI Limits
		○ RHEL, SUSE Linux and Windows AMIs are not supported
	• Amazon RDS instances are not supported
	• Placement groups are not supported for Dedicated Hosts
	• Hosts can be shared with other Organizational Accounts using Resource Access Manager (RAM) product
	
### Enhanced Networking and EBS Optimized
	• Enhanced Networking
		○ Uses Single Route - IO Virtualization (SR-IOV)
			§ NIC is virtualization aware
		○ No charge - available on most EC2 types
		○ Higher I/O and Lower host CPU usage
		○ More bandwidth
		○ Higher packets-per-second (PPS)
		○ Consistent lower latency
		○ Either enabled by default or available on most modern EC2 types
	• EBS Optimized Instances
		○ Option set on per instance basis
		○ EBS = Block storage over the network
		○ Historically network was shared for data and EBS
		○ EBS optimized means dedicated capacity for EBS
			§ Faster speeds possible with EBS
			§ Storage doesn't impact performance of EBS
		○ Most instances support and have enabled by default
		○ On some older instances, it's supported but enabling costs extra

# Route 53 - Global DNS
### Route 53 Public Hosted Zones
	• A Route 53 Hosted Zone is a DNS database for a domain
		○ e.g. animals4life.org
	• Public = Hosted on R53 provided public DNS Servers
	• Globally resilient (multiple DNS Servers)
	• Created with domain registration via R53
		○ Can be created separately
	• Public/private hosted zones store DNS records
		○ A
		○ AAAA
		○ MX
		○ NS
		○ TXT
	• Hosted Zones are what the DNS system references
		○ Authoritative for a domain
			§ e.g. Animals4Life.org
	• Client submits DNS Query to Route 53 resolver. Route 53 Resolver checks Hosted Zone database for the zonefile. IP Address sent back to client through Route 53 Resolver
	
### Route 53 Health Checks
	• Health checks can monitor health of servers periodically
	• If server is unhealthy, it can remove that from the zonefile
	• Health checks are separate from, but are used by records
	• Health checkers located globally
	• Can check anything accessible over the public internet
	• Occur every 30 seconds by default but can be increased to every 10 seconds at a cost
	• One of three types:
		○ TCP
			§ Tries to establish TCP connection with endpoint
		○ HTTP/HTTPS
			§ Tries to establish TCP connection with endpoint and endpoint needs to respond with 200/300 series http status code
		○ HTTP/HTTPS with String Matching
			§ Tries to establish TCP connection with endpoint and endpoint needs to respond with 200/300 series http status code
			§ Body of response also checked for a string that user specifies (occurs in first 5120 bytes of the response)
	• Marks as either healthy or unhealthy based on the checks that have been conducted
	• Can be checks of three types
		○ Endpoint
		○ CloudWatch Alarm
		○ Checks of Checks (calculated)
		
### Route 53 Routing Protocols
	• Simple
		○ Can configure standard DNS records with no special Route53 routing
		○ Default
		○ Single record has 1 or more values. Client querying will get back all values and pick one at random to use
	• Failover
		○ Create two records of the same name/type
		○ One set to be primary and other is secondary
		○ Use health checks so each record has an associated health check
		○ Always use primary as long as it's healthy
	• Weighted
		○ Create multiple records of same name within each hosted zone
		○ You provide the weighted value and that determines which record is returned
		○ If any record has a failed health check, process occurs again until another record is selected which isn't failing the health check
		○ Can use for migrations by adjusting weights and gradually moving over
	• Latency-based
		○ Create multiple records in hosted zone with same name/type
		○ Each record has a region that it corresponds to (specified by user)
		○ Picks the healthy record with the lowest latency
		○ Used to provide customers with best user-experience
	• Geolocation
		○ Delivering results to queries which match  location of customers
		○ Can be set to default, continent, or country
		○ Tries to match the country first, then the continent, then the default as a catch all. If no matches for country, then continent, then default
		○ Designed to offer localized content to customers
	• Multi-value
		○ Similar to Simple but each records with same name can have each individual health checks
		○ When one fails a health check, it can be removed from the results. Simple does not remove from results

### Route 53 Failover to S3 and Private Zones
	• Private hosted zone only accessible from the VPC that  it's associated with
	
# Relational Database Service (RDS)
### Database Refresher
	• Relational (SQL) vs Non-Relational (NoSQL)
	• Structure in and between tables of data = Rigid Schema
	• Schema defines names, values, and types of data stored and where
	• NoSQL = not one single thing. It's different models
		○ Anything that's not relational
		○ Generally a much more relaxed schema (weak or no schema)
		○ Relationships between tables handled differently
	• Every row has to have a unique value (primary key)
	• Join table has composite key
		○ Key formed from two parts
		○ Key in its entirety must be unique
	• Table schemas and relationships are defined in advance
	• Key-Value database (NoSQL)
		○ Consists of sets of keys and values
		○ No Schema or Structure
		○ Scalable
		○ Really Fast
		○ Only the Key matters
	• Wide Column Store (variation on key value database) (NoSQL)
		○ Has one or more keys (partition key)
		○ Secondary key (sort or range key)
		○ Offer groupings of items called tables (not same as other database)
		○ Every item can have ANY attributes
		○ 
		○ If it's a single key, it has to be unique
		○ If it's a composite key, the combination of both of those values need to be unique
	• Document Database (NoSQL)
		○ Works best with order or contact style databases
		○ Ideal Scenarios:
			§ Interacting with whole documents or deep attribute interactions
		○ Provide flexible indexing - run powerful queries against data nested deep inside document
	• Column (NoSQL)
		○ Counterpart = Row based database (most sql databases)
		○ Store data on disk based on columns
		○ Very inefficient for transactional style processing
		○ Very good for reporting
		○ Columns are stored together
		○ Ideal for reporting or when all values for a specific attribute (size) are required
		○ Redshift (generally shifting a row style database to column style)
	• Row based databases = Online Transaction Processing (OLTP)
		○ Ideal if you are operating with rows (adding, updating, deleting)
	• Graph (NoSQL)
		○ Great for relationship-driven data
		○ Nodes = nouns (objects)
		○ Relationships between nodes = Edges
			§ e.g. :works_for
			§ e.g. :located_in
		○ Relationships stored inside the database
		○ Relationships are fluid, dynamic
			§ Much more efficient
		
### Databases on EC2
	• Bad idea to run databases on EC2
	• Why you might do it:
		○ Access to the DB instance OS
		○ Advanced DB option tuning (DBROOT)
		○ Often an application vendor demanding this level of access
		○ Might need to run a DB or DB version that AWS doesn't provide
		○ Require specific OS/DB combination that AWS doesn't provide
		○ Architecture AWS doesn't provide (replication/resilience)
		○ Decision makers "Just want it"
	• Why you shouldn’t do it:
		○ Admin overhead - managing EC2 instance and the database host/server
			§ Keep EC2 instance patched and DB version at a specific version to be compatible with application
		○ Backup and Disaster Recovery management
			§ Adds additional complexity
		○ EC2 runs in a single AZ
			§ If that zone fails, access to the DB could fail
		○ Features - some of AWS DB products are amazing
		○ EC2 is ON or OFF
			§ No serverless
			§ No easy scaling (burst style demands)
		○ Replication - skills to set it up, setup time, monitoring, and effectiveness
		○ Performance - AWS invest time into optimization and features
	• Never a good idea to have a single, monolithic application stack if you can avoid it
	
### Relational Database Service (RDS) Architecture
	• RDS described as a Database-as-a-service (DBaaS) product
		○ Not entirely accurate
		○ More accurately described as DatabaseServer-as-a-service product
	• RDS provides managed database isntances (1 or more databases)
	• Paying for and consuming a database server that you have access to
	• Don't need to manage the hardware, server OS, or database system (handled by AWS)
	• RDS supports multiple engines:
		○ MySQL, MariaDB, PostgreSQL, Oracle, Microsoft SQL Server
		○ Amazon Aurora - database engine AWS created
	• Provides benefits in terms of reduced admin overhead
	• RDS Database Instance
		○ Instance runs one of a few types of database engines and can contain multiple user-created databases
		○ Access it using a database hostname (CNAME)
		○ Examples
			§ db.m5
			§ db.r5
			§ db.t3
		○ Can be single AZ or multi AZ
			§ Allocate dedicated storage when deploying an RDS instance
				□ Essentially EBS storage located within the same AZ
		○ Billed for amount of storage that you allocate (GB per month)
			§ If using io1, you also pay for IOPS allocation
		○ Access to RDS Instance controlled by Security Group (attached to RDS Instance)

### RDS High-Availability (Multi AZ)
	• Single AZ RDS instances are vulnerable to failures in AZs
	• RDS enables synchronous replication from the primary to the standby
	• RDS access ONLY via CNAME (database endpoint address)
	• CNAME normally points at the primary instance
		○ Cannot access the standby replica using the CNAME
		○ Standby just sits there accepting data from the primary instance
	• If an error occurs in the primary instance, RDS detects and changes the database endpoint CNAME to the standby
	• RDS Multi-AZ provides high availability but not fault tolerance
	
### RDS Automatic Backups, RDS Snapshots, and Restore
	• Recovery Point Objective
		○ Time between last backup and the incident
		○ Amount of maximum data loss
		○ Influences technical solution and cost
		○ Generally lower values cost more
		○ Lowering RPO generally means more regular system backups or some form of replication
		○ Low values in the minutes/seconds can be very expensive
	• Recovery Time Objective
		○ Time between the disaster recovery event and full recovery
		○ Influenced by process, staff, tech, and documentation
		○ Generally lower values cost more
		○ Can be reduced by having spare hardware, effective processes, docs/passwords stored for easy access
	• Two types of backups:
		○ Automated Backups
			§ Just snapshots that occur automatically
			§ Define backup window when they will occur
			§ Every 5 minutes, transaction logs are stored/written to S3
			§ Not retained indefinitely
				□ Automatically cleaned up
				□ Retention period anywhere from 0 to 35 days
				□ When deleting database, you can choose to keep the automated backups but they will still expire
				□ Only way to retain is to create a final snapshot
		○ Manual Snapshots
			§ Run against an RDS database instance
			§ Function like EBS snapshots
				□ First snapshot is a full copy of data used on RDS volume
				□ Then onward it's only incremental and only store the change in data
			§ Brief interruption when snapshots occur
				□ Single AZ can impact
				□ Multi AZ it occurs on the standby and doesn't interrupt
			§ Don't expire and must be cleared by the user
			§ They are not deleted if you delete the RDS instance (offered to make a final snapshot when deleting RDS instance)
		○ Both use AWS Managed S3 Buckets
			§ Any data contained in backups are regionally resilient
			
### RDS Read-Replicas
	• Provide performance and availability benefits
	• Read-only replicas of an RDS instance
	• Kept in sync using asynchronous replication
	• Synchronous replication means Multi-AZ
	• Asynchronous replication means Read Replica
	• Can be in same region or different region (cross region read replica)
		○ Fully encrypted in transit and user doesn't have exposure
	• (read) performance improvements
		○ 5x direct read-replicas per database instance
		○ Each providing an additional instance of read performance
			§ Can scale out read capacity for a database
		○ Read-replicas can have read-replicas - but lag starts to be a problem
		○ Global performance improvements
	• Availability Improvements
		○ Snapshots and Backups improve RPO
		○ RTO's are a problem
		○ Read-replicas offer near 0 RPO
		○ Read-replicas can be prompted quickly - low RTO
		○ Failure only - watch for data corruption
			§ Read-replicas can introduce data corruption
		○ Read only - until promoted
		○ Global availability improvements - global resilience
	• Read replicas provide read scaling for RDS instances
	• Read Replicas work for read scaling but not for write scaling
	
### Snapshot and Restore to Recover from Data Corruption
	• Snapshot represents a discrete point in time
	• RDS instance supports ranges from 20 GiB and 16384 GiB
		○ MariaDB specifically
	• When making changes to RDS Instance, you can apply during a scheduled maintenance window or immediately
	• Restoring using a snapshot creates a brand new RDS instance
		○ Newly restored DB has a brand new endpoint address (CNAME)

### Aurora Architecture
	• Aurora Architecture is VERY different from RDS
		○ Uses a "Cluster"
	• Made up of a single primary instance and 0 or more replicas
	• Replicas within Aurora can be used for reads during normal operation
	• Aurora doesn't use local storage for compute instance
		○ No local storage
		○ Uses cluster volume
		○ Faster provisioning and improved availability and performance
	• Aurora cluster functions across multiple AZs
	• Cluster has shared storage
	• Cluster Volume: Max 64 TiB, 6 Replicas, AZs
	• No extra resources are consumed during replication process
	• Primary instance is the only one able to write to the replicas
	• Aurora automatically detects failures in the disk volumes that make up the shared storage
	• Aurora can have 15 different replicas to failover to
	• Cluster Shared storage based on SSD by default
		○ Provides high IOPS and low latency
		○ Storage is billed based on what's used
		○ High water mark - billed for the most used
			§ Still billed for high water mark even if you reduce storage
		○ Storage which is freed up can be re-used
		○ Replicas can be added and removed without requiring storage provisioning
	• Clusters use endpoints, but they have multiple endpoints available for an application
	• Cluster Endpoint
		○ Always points at primary instance
		○ Endpoint used for read/write operations
	• Reader Endpoint
		○ Can point at primary instance
		○ If there are replicas, reader endpoint will load balance across all replicas
		○ Automatically updated to load balance across new replicas
	• Cost
		○ No free-tier option
		○ Aurora doesn't support Micro Instances
		○ Beyond RDS SingleAZ (micro) Aurora offers better value
		○ Compute - hourly charge, per second, 10 minute minimum
		○ Storage - GB/Month consumed, IO Cost per request
		○ 100% DB size in backups are included
	• Backups in Aurora work in the same way as RDS
	• Restores create a new cluster
	• Backtrack can be used which allow in-place rewinds to a previous point in time
		○ Enabled on per cluster basis and can adjust the window
	• Fast clones make a new database MUCH faster than copying all the data
		○ Doesn't make a one-to-one copy
		○ Copy-on-write
			§ Only stores data that's changed on the clone or data stored in the original after you make the clone
	• Snapshot identifier is the snapshot name

### Aurora Serverless
	• Removes admin overhead of managing individual database instances
	• Scalable
		○ Aurora Capacity Units (ACU)
	• Aurora Serverless cluster has a MIN and MAX ACU
	• Cluster adjusts based on load
	• Can go to 0 and be paused
	• Consumption billing per-second basis
	• Same resilience as Aurora (6 copies across AZs)
	• Architecture:
		○ ACUs are stateless and shared across many customers
		○ Allocated from a shared pool provided by AWS
		○ Number of ACUs dynamically increased/decreased based on load
		○ User interacting with an application  goes through a PROXY FLEET that brokers a connection between the application and the Aurora Capacity Units (ACU)
		○ Only need to pick the min/max values for the ACU
		○ Only billed for amount of ACU you're using at a particular point in time AND the cluster storage
	• Use Cases:
		○ Infrequently used applications
		○ New applications
		○ Variable workloads
		○ Unpredictable workloads
		○ Development and Test databases
			§ Can pause itself during periods of no loads
			§ Only billed for storage during pause periods
		○ Multi-tenant applications

### Aurora Global Database
	• Allow you to create global data replication from Aurora from a master region to up to 5 other regions
	• Introduce concept of secondary regions
	• Entire secondary cluster is read-only during normal operations
	• Replication occurs at the storage layer (~1 second)
	• Great for Cross-Region Disaster Recovery and Business Continuity (BC)
	• Makes sure RPO and RTO values low
	• Great for global read scaling
		○ Low latency performance improvements
	• Replication occurs at the storage layer and generally around 1 second or less between regions
		○ One-way replication from primary to secondary regions
	• Replication has no impact on database performance
		○ Done at storage layer
	• Secondary regions can have 16 replicas
		○ Can be promoted to read/write
	• Currently max of 5 secondary regions
	
### Aurora Multi-Master Writes
	• Allows Aurora cluster to have multiple instances capable of performing read and writes
	• Default Aurora mode is Single-master
		○ Allows one read/write database instance and 0 or more read only replicas
		○ Cluster endpoint is used to write, read endpoint is used for load balanced reads
		○ Failover takes time
			§ Needs replica promoted to read/write
	• In multi-master mode, all instances are read/write
	• Application connects to one or all of the instances within the cluster and initiates operations directly
		○ No load-balanced endpoint
	• One node receives a read/write request, it proposes that data be committed to all storage nodes within the cluster
		○ Each node either confirms or rejects the change
	• Aurora single master cannot be fault tolerant
		○ If failure in primary instance, there will be a delay to move to the replica instance
	
### Database Migration Service (DMS)
	• A managed database migration service
	• Runs using a replication instance
		○ Runs one or more replication tasks where configuration is defined for the migration of databases
	• Need to define the source and destination endpoints within a replication task
		○ Point at source and target databases
		○ One endpoint MUST be on AWS
	• You define replication tasks that define all options relating to migration
	• Replication instance performs the migration between source and destination endpoints which store connection information for source and target databases
	• Source and destination endpoints store the connection information
	• Tasks moves data from source to target database using details in the source/destination endpoints
	• Jobs can be Full Load (one off migration of all data), Full Load + CDC (Change Data Capture) for ongoing replication which captures changes only, or CDC Only (if you want to use an alternative method to transfer the bulk database data such as native tooling)
	• Schema Conversion Tool (SCT) can assist with Schema Conversion
	• If question talks about no downtime or little downtime, then question likely to be DMS
		○ AS LONG AS AT LEAST ONE DATABASE IS WITHIN AWS
	
# Network Storage
### Elastic File System (EFS) Architecture
	• Provides network based file systems that can be mounted within linux EC2 instances
	• Can be used by multiple instances at once
	• EFS is an implementation of NFSv4 (network file system)
	• EFS filesystems can be mounted in Linux
	• Uses tree structure for filesystem
	• Shared between many EC2 instances
	• Private Service via mount targets inside a VPC
	• Can be accessed from on-premises
		○ VPN
		○ DX (Direct Connect)
		○ Must configure this access
	• EFS made available inside a VPC using mount targets
	• Need to put mount targets inside multiple AZs in order to ensure high availability
	• EFS is for linux only instances
	• Offers two performance modes:
		○ General Purpose
			§ Latency sensitive use cases (web servers, home directories, file servers
			§ Default
		○ Max I/O
			§ Scale to high levels of aggregate throughput and operations per second
			§ Increased latencies
			§ Highly parallel applications (big data, media processing, scientific analysis
	• General Purpose = default for 99.9% of uses
	• Bursting and Provisioned throughput modes
		○ Bursting throughput scales with the size of the filesystems
		○ Provisioned you specify separate from size
	• Standard and Infrequent Access (IA) classes
		○ IA = lower cost for things that aren't accessed as often
		○ Standard = default
			§ Day to day data
	• Lifecycle policies can be used with classes
		○ Move data between classes
	
# High Availability (HA) and Scaling
### Load Balancing Fundamentals
	• LB set to listen on certain protocols and ports
		○ Configuration for which ports the load balancer listens on is called a LISTENER
			§ Controls what it's listening to on the user side
	• User connects to the Load Balancer and not the actual server
	• User client thinks it's talking to the server directly
	• Without load balancer, the user client receives directions from DNS to connect to a server
		○ Work is put on the client and that's inefficient
	• Customers connect to the Load Balancer (LB)
		○ As long as 1+ servers are operational
		○ The LB is operational
		○ Clients shouldn't see failure
	• Used for high available and fault tolerant architectures
	
### Application Load Balancer (ALB)
	• Legacy load balancer = Classic Load Balancer (CLB)
	• Elastic Load Balancer (ELB) refers to family of three products:
		○ Classic Load Balancer (CLB
		○ Application Load Balancer (ALB)
		○ Network Load Balancer (NLB)
	• ALB is a Layer-7 (application layer) LB
		○ Understands http and https
	• Scalable and highly-available
	• Capacity increases automatically depending on the load that's passing through the ALB
	• Internet-facing or internal
		○ Depends on whether nodes have public IP addresses or not
	• Listens on the outside -> sends to Target(s) (Groups)
	• Billed based on Hourly rate and Load Balancer Capacity Unit (LCU) Rate (Capacity)
		○ 1 LCU allows:
			§ 25 new connections per second
			§ 3000 active connections per minute
			§ 1GB per hour for EC2 instances, containers, and IP address as targets
			§ 0.4GB per hour for lambda functions as targets
			§ 1000 rule evaluations per second
	• Load Balancer by default has at least 1 node per AZ it's configured for
	• Each node gets 100% / number of nodes
	• Cross Zone Load Balancing
		○ Load Balancing across AZs
	• Load Balancers perform health checks
	• Targets = services that ALB can distribute connections to
		○ EC2 instances, containers, lambda functions, etc
		○ Grouped within target groups
		○ Can be member of multiple target groups (overlapping)
	
### Launch Configuration and Templates
	• Launch Configurations and Launch Templates provide the WHAT to Auto scaling groups.
	• They define WHAT gets provisioned
	• The AMI, the Instance Type, the networking & security, the key pair to use, the userdata to inject and IAM Role to attach.
	• Allow you to define the configuration of an EC2 instance in advance. Let's you define:
		○ Documents which let you configure AMI, Instance Type, Storage, and Key Pair
		○ Define networking configuration and security groups
		○ Userdata and IAM role
		○ Everything you can define at the configuration of an EC2 instance can be defined with LC and LT
	• Both are NOT editable
		○ Defined once
		○ Launch Templates is the newer and allows versions
			§ Provide newer features
				□ T2/T3 unlimited, placement groups, capacity reservations, elastic graphics
	• Launch Configurations (LC) used as part of auto scaling groups
		○ Not editable
		○ No versioning
	• Launch Templates can be used as part of auto scaling groups
		○ Can be used to launch EC2 instances directly from console UI/CLI
		
### Auto-Scaling Groups
	• Automatic scaling and self-healing for EC2
	• Auto Scaling Groups are how Scaling and self-healing can be implemented within AWS using EC2.
	• ASGs use LT and LC to control WHAT gets launched, and provide various types of scaling policy to scale OUT and IN based on metrics.
	• Uses Launch Templates or Configurations
		○ Uses 1 at a time
	• Has three values associated with it:
		○ Minimum size
		○ Desired capacity
		○ Maximum size
	• Provision or terminate instances to keep at Desired level (between Min/Max)
	• Scaling policies automate based on metrics
	• ASG runs inside a VPC across 1 or more subnets
	• Scaling policies automatically adjust the Desired Capacity between the MIN and MAX values
	• ASG define where instances are launched
		○ Want to keep number of instances between AZs even
	• Scaling Policies are rules that you define which can adjust values within ASG
	• Manual Scaling = manually adjust the desired capacity
	• Scheduled Scaling = time based adjustments (e.g. sales)
	• Dynamic Scaling
		○ Simple - define rule based on a metric
			§ e.g. CPU above 50% + 1, adjust capacity by 1
			§ Can scale out or in
		○ Stepped - define more detailed rules
			§ Bigger add/subtract based on difference
			§ Allows you to react in a more extreme way for more extreme conditions
		○ Target Tracking - define ideal amount for something
			§ e.g. Desired Aggregate CPU = 40% -> ASG handle it
	• Cooldown Period
		○ Value in seconds
		○ Controls how long to wait at the end of a scaling action before performing another action
		○ Can avoid costs with constantly adding/removing instances
	• ASG instances are automatically added to or removed from the target group and can be used with a load balancer pointed at that target group
	• ASG can use the Load Balancer health checks rather than EC2 status checks Application Awareness
	• Autoscaling Groups are free
		○ Billed for resources created by the ASG
	• Use cool down periods to avoid rapid scaling
	• Think about more, smaller instances for more granularity
	• Use with ALB's for elasticity - abstraction
	• ASG defines WHEN and WHERE, and the Launch Template/Configuration defines WHAT
	
### Network Load Balancing (NLB)
	• Part of AWS version 2 load balancers
	• NLB's are Layer-4
		○ Only understand TCP and UDP
		○ Understand IP address too
	• Can't understand HTTP/S but are faster
		○ ~100ms vs 400ms for application load balancers
	• If HTTP/S are NOT required, you should default to NLB
	• Nothing stopping an NLB load balancing TCP port 80
		○ Can load balance the network part of http connections
		○ Just performing simple cycling of connections
	• Rapid Scaling
		○ Millions of requests per second
	• 1 interface with static IP per AZ
		○ Can use Elastic IPs (whitelisting)
	• Can do SSL Pass through
	• Anything running above TCP/UDP is just data that the NLB passes along
	• Can load balance non HTTP/S applications
		○ Doesn't care about anything above TCP/UDP
		○ E.g. FTP
	
### SSL Offload and Session Stickiness
	• SSL Offload
		○ Bridging
			§ One or more clients makes one or more connections to a load balancer
			§ Load balancer has listener using HTTPS
			§ Connection is terminated on the ELB and needs a certificate for the domain name
			§ AWS has some level of access to the certificate
				□ Keep in mind if you have strong security frameworks you need to adhere to
			§ ELB initiates a new SSL connection to backend instances
			§ Instances need SSL certificates and the compute required for cryptographic operations
			§ ALB in bridging mode can see http traffic
			§ Default mode for application load balancer and why the ALB requires an SSL certificate
			§ EC2 instances need matching SSL certificates
			§ ELB gets to see the unencrypted HTTP and can take actions based on what's in it
		○ Pass-through
			§ Load balancer just passes the connection along to the backend instances
			§ Connection maintained between the client and backend instances
			§ Each instance needs to have the  appropriate SSL cert installed
			§ With this architecture there is no certificate exposure to AWS
				□ All self-managed and secured
			§ Listener is configured for TCP
			§ No encryption or decryption happens on the NLB
			§ Connection is passed to backend instance
			§ AWS never needs to see the SSL certificate
			§ No performing load balancing based on the HTTP part
			§ Instances still need to have the certificates and need to compute the cryptographic operations
		○ Offload
			§ Listener is configured for HTTPS
			§ Connections are terminated and then backend connections use HTTP
			§ ELB to instance connections use HTTP
				□ No certificate or cryptographic requirements
			§ Data is encrypted between the user and the load balancer
				□ Then travels from the load balancer to the instances in plaintext form
				□ No compute requirements
			§ Data is in plaintext form across AWS networks
	• Connection Stickiness
		○ With no stickiness, connections are distributed across all in-service backend instances
		○ Unless application handles user state, this could cause user logoffs shopping cart losses
		○ With stickiness, the load balancer generates a cookie (called AWSALB)
		○ Stickiness generates a cookie which locks the device to a single backend instance for a duration
			§ 1s to 7 days
		○ Happens until two things occur:
			§ Server failure
			§ Cookie expires
		○ Can cause uneven load on backend servers
		○ When possible, should host the session on DynamoDB so the cookie isn't stored on the EC2 instances
		
# Serverless and Application Services
### Architecture Evolution - Monolithic and Tiered
	• Monolithic Architecture
		○ All applications within one entity
			§ If one component fails, it impacts all components
		○ Fails together
		○ Scales together
			§ Everything on same server, directly connected, using same codebase
			§ Need to vertically scale the system
		○ Generally billed together
			§ All components always running
		○ Least cost effective ways of architecturing systems
	• Tiered Architecture
		○ Break apart monolith architecture
		○ Each tier can be on same or different servers
		○ Individual tiers can be scaled vertically/independently
			§ Increase one tier without having to increase any other tiers
		○ Can utilize load balancers placed in between each tiers
			§ Tiers aren't specifically communicating to each other
			§ Allows for horizontal scaling
		○ Tiers are still coupled
			§ Tiers expect and require other tiers to respond
		○ Each tier has to be running something for the app to function

### Architecture Evolution - Queue based, Microservice, and Event-Driven
	• Queue based
		○ Typically, messages received off the queue in a FIFO (first in first out) architecture
		○ Tiers don't expect/need an immediate response from other tiers
		○ Uses Asynchronous communications
		○ Uses an auto scaling group that uses the queue length in order to provision instances depending on the queue
		○ One tier adds jobs to the queue and another tier reads jobs from the queue
			§ Tiers don't depend on each other
		○ Components are decoupled and can scale independently/freely
	• Microservice
		○ Collection of microservices that do individual things well
		○ Might be different services or multiples of the same service
		○ Producers
			§ Produce data/messages
		○ Consume
			§ Consume data/messages
		○ Both
			§ Does both
		○ Just a tiny self-service application
	• Event-driven
		○ Collection of event producers
			§ bits of software that generate and produce events in reaction to something
		○ And Event Consumers
			§ Wait for an event and take action
		○ Components can be both event producers/consumers
		○ Event producers/consumers don't wait for things to happen
		○ Best practice has an event router that has an event bus (constant flow of info)
			§ Events generated by producers are added to the event bus and then goes to the event consumer
		○ No constant running or waiting for things
		○ Producers generate events when something happens
			§ Clicks, errors, criteria met, uploads, actions
		○ Events are delivered to consumers of those events
			§ Generally happens using an event router
		○ Actions are taken and the system returns to waiting
		○ Mature event-driven architecture only consumes resources while handling events (serverless)
		
### AWS Lambda
	• Function-as-a-Service (Faas)
	• Event-driven invocation (execution)
		○ Lambda functions are invoked (executed) based on events
	• Lambda function = piece of code in one language
	• Lambda functions use a runtime (e.g. Python 3.6)
	• Runs in a runtime environment
		○ Virtual environment that's able to run code in a specific language
	• You are billed only for the duration a function runs
		○ Difference between lambda and running directly on ec2 instance
	• Key component of serverless architecture
		○ Consuming other services
		○ Using other as-a-service products
	• Best practice is to make lambda function super specialized
	• Can configure Lambda function to use an IAM role known as an Execution Role
		○ Passed into the runtime environment
	• Event-driven or manual invocation
		○ e.g. AWS service, customer via API gateway, or even scheduled
	• Capable of highly parallel form of execution
	• Assume the environment is new every time (stateless)
		○ Not persistent
	• Functions can access public internet resources
	• Can be configured to be invoked inside a VPC to access private resources
		○ Can only access VPC resources unless you've configured VPC to have access to public internet access or AWS public space
	• Execution Role provides access to AWS services
		○ e.g. DynamoDB and S3 for input and output
	• Can run for less than a second or anywhere up to 15 minutes
	• Start at Lambda for any compute requirement less than 15 minutes duration
		○ Much more economical compute service
	• Currently - 15 minute execution limit
	• New runtime environment every execution - no persistence
	• Execution Role provides permissions
	• Load data FROM other services (e.g. S3)
	• Store data TO other services (e.g. S3)
	• (free tier) 1million free requests per month and 400,000 GB-seconds of compute time per month
	
### CloudWatch Events and EventBridge
	• Delivers a near real-time stream of events
	• EventBridge replacing CloudWatch Events
		○ Can handle events from third parties and custom applications
	• Allow you to implement an architecture:
		○ If X happens, or at Y time(s) then do Z
	• EventBridge is basically CloudWatch Events v2
	• A default Event Bus for the account
		○ Bus is a stream of events that occur
		○ In CloudWatch Events this is the only bus (implicit)
	• EventBridge can have additional event buses
	• Rules match incoming events or schedules
		○ Pattern matching rules
		○ Scheduled rules
	• Route the events to 1 or more targets (e.g. Lambda)
	• When rule is executed, it delivers the event to one or more targets
	• Events are JSON structures
		○ Data in the JSON structures can be used by a target

### API Gateway
	• Application Programming Interface (API)
	• Provide application functionality to other users, applications, systems
	• Way that applications can communicate with each other
	• Each service has it's own endpoint inside each region
		○ Endpoints are entry points for AWS APIs
	• API = piece of code that's hosted on a server
	• API in most cases perform authentication
	• API is the entity that authorizes every single operation that is tried to perform on services that that API manages
	• Two different processes: Authentication and Authorization
	• API Gateway is a managed API Endpoint Service
	• Allows you to create, publish, monitor, and secure APIs AS A SERVICE
	• Billed based on the number of API Calls, Data Transfer, and additional performance features such as caching
	• Can be used directly for serverless architecture
		○ Or during architecture evolution
			§ Migrating services from on-premises to AWS as a serverless architecture
	• Core product used to deliver serverless architectures inside AWS

### Serverless Architecture
	• Serverless isn't one single thing
	• Aiming to manager few, if any servers - low overhead
	• Applications are a collection of small and specialized functions
	• Functions run in stateless and ephemeral environments
		○ Duration Billing
	• Generally, everything is event-driven
		○ Consumption only when being used
	• Serverless environments should use FaaS for compute functionality
	• Generally have no persistent use of compute within that system
	• Managed services are used where possible
		○ e.g. S3 for persistent object storage, DynamoDB for persistent data storage, third-party identity providers like google and twitter and active directory
	• Limit on number of IAM users inside AWS account
		○ 5000 IAM users per account
		○ Use third party identity provider to get around this 
			§ e.g. Authenticate with Google IDP to receive token
	• Cognito swaps third-party IDP to swap token for AWS temp credentials
	
### Simple Notification Service
	• The Simple Notification Service or SNS .. is a PUB SUB style notification system which is used within AWS products and services but can also form an essential part of serverless, event-driven and traditional application architectures.
	• Publishers send messages to TOPICS
	• Subscribers receive messages SENT to TOPICS.
	• SNS supports a wide variety of subscriber types including other AWS services such as LAMBDA and SQS.
	• Public AWS Service
		○ Requires network connectivity with Public Endpoint
	• Coordinates the sending and delivery of messages
	• Messages are <= 256KB payloads
	• SNS Topics are the base entity of SNS
		○ Permissions are controlled and configurations are defined
	• A Publisher SENDS messages to a TOPIC
	• TOPICS have SUBSCRIBERS which receive messages
		○ HTTP(S), Email (-JSON), SQS, Mobile Push, SMS Messages, and Lambda
	• SNS used across AWS for notifications
		○ e.g. CloudWatch and CloudFormation
	• Things can be subscribers and producers at the same time
		○ e.g. APIs
	• Fanout Architecture
		○ Single SNS topic with multiple SQS Queues as subscribers
		○ Create multiple, related workloads
	• Offers the following:
		○ Delivery Status - Including HTTP, Lambda, SQS
		○ Delivery Retries - reliable delivery
		○ Highly available and scalable within a region
		○ Server Side Encryption (SSE)
			§ Any data needed to be stored on disk can be encrypted
		○ Cross-Account via TOPIC Policy
		
### Step Functions
	• Long-Running Serverless Workflows
	• Problems with Lambda:
		○ Lambda is a Function as a Service (FaaS) product
		○ 15-minute max execution time
		○ Can be chained together but gets messy at scale
		○ Runtime environments are stateless
			§ Each environment cleaned each time
	• Step Functions let you create state machines
		○ Serverless workflow with a start > states > end
		○ States are THINGS which occur
		○ Max duration for state machine execution within step functions is 1 YEAR
		○ Standard workflow and Express workflow
			§ Standard is default and 1 year execution limit
			§ Express designed for high volume, event driven workloads
				□ Can run for up to 5 minutes
		○ Started via API Gateway, IOT Rules, EventBridge, Lambda, manually
		○ Amazon States Language (ASL) - JSON Template
			§ Can use template to create and export state machines
		○ IAM Role is used for permissions
	• Different States:
		○ SUCCEED and FAIL
		○ WAIT
			§ Will wait for certain period of time or until a specific date and time
		○ CHOICE
			§ Allows state machine to take a different path depending on an input
		○ PARALLEL
			§ Allows to create parallel branches within a state machine
		○ MAP
			§ Accepts a list of things (e.g. list of orders)
		○ TASK (Lambda, Batch, DynamoDB, ECS, SNS, SQS, Glue, SageMaker, EMR, Step Functions)
			§ How a state machine can actually perform work
			§ Coordinate with other external services to do the work

### Simple Queue Service (SQS)
	• Public, Fully Managed, Highly-Available Queues
		○ Standard
			§ Best Efforts
			§ Possibility messages are received out of order
		○ FIFO
			§ Guarantee an order
			§ See messages in order
	• Messages up to 256KB in size
		○ Link to large data from something like S3
		○ Ideally want to keep messages small for better processing at scale
	• Polling = checking for any messages on a queue
	• Received messages are hidden (VisibilityTimeout)
		○ After VisibilityTimeout, messages either reappear (retry) or are explicitly deleted
	• Dead-letter queue can be used for problem messages
		○ Ex. Message received 5 or more times and not deleted, then moved to dead-letter queue
	• ASGs can scal and Lambdas invoke based on queue length
	• SNS and SQS Fanout
		○ Message sent to SNS topic then to different SQS queues
		○ Allows for multiple jobs to be started per the object upload
	• Standard Queues
		○ Guarantee at-least-once delivery
	• FIFO
		○ Guarantee exactly-once delivery
		○ Guarantee to maintain the order of messages
	• FIFO (performance)
		○ 3000 messages per second with batching, or up to 300 messages per second without
	• Billed on requests
	• 1 request = 1-10 messages up to 64KB total
	• Short (immediately) vs Long (waitTimeSeconds) polling
		○ Long polling is how you should poll SQS because it uses less requests
	• Encryption at rest (KMS) and in-transit encryption is supported
		○ Data by default is encrypted in-transit between the client and SQS
	• Access to queue is based on identity policies or you can use queue policy
		○ Queue policy = resource policy
		○ Queue policy is the only way to allow access from external accounts
	
### Kinesis and Kinesis Firehose
	• Kinesis is a scalable streaming service
		○ Designed to ingest lots of data
	• Producers send data into a kinesis stream
	• Streams can scale from low to near infinite data rates
	• Public service and highly available by design
	• Streams store a 24-hour moving window of data
	• Multiple consumers access data from that moving window
	• Great for things like analytics and dashboards
	• Producers = EC2 instances, on-premise servers, mobile applications/devices, etc
	• Consumers = on-prem servers, lambda functions, EC2 instances, etc
	• Kinesis stream connects producers and consumers
	• Kinesis stream scales by using a shard architecture
		○ Each shard provides own performance
			§ 1MB ingestion capacity
			§ 2MB consumption capacity
		○ More shards = more cost
	• 24-hour window up to 7 days (at a higher cost)
	• Data stored on stream using a Kinesis Data Record (max size of 1MB)
		○ Stored across shards
	• Kinesis Data Firehose
		○ Connects to stream and moves data from stream to another AWS service (ex. S3)
		○ Good if you need to store for a longer term or if you need to analyze data
	• SQS vs Kinesis
		○ If question is about ingestion of data or ingestion of data at scale = Kinesis
		○ SQS generally has one thing sending messages to a queue
			§ 1 production group and 1 consumption group
		○ SQS queues designed for decoupling and asynchronous communications
		○ SQS has no persistence of messages, no concept of time window
		○ Kinesis designed for huge scale ingestion of data
			§ Designed for multiple consumers with rolling window
		○ Kinesis designed for data ingestion, analytics, monitoring, and app clicks
	• Looking to decouple applications, provide asynchronous communications to split workload and have web tier and worker pool:
		○ SQS
	• Data ingestion, lots of devices pumping data into AWS at scale (STREAMING data into AWS). Lots of different consumers consuming data at different rates at different points in time of this rolling window:
		○ Kinesis

# Global Content Delivery and Optimization
### CloudFront Architecture Basics
	• Content Delivery Network (CDN)
	• CloudFront is a global object cache (CDN)
	• Content is cached in locations close to customers
	• Brings lower latency (more responsiveness) and higher throughput (faster page loads and interactions)
	• Load on the content server is decreased
	• It can handle static and dynamic content
	• Origin
		○ The source location of your content
			§ S3 bucket or application load balancer or anything accessible on the public internet
	• Distribution
		○ The configuration unit of CloudFront
		○ Create a distribution and that gets deployed out to the network
	• Edge Location
		○ Local infrastructure which hosts a cache of your data
		○ In or around capital cities or large urban areas
		○ Over 200 edge locations (as of now)
		○ Smaller than AWS regions
		○ Generally 1+ racks in a third party data center
		○ Around 90% storage with a small compute portion
	• Regional Edge Cache
		○ Larger version of an edge location
		○ Provides another layer of caching
	• Edge locations actually cache the content and are globally distributed
	• General steps:
		1. Checks Edge location
		2. If not at edge location, goes to regional edge location
			i. Regional edge location also checks local edge locations in the area
		3. If not at regional edge location, checks origin
		4. Gets cache from origin = Origin Fetch
		5. Goes through regional edge location, then edge location, then back to user
		6. Cache is now available at that regional edge location
	• CloudFront integrates with ACM (AWS Certificate Manager) for HTTPS
	• Upload directs to origins - no caching
		○ For download style operations only
		○ Any object uploads will automatically go directly from the customer to the origin (not through the edge locations)
	• Query String Parameters
		○ Ex. http://animals4life.org/whiskers.jpg?language=en
			§ ?language=en
		○ Caching objects both on the name and the unique query string parameters
		○ Options:
			§ If application doesn't use query string parameters, don't worry about it at all
				□ Can configure CloudFront Distribution to either forward the query string parameters to the Origin or not
			§ If application does use Query String Parameters, you can choose to use ALL or SELECTED ones for caching
			
### ACM
	• AWS Certificate Manager
	• Let's you manage, provision, and deploy public and private certificates used mainly with AWS services
	• HTTP = simple and insecure
		○ No server ID authentication or transport encryption
	• HTTPS = SSL/TLS layer of encryption added to HTTP
		○ Creates a secure tunnel over which normal HTTP can be transferred
		○ Data is encrypted in-transit
		○ Certificates prove identity
		○ Signed by a trusted authority
	• Create, renew, and deploy certificates with ACM
	• Supported AWS services ONLY (e.g. CloudFront and ALBs but NOT EC2)
	• Certificate created for DNS name (e.g. animals4life.org)
	• Certificates deployed onto supported services
	• Edge locations are accessed using HTTPS and the DNS name on the certificate
	• Origin certificates must be valid (no self-signed certs)
	• For CloudFront, if you're communicating between the edge locations and the origins using HTTPS, it needs to be a trusted, signed certificate
	
### Securing CF and S3 using OAI
	• Origin Access Identity
	• Create the OAI and associate it with a CloudFront distribution
		○ Edge locations gain the origin access identity
	• Once OAI is associated with the distribution, accesses are FROM the OAI
	• Direct access blocked via implicit Deny
		○ Implicit Deny from the S3 Bucket Policy
	• CloudFront capable of being set to Private
		○ Only affects accesses via the edge location
	
### Lambda@Edge
	• CloudFront Lambda @ Edge
	• You can run lightweight Lambda functions at edge locations
	• Adjust data between the Viewer and Origin
	• Don't have full lambda feature set
	• Currently supports Node.js and Python
	• Run in the AWS Public Space (Not VPC)
	• Layers are not supported
	• Different limits vs normal lambda functions
	• Connection between user and Edge Location = Viewer Request
		○ After CloudFront receives a request from a viewer (Customer)
	• Connection between the Edge Location and the user = Viewer Response
		○ Before CloudFront forwards the request to an origin
	• Connection between the Edge Location and the Origin = Origin Request
		○ After CloudFront receives a response from an origin
	• Connection between the Origin and the Edge Location = Origin Response
		○ Before a response is forwarded to a viewer (customer)
	• Each of the components of the communications above can run lambda functions that can influence the traffic of those connections
	• On viewer side, a lambda@edge function has a limit of 128MB for memory allocation and function timeout of 5 seconds
	• On origin side, a lambda@edge function has a limit of 128MB for memory allocation and function timeout of 30 seconds
	• Can do pretty much whatever you want as long as you can code it in a lambda environment
	• Scenarios for using Lambda@Edge:
		○ Can use Lambda to perform A/B testing
			§ Generally done with a viewer request function
		○ Migration between S3 origins
			§ Origin Request
			§ Gradually transfer traffic from existing S3 origin to a new one
		○ Different objects based on device
			§ Origin Request
			§ Display different objects based on type/capability of device
		○ Content by country
			§ Origin Request
			§ Adjust what gets displayed based on country of customer

### Global Accelerator
	• AWS Global Accelerator is designed to improve global network performance by offering entry point onto the global AWS transit network as close to customers as possible using Anycast IP addresses
	• Architecturally similar to CloudFront
	• Starts with 2 Anycast IP Addresses
		○ Special type of IP Address
		○ Normal IP Address = Unicast (1 device)
		○ Anycast IP's allow a single IP to be in multiple locations. Routing moves traffic to closest location
	• Global Accelerator Edge Locations use all IP Anycast IP Addresses
	• Traffic initially uses public internet and enters a Global Accelerator edge location
	• From the edge, data transits globally across the AWS global backbone network
		○ Less hops, directly under AWS control, significantly better performance
	• Customers arrive at global accelerator edge locations because they're using one of the anycast IP addresses
	• Moves the AWS network closer to the customers
		○ CloudFront does this by caching the content on the edge locations
		○ Global Accelerator moves the actual AWS network as close to the customers as possible
	• Connections enter at edge using anycast IPs
	• Transit over AWS backbone to 1 or more locations
	• Gets data from customer to application endpoint as quickly as possible with best performance
	• Can be used for NON HTTP/S (TCP/UDP)
		○ Difference from CloudFront
	• Questions with caching typically indicate CloudFront
	• Questions mentioning TCP/UDP and requirement for global performance optimization then it should be Global Accelerator
	• Global Accelerator doesn't cache

# Advanced VPC Networking
### VPC Flow Logs
	• VPC FLow logs is a feature allowing the monitoring of traffic flow to and from interfaces within a VPC
	• VPC Flow logs can be added at a VPC, Subnet or Interface level.
	• Flow Logs DON'T monitor packet contents ... that requires a packet sniffer.
	• Flow Logs can be stored on S3 or CloudWatch Logs
	• https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-s3.html
	• https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-cwl.html
	• Capture packet Metadata
		○ NOT PACKET CONTENTS
		○ I.e. Source/Destination IP Address/Ports
	• Applied to a:
		○ VPC - All interfaces in that VPC
		○ Subnet - interfaces in that subnet
		○ Interface directly
	• VPC Flow Logs are NOT realtime
		○ Can't rely on Flow Logs to provide realtime telemetry on network packet flow
	• Destination can be S3 or CloudWatch Logs
		○ Each come with different tradeoffs
	• RDS can use VPC Flow Logs
	• 0 for port is protocol that doesn't use port numbers
		○ Ex. ICMP
	• Protocol within Flow Logs:
		○ ICMP = 1
		○ TCP = 6
		○ UDP = 17
	• If security group, then generally only 1 line with show in the flow log
	• If you see two flow log entries (one that accepts and one that rejects), it generally is an interaction between security group and network ACLs
	• Not all traffic is recorded in Flow Logs
		○ Communication with the metadata IP: 169.254.169.254
		○ AWS Time Synchronization server: 169.254.169.123
		○ DHCP
		○ Amazon DNS Server
		○ Amazon Windows License server not recorded
	
### Egress-Only Internet Gateway
	• Internet gateway which only allows connections to be initiated from inside a VPC to outside the VPC
	• With IPv4 addresses are private or public
	• Private instances cannot communicate directly with the public internet or AWS public services
	• Public instances can communicate to the public internet and can be communicated with from the public internet
	• NAT allows private IPs to access public networks without allowing externally initiated connections (IN)
		○ Doesn't allow any connections from the internet to be initiated to the private instance
	• With IPv6, ALL IPs are public
	• Internet Gateway (IPv6) allows all IPs IN and OUT
	• NAT isn't usable with IPv6
	• Egress-Only is outbound-only for IPv6
		○ Things cannot initiate connections in
	• Egress-Only Gateway is Highly Available (HA) by default across all AZs in the region
		○ Scales as required
	• Architecture is exactly the same as the IGW
	• Default IPv6 Route ::/0 added to Route Table with eigw-id as target
	• Only allows outgoing connections AND their response
	
### VPC Endpoints (Gateway)
	• Gateway endpoints are a type of VPC endpoint which allow access to S3 and DynamoDB without using public addressing.
	• Gateway endpoints add 'prefix lists' to route table, allowing the VPC router to direct traffic flow to the public services via the gateway endpoint.
	• Provide private access to supported resources (currently S3 and DynamoDB)
		○ Allow private-only resource inside a vpc or ANY resource inside a private-only VPC to access S3 and DynamoDB
	• Prefix List added to route table -> Gateway Endpoint
		○ Prefix list uses gateway endpoint as a target
	• Highly Available (HA) across all AZs in a region by default
	• Is a VPC endpoint object
	• Does not go into a particular subnet
	• Endpoint policy is used to control what it can access
	• Can only be used to access services in the same region
		○ Can't access cross-region services
	• Support two main use-cases:
		○ Private VPC to allow public resources (S3 or DynamoDB)
		○ Private-only S3 Buckets
			§ Prevent Leaky Buckets - S3 buckets can be set to private only by allowing access ONLY from a gateway endpoint
	• Limitation: Only accessible from inside that specific VPC
		○ Logical gateway object and can only access logical gateways from within that VPC
	• Gateway endpoints are HA by design
	• Region resilient by default
	• Gateway endpoints are not accessible outside of the VPC they're associated with
	• Endpoint policies can be used to control what the endpoint can be used to access
	
### VPC Endpoints (Interface)
	• Interface endpoints are used to allow private IP addressing to access public AWS services.
	• S3 and DynamoDB are handled by gateway endpoints - other supported services are handled by interface endpoints.
	• Unlike gateway endpoints - interface endpoints are not highly available by default - they are normal VPC network interfaces and should be placed 1 per AZ to ensure full HA.
	• Provide private access to AWS public services
		○ Anything NOT S3 and DynamoDB
	• Added to specific subnets - an ENI - not HA
	• For HA, add one endpoint, to one subnet, per AZ used in the VPC
		○ 2 AZ require 2 interface endpoint
		○ 3 AZ require 3 interface endpoint
		○ So on
	• Network access controlled via Security Groups
	• Endpoint policies - restrict what can be done with the endpoint
	• TCP and IPv4 ONLY
	• Interface endpoints use PrivateLink
		○ Allow external services to be injected into your VPC 
			§ From AWS or third parties
		○ Given network interfaces inside your VPC subnet
		○ Useful for heavily regulated industry but also want to allow third-party resources inside the VPC
	• Primarily use DNS
	• Endpoint provides a NEW service endpoint DNS
		○ e.g. vpce-12-xyz.sns.us-east-1.vpce.amazonaws.com
	• Endpoint Regional DNS
		○ Single DNS name that works with whatever AZ you're using the access the endpoint
	• Endpoint Zonal DNS
		○ Resolves to that one specific interface in that one specific AZ
	• Applications can optionally use these two (endpoint regional DNS or endpoint zonal DNS) or PrivateDNS overrides the default DNS for services
		○ Associates a route53 private hosted zone with your VPC
		○ Carries a replacement DNS record for the default service DNS name
	• Interface Endpoint can access the private services without a public IP address. Has direct access
	• Private DNS associates a private route53 hosted zone to the VPC changing the default service DNS to resolve to the interface endpoint IP
	• Gateway endpoints work using prefix lists and route tables
		○ Never require changes to the applications
		○ Application thinks its communicating directly with S3 or DynamoDB
		○ Instead of going via the IGW and requiring public IP addresses, it goes via an endpoint gateway and can use private IP addressing
		○ HA by design
	• Interface endpoint uses DNS and a private IP address for the interface endpoint
		○ Can use endpoint specific DNS names or enable private DNS which overrides the default and allows unmodified applications to access the services using the interface endpoint
		○ Doesn't use routing but rather DNS
		○ Not HA
	
### VPC Peering
	• Direct encrypted network link between two VPCs
		○ ONLY TWO
	• Works same/cross-region and same/cross-account
	• (optional) Public Hostnames resolve to private IPs
	• Same region security groups can reference peer security groups
		○ Only works with VPC peers inside the same regions
		○ If in same region, you can reference SGs logically
	• VPC Peering does NOT support transitive peering
		○ VPC A peered with VPC B which is peered with VPC C
			§ VPC A IS NOT peered with VPC C
		○ ONLY PEERED BETWEEN TWO VPCs
		○ Can't route through interconnected VPCs
	• Creating a logical gateway object inside both VPCs
	• Routing Configuration is needed
		○ Security Groups and Network ACLs (NACLs) can filter
	• Route tables at both sides of the peering connection are needed, directing traffic flow for the remote CIDR at the peer gateway object
	• VPC Peering connections cannot be created where there is overlap in the VPC CIDRs
		○ Ideally NEVER use the same address ranges in multiple VPCs
	• Communication is encrypted and transits over the AWS global network when using cross-region peering connections
	
# Hybrid Environments and Migration
### Border Gateway Protocol
	• Routing protocol used to control how data flows and arrives at destination
	• Autonomous Systems (AS)
		○ Routers controlled by one entity
		○ A network in BGP
		○ Blackboxes that only concern themselves with network routing in/out of the autonomous system
	• Autonomous System Number (ASN) are unique and allocated by IANA (0-65535)
		○ 64512-65534 are private and utilized in private peering arrangements without being officially allocated
		○ The rest are public ASN directly allocated by IANA
	• BGP operates over TCP using port 179
		○ It's reliable
	• Not automatic
		○ Peering is manually configured
	• BGP is a path-vector protocol
		○ It exchanges the best path to a destination between peers
		○ The path is called the ASPATH
		○ Doesn’t take into account link speed or conditions
	• iBGP
		○ Internal BGP
		○ Routing WITHIN an autonomous system (AS)
	• eBGP
		○ External BGP
		○ Routing BETWEEN autonomous system (AS)
	• i is the origin
		○ The network was learned from a locally connected network
	• BGP exchanges the shortest ASPATH between peers
	• AS Path Prepending can be used to artificially make the satellite path look longer making the fiber path preferred
	• An Autonomous System (AS) will advertise all the shortest paths it knows to all its peers, the AS prepends its own AS number onto the path
		○ This creates a source to destination path which BGP routers can learn and propogate
		
### AWS Site-to-Site VPN
	• AWS Site-to-Site VPN is a hardware VPN solution which creates a highly available IPSEC VPN between an AWS VPN and external network such as on-premises traditional networks. VPNs are quick to setup vs direct connect, don't offer the same high performance, but do encrypt data in transit. This lesson details the architecture and key concepts you need to be aware of for the exam.
	• Offer quickest way to create a link between an AWS environment and something that's not an AWS environment (on-prem)
	• A logical connection between a VPC and on-premises network encrypted using IPSec, running over the public internet
	• Full HA - if you design and implement it correctly
	• Quick to provision
		○ Less than an hour
		○ In contrast to the long provision times for direct connect
	• Virtual Private Gateway (VPW)
		○ Can be the target on route tables
		○ Associated with a single VPC
	• Customer Gateway (CGW)
		○ Can refer to two different things:
			§ Logical piece of configuration within AWS
			§ Physical on-premises router that the VPN connects to
		○ Either logical or physical
	• VPN connection between the VGW and CGW
		○ How we create the network virtual connection between two locations
	• Need IP range of VPC and the on-prem it'll be connecting to
		○ Also need IP Address of the router on-prem
		○ Can create a Virtual Private Gateway (VGW) and attach to AWS Public Zone
		○ Then create a VPN connection (Static or dynamic) within AWS
			§ Needs to be linked to a VGW to use the endpoints that the VGW provides
			§ Also need to create the CGW
	• VGW is highly available by design
	• 
		○ If the customer on-prem router, then everything fails
			§ Why it's not completely HA
		○ Known as "Partial HA"
			§ HA on the AWS but suffers from single point of failure on the on-prem side
		○ On-prem using multiple internet connections (ideally in different buildings)
	• Static vs Dynamic VPN (BGP)
		○ Dynamic VPN uses BGP
		○ The difference is how routes are configurated
		○ Static VPN:
			§ is simple and just uses IPSec
			§ Works almost anywhere
			§ No load balancing and multi connection failover
			§ Routes for remote side added to route tables as static routes
			§ Networks for remote side statically configured on the VPN connection
		○ Dynamic VPN:
			§ Border Gateway Protocol (BGP) is configured on both the customer and AWS side using (ASN)
			§ Networks are exchanged via BGP
			§ Multiple VPN connections provide HA and traffic distribution
			§ Can communicate the state of the links between the Virtual Private Gateway (VGW) and the Customer Gateway (CGW)
			§ Routes for remote side added to route tables as static routes
			§ Route propagation (if enabled) means routes are added to route tables automatically
	• VPN Considerations:
		○ Speed limitations
			§ 1.25 Gbps
			§ AWS limit
			§ Need to check restrictions on customer router as well
		○ Latency Considerations
			§ Inconsistent, public internet
		○ Cost
			§ AWS hourly cost
			§ GB out cost
			§ Data cap (on-premises)
		○ Speed of setup
			§ Hours
			§ All software configuration
		○ Can be used as a backup for a Direct Connect (DX)
		○ Can be used with Direct Connect (DX)

### Direct Connect (DX)
	• A 1 Gbps or 10 Gbps Network Port into AWS
	• At a DX Location (1000-Base-LX or 10GBASE-LR)
		○ 1 Gbps = 1000-Base-LX
		○ 10 Gbps = 10GBASE-LR
		○ Both use Single-mode fiber optic cables
	• You're applying to connect your equipment to the AWS port
		○ Called a cross-connect
		○ Cable from the AWS DX rack and port allocated to you and your customer router (located inside the DX location)
	• Goes to your Customer Router
		○ Requires VLANS and BGP
	• Or goes to a Partner Router (if extending to your location)
	• Need to arrange for a port to plug into that DX location and for that to be transmitted into your business premises
		○ Can take some time
	• Basic DX product provides just a port and you provide the rest
		○ Cable from the DX port all the way to your network
	• Can run Multiple Virtual Interfaces (VIFS) over one DX
		○ Each VIFS is a VLAN and BGP connection
		○ Come in two different types:
			§ Private VIF (VPC) associated with a virtual private gateway and connect into a single VPC
				□ Provide private network connectivity between a VPC and your on-premises network
				□ Can have as many private VIFS running over a single DX connection
			§ Public VIF (Public Zone Services)
				□ Provide connectivity to AWS public zone services (S3, DynamoDB, etc)
	• One physical cable between the customer/partner router and the router located on-prem
		○ No High Availability
		○ No encryption
			§ Not supported by default with DX product but can be added
	• Can take Weeks/Months for physical cable installation from customer/partner router and on-prem
	• Public VIF = Public AWS Services
		○ NO Public Internet
	• Private VIF = One VPC
		○ Multiple VPCs - you can create multiple Private VIFs
			§ Only provide to the VPC they're connected to
	• DX is more complex than VPN = provides low consistent latency and high speeds
	• DX Considerations:
		○ Takes much longer to provision vs VPN
		○ DX Port provisioning is quick but the cross-connect (between AWS port and customer router) takes longer
			§ Human has to do this
			§ Question that requests DX to be setup in one day is probably a faulty question
		○ Extension from DX location to on-prem is a physical cable run and can take weeks/months
		○ Use VPN first…then replace with DX (or leave as backup)
		○ Faster than site-to-site VPN
			§ Up to 40 Gbps with Aggregation
				□ 4 10 Gbps ports
		○ Doesn't use public internet for transit
			§ Low consistent latency
			§ Doesn't use business bandwidth
		○ Direct Connect (DX) provides no built-in encryption (Native)
			§ Completely unencrypted
			§ Things running over the top can be encrypted
				□ Can be managed on a per-application basis unless you apply workarounds
	• Application themselves might encrypt the data before or in-transit
	• When you create a Virtual Private Gateway, it creates endpoints located inside the AWS Public Zone with public IP addresses
		○ Can create a VPN and instead of using the public internet as the transit network, you can use the Public VIF running over the direct connect
			§ IPSec VPN over a public VIF
			§ The benefits of DX with the encryption of IPSec
	
### Transit Gateway (TGW)
	• Network Transit Hub to connect VPCs to on premises networks
	• Significantly reduces network complexity
	• Single network object
		○ HA
		○ Scalable
	• Attachments created to other network types
		○ How it connects to on-prem
		○ VPC, Site-to-Site VPN, and Direct Connect (DX) Gateway attachments
	• Full mesh network without Transit Gateway scales badly
		○ The more sites or VPNs, the faster the growth in connections to manage
		○ Complex with lots of admin overhead
	• Transit gateway uses a site-to-site VPN attachment
		○ Becomes the AWS side termination point for the VPN
	• With TGW, you can create attachments to VPC
		○ VPC attachments are configured with a subnet in each AZ where service is required
		○ One single TGW can route traffic between lots of different VPCs
		○ Is a transitive routing capable device
		○ VPCs talk to each other through the TGW
	• Can peer TGW with other TGW in other accounts in other regions
		○ Peering attachment
		○ Cross-region
		○ Same/Cross-account
	• Can attach TGW to Direct Connect gateways
		○ TGW can integrate with direct connect gateway using a transit VIF
			§ Allows to use the TGW with physical connections on-prem
	• TGW supports multiple route tables allowing complex routing architectures
	• Transit Gateway Considerations:
		○ Supports transitive routing
			§ Don't need to create full mesh topology
		○ Can be used to create global networks
			§ Can peer different transit gateways
		○ Share between accounts using AWS Resource Access Manager (RAM)
			§ Allows to share products/service (or components of them) between AWS accounts
		○ Peer with different regions in the same or cross-account
		○ Offers much less complexity in terms of network architectures than without transit gateways

### Storage Gateway
	• Storage Gateway is a super flexible hybrid storage appliance.
	• Its capable of running in 3 modes
		○ FILE
		○ TAPE
		○ VOLUME (Stored or Cached).
	• Understanding the features of each, and when to use those features is a key part of any hybrid infrastructure questions in the exam.
	• Hybrid Storage Virtual Appliance (On-Premises)
		○ Can be run inside AWS as part of certain disaster recovery scenarios
	• Let's you extend your storage into AWS
		○ Extension of File and Volume storage into AWS
			§ Volume = Block storage delivered over iSCSI
	• Allows you to keep volume storage hosted locally but have data replicated into AWS
		○ Volume storage backups into AWS
	• Migrate existing tape backups into AWS
		○ Can present AWS storage to backup software as a physical tape
	• Migration of existing infrastructure to AWS
	• Storage Gateway:
		○ Extension, migration, and backups
	• Runs in three main modes (must decide when creating):
		○ Tape Gateway (VTL = virtual tape library) Mode:
			§ Configures storage gateway so that backup servers think it's physical tape
			§ Virtual tapes stored on S3 and Glacier
		○ File Mode
			§ Create file shares and offer them using SMB and NFS
			§ File Storage backed by S3 Objects
			§ Great way to extend data center into AWS
		○ Volume Mode (Gateway Cache/Stored) - iSCSI
			§ Block storage backed by S3 and EBS Snapshots
	• File Gateway:
		○ Files are stored to shares using NFS or SMB
		○ Communicates with On-Premises to AWS using HTTPS and public endpoint
		○ Mapped directly 1:1 as S3 objects
		○ Lifecycle policies can automatically control Storage Classes
		○ SMB shares can integrate with Active Directory for file authorization
		○ Use if you need additional capacity or if you're decommissioning on-prem storage infrastructure
	• Tape Gateway:
		○ Storage Gateway is pretending to be a real tape backup system
			§ Pretends to be a iSCSI tape library, changer, and drive
		○ Connects back to AWS using HTPS and public endpoint
		○ Active tapes are stored in S3
		○ Archived/exported tapes are stored in VTS in Glacier
		○ Virtual tape from 100 GiB to 5 TiB
		○ 1 PB total storage across 1500 virtual tapes
		○ Unlimited VTS (Archive) Storage in AWS
		○ Wouldn't implement as a new solution
	• Volume Gateway (Stored)
		○ Storage gateway running locally on-prem
		○ 16 TB per volume, 32 Volumes (MAX), 512 TB total capacity
		○ Primary data is stored on-premises
		○ Backup Data is asynchronously replicated to AWS
		○ Block storage presented to AWS using iSCSI
		○ Connects back to AWS using HTPS and public endpoint
		○ Volumes are made available via iSCSI for network based servers to access (single connection per volume unless servers are clustered)
		○ AWS side creates EBS snapshots from backup data. Can be used to create standard EBS volumes. Ideal for migrations to AWS
		○ Can be accessed the same as normal EBS snapshots
		○ Used for disaster recovery or business continuity
		○ For Migrations and Disaster Recovery
		○ Not useful for data center extensions
	• Volume Gateway (Cached)
		○ Designed for extensions into AWS
			§ Capacity is limited or looking to decommission existing infrastructure
		○ Volumes are made available via iSCSI for network based servers to access (single connection per volume unless servers are clustered)
		○ Primary data is stored in AWS. Data which is accessed frequently is cached locally. Ideal for extended storage into AWS
		○ Primary data is stored on a S3-backed volume (AWS managed bucket) snapshots are stored as standard EBS snapshots
		○ Not storing primary copy of data locally (stored in AWS)
			§ Locally is used ONLY for frequently accessed data
		○ Connects back to AWS using HTPS and public endpoint
		○ 32 TB per volume, 32 Volumes (MAX), 1 PB total capacity
	• If you need to replace tape backup system = Tape Gateway
	• If you need to store files and transferred into S3 = File Gateway
	• If your application use Block storage (volumes):
		○ Stored
			§ Keep volumes locally but asynchronously backup to AWS
		○ Cached
			§ Extend into AWS while minimizing local infrastructure footprint

### Snowball / Edge / Snowmobile
	• Snowball, Snowball Edge and Snowmobile are three parts of the same product family designed to allow the physical transfer of data between business locations and AWS.
	• Knowing which to pick and why is essential for the solutions architect exam .. in this lesson I step through all of the key product family features.
	• Designed to move large amounts of data IN and OUT of AWS
	• Physical storage unit:
		○ Suitcase size or Truck size
	• Ordered from AWS empty, load up, return
	• Ordered from AWS with data, empty, return
	• For the exam know which to use
	• Snowball:
		○ Ordered from AWS, Log a Job, Device Delivered (not instant)
		○ Data encryption uses KMS
		○ 50 TB or 80 TB capacity
		○ Connect to the snowball using either 1 Gbps (RJ45 1GBase-TX) or 10 Gbps (LR/SR) network
			§ Must have that physical cable network connectivity on-prem
		○ 10 TB to 10 PB economical range (multiple devices)
			§ Can order multiple devices
		○ Multiple devices can be sent to multiple premises
		○ ONLY STORAGE (no compute capability)
		○ Snowball is older and purely for storage
	• Snowball Edge:
		○ Both Storage and Compute
			§ Like snowball but comes with compute capability
		○ Larger capacity vs Snowball
		○ 10 Gbps (RJ45), 10/25 (SFP), 45/50/100 Gbps (QSFP+)
		○ Storage Optimized (with EC2)
			§ 80 TB, 24 vCPU, 32 GiB RAM, 1 TB SSD (local)
		○ Compute Optimized
			§ 100 TB + 7.68 NVME, 52 vCPU, and 208 GiB RAM
		○ Compute with GPU
			§ Same as compute optimized but with GPU
			§ Good for scientific analysis, modeling, parallel processing
		○ Ideal for remote sites or where data processing on ingestion is needed
		○ Turnaround time can be quicker
	• Snowmobile
		○ Portable Data Center (DC) within a shipping container on a truck
			§ Literally a truck
		○ Special order
		○ Not available in high volume and not available everywhere
		○ Ideal for single location when 10 PB+ is required
		○ Up to 100 PB per snowmobile
		○ Expected to connect to data center grade computing
		○ Single Truck (not economical for smaller than 10 PB or for multi-site migrations)
		
### Directory Services
	• The Directory service is a product which provides managed directory service instances within AWS
	• It functions in three modes
		○ Simple AD - An implementation of Samba 4 (compatibility with basics AD functions)
		○ AWS Managed Microsoft AD - An actual Microsoft AD DS Implementation
		○ AD Connector which proxies requests back to an on-premises directory.
	• This lesson steps through the architecture of the service and explains scenarios where each might be used.
	• Directory
		○ Stores objects (e.g. Users, Groups, Computers, Servers, File Shares) with a structure (domain/tree)
		○ Multiple trees can be grouped into a forest
		○ Commonly used in Windows Environments
		○ Sign-in to multiple devices with the same username/password provides centralized management for assets
		○ Microsoft Active Directory Domain Services (AD DS)
		○ AD DS most popular, open-source alternative = SAMBA
			§ Designed to provide an alternative but only provides partial compatibility with Active Directory
	• Directory Service
		○ AWS Managed implementation
		○ No admin overhead of running your directory service
		○ Runs within a VPC (Private Service)
			§ Services that use it need to be within that VPC or private connectivity must be configured
		○ Provides HA by deploying into multiple subnets into multiple AZs within AWS
		○ Some AWS Services NEED a directory
			§ e.g. Amazon Workspaces
				□ Needs a directory registered with AWS
		○ Can be an isolated directory
			§ Inside AWS only and independent of any other directory
		○ Can be integrated with existing on-prem system
		○ Or act as a 'proxy' back to on-premises
			§ Allows you to use your existing on-prem directory with AWS services that require a registered directory service
	• Simple AD Mode:
		○ Open source directory based on SAMBA 4
		○ Provide directory with enough compatibility with AD but in a lightweight way
		○ Anything mentioning open-source/Samba then Simple AD
		○ Up to 500 Users (Small) or 5,000 users (Large)
		○ Integrates with AWS Services
			§ EC2 Instances can join SimpleAD and Workspaces can use it for logins and management
			§ Ex. Chime, Connect, QuickSight, RDS, Workdocs, Workmail, Workspaces
		○ Basically deploying a highly available version of Samba
		○ Not designed to integrate with any existing on-premises directory system such as Microsoft AD
	• AWS Managed Microsoft AD:
		○ When you want to have a direct presence inside AWS but also have an existing on-prem environment
		○ Can create a trust relationship with the existing on-prem network
			§ Must be connected with a private connection (Direct Connect or VPN)
		○ Benefit:
			§ Primary running location is in AWS
			§ Trust relationships can be created between AWS and on-prem directory systems
			§ Resilient if the VPN fails
				□ Services in AWS will still be able to access the local directory running in Directory Service
		○ Not reliant on any on-prem infrastructure
		○ Full Microsoft AD DS running in 2012 R2 Mode
			§ Microsoft AD aware applications running in AWS
		○ Supports applications which require MS AD specific Schema or Schema Updates
		○ Questions about requiring an actual implementation of MS AD with trust relationships with MS AD, then this is the mode you need to use
	• AD Connector
		○ Need to establish private network connectivity between AWS and on-prem
		○ Only a proxy
		○ Allows AWS services which NEED a directory to use an existing on-prem directory
		○ ONLY A PROXY
			§ No local functionality
		○ Primary Directory is located on-premises requests from AWS are proxied back to the existing directory
		○ Don't need to provision an additional directory service to use AWS products and services
		○ If private connectivity fails, then the AD proxy won't function - interrupting service at the AWS side
		○ Use only when you already have a directory on-prem and just want to use AWS service which require a directory but you don't want to deploy a new one
	• When to pick between different modes:
		○ Simple AD
			§ The default. Simple requirements. A directory in AWS
		○ Microsoft AD
			§ Applications in AWS which need MS AD DS, or you need to TRUST AD DS
			§ Actually an implementation of MS AD. Not emulated.
		○ AD Connector
			§ Use AWS Services which need a directory without storing any directory info in the cloud
			§ Proxy to your on-prem directory
			§ Doesn't provide functionality on its own
			
### DataSync
	• AWS DataSync is a product which can orchestrate the movement of large scale data (amounts or files) from on-premises NAS/NAS into AWS or vice-versa
	• Data Transfer service TO and FROM AWS
	• Tends to be used for workloads like Migrations into AWS, Data Processing Transfers, Archival/Cost Effective Storage, or Disaster Recover/Business Continuity
	• Designed to work at huge scale
	• Each agent can handle 10 Gbps of data transfer
	• Each job can handle up to 50 million files
	• Keeps metadata (e.g. permissions/timestamps)
	• Bult in data validation
	• Key Features:
		○ Scalable
			§ 10 Gbps per agent (~100 TB per day)
		○ Bandwidth Limiters
			§ Avoid link saturation
		○ Incremental and Scheduled transfer options
		○ Compression and encryption
		○ Automatic recovery from transit errors
		○ AWS Service Integration - S3, EFS, FSx
			§ Supports service to service transfers and cross-region
		○ Pay as you use
			§ Per GB cost for data moved
	• The DataSync Agent runs on a virtualization platform such as VMWare and communicates with the AWS DataSync Endpoint
		○ Runs on-prem
	• DataSync Agent communicates with the SAN/NAS Storage using NFS or SMB protocols
	• Agent communicates with DataSync Endpoint running on AWS
		○ Uses Encryption in-transit (TLS)
	• Locations define the SRC or DST for the sync of data TO or FROM AWS
		○ e.g. S3, EFS, FSx, NFS, SMB
	• Schedules can be set to ensure the transfer of data occurs during or avoiding specific time periods
	• Customer impact can be minimized by setting a bandwidth limit in MiB/s
	• Must have DataSync agent installed locally in on-prem
		○ Communicates with SAN/NAS storage using NFS/SMB
	• Can recover from failures and use schedules
	• Can throttle bandwidth
	• Any questions requiring reliable transfer of large quantities of data, needs to integrate with EFS/FSx/S3 and support bidirectional/incremental/scheduled transfer, then it's likely to be AWS DataSync
	• Task = A 'job' within DataSync
		○ Defines what is being synced, how quickly, FROM where, and TO where
	• Agent = software used to read or write to on-premises data stores using NFS or SMB
	• Location = Every task has two locations FROM and TO
		○ e.g. Network File Systems (NFS), Server Message Block (SMB), Amazon EFS, Amazon FSx, and Amazon S3
			§ Tend to use NFS with Linux/Unix
			§ SMB popular in Windows environments
	• If you need an electronic method of data transfer, then snowball/snowball edge are not appropriate
	• If you need to transfer data in/out of AWS, and the product needs to support schedules/throttling/automatic retries/compression and cope with huge scale transfers involving lots of different AWS and traditional file transfer protocols = DataSync
	
### FSx for Windows File Servers
	• FSx for Windows Servers provides a native windows file system as a service which can be used within AWS, or from on-premises environments via VPN or Direct Connect
	• FSx is an advanced shared file system accessible over SMB, and integrates with Active Directory (either managed, or self-hosted).
	• It provides advanced features such as VSS, Data de-duplication, backups, encryption at rest and forced encryption in transit.
	• Fully managed native windows file servers/shares
	• Designed for integration with windows environments
		○ Not an emulated file server
	• Integrates with Directory Service or Self-Managed AD
		○ Critical for enterprises that already have their own AD service
	• Can be deployed in either Single or Multi-AZ within a VPC
	• On-Demand and Scheduled Backups
	• Accessible using VPC, Peering, VPN, Direct Connect (DX)
	• Questions talking about shared file systems that mention Windows keywords (native windows file systems, active directory/directory service integration) then FSx for Windows File Servers
	• Need to determine when to use FSx or EFS
		○ EFS tends to be used for shared file systems for Linux EC2 Instances and on-prem
		○ FSx dedicated for Windows environments
	• FSx uses Active Directory for its user store
		○ Supports managed or self-managed AD (on-prem)
			§ Can integrate with both
		○ Can integrate with a completely normal implementation of AD that most enterprises already have on-prem
	• Can be shared using the typical windows implementation
		○ \\fs-xxx123.animals4life.org\catpics
	• FSx is a native windows file system
		○ Supports de-duplication (sub file), distributed file system (DFS), KMS at-rest encryption, and enforced encryption in-transit
			§ DFS = windows can group file systems together and scale out for a more managed file share structure at-scale
		○ Shares are accessed using SMB protocol
		○ Support volume shadow copies (file level versioning)
			§ Way that users can see multiple file versions and initiate restores from the client side
	• FSx is highly performant
		○ 8MB/s up to 2GB/s
		○ 100k's IOPS
		○ <1ms latency
	• Key Features and Benefits:
		○ VSS = User-Driven Restores
			§ Feature that allows users to perform file/folder-level restores
			§ Any users of workspaces that use files/folders on FSx shares, they can view and restore previous versions without having to work with System Admin
		○ Native file system accessible over SMB
			§ EFS uses the NFS protocol
				□ Only accessible from Linux EC2 Instances or Linux On-Prem Servers
			§ If SMB is mentioned, it's most likely FSx
		○ Windows permission model
		○ Supports DFS
			§ Scale-out file share structure
			§ Group file-shares together or use DFS for file replication to scale out performance
		○ Managed
			§ No file server admin
			§ No admin overhead of managing file server yourself
		○ Integrates with Directory Service AND your own directory
		
### FSx for Lustre
	• FSx for Lustre is a managed file system which uses the FSx product designed for high performance computing
	• It delivers extreme performance for scenarios such as Big Data, Machine Learning and Financial Modeling
	• https://docs.aws.amazon.com/fsx/latest/LustreGuide/performance.html#fsx-aggregate-perf
	• Managed Lustre - Designed for High Performance Computing (HPC)
		○ Supports Linux based instances running in AWS
		○ Supports POSIX style permissions for file systems
	• Typically used for machine learning, big data, financial modeling
	• Can scale to 100s GB/s throughput and sub millisecond latency
	• Lustre = One AZ Only
	• Can be provisioned using two performance types:
		○ Scratch
			§ Highly optimized for Short Term
			§ No replication
			§ Fast
		○ Persistent
			§ Longer term
			§ High availability (ON ONE AZ ONLY)
			§ Self-Healing
				□ Any hardware fails as part of the file system, it's automatically replaced by AWS
	• Accessible over VPN or Direct Connect
	• Focuses around a managed file system created by the user
		○ Can access from the VPC or anything connected to it with private networking
	• Data is 'Lazy Loaded' from S3 (S3 Linked Repository) into the file system as it's needed
		○ Only truly present in the file system when they're first accessed
		○ No synchronization
		○ Data can be exported back to S3 at any point using hsm_archive command
		○ The separate file system is where the processing of data occurs
	• Lustre splits data up when it's storing it to disks
	• Metadata stored on Metadata Targets (MST)
	• Objects are stored on object storage targets known as OSTs
		○ Each is 1.17 TiB in size
	• Baseline performance based on size of file system
		○ Size - min 1.2 TiB then increments of 2.4 TiB
	• For Scratch - Base 200 MB/s per TiB of storage
	• Persistent offers 50MB/s, 100MB/s, and 200MB/s per TiB of storage
	• Both scratch and persistent can burst up to 1,300 MB/s per TiB
		○ Based on credit system
		○ Each credits when using a performance level below the baseline and use it when you go above the baseline
	• Any writes to Lustre goes through the ENI and directly to disk
		○ Depends on the throughput and IOPS
	• Any reads from disk is based on performance characteristics (disk throughput and IOPS)
	• Any reads from cache depends on the network throughput and IOPS
	• Scratch is designed for pure performance
		○ Short-term or temporary workload
		○ Doesn't provide HA or Replication
		○ Any hardware failure will result in data being lost and not available to the file system
		○ Larger file systems means more servers, more disks, and more chance of failure
	• Persistent has replication within ONE AZ ONLY
		○ Protects against a hardware failure but not against a failure of an AZ
		○ Auto-heals when hardware failure occurs within one AZ
	• You can backup to S3 with both scratch and persistent
		○ Manual or automatic (0-35 day retention)
	• If you see Windows or SMB mentioned, then it's going to be FSx for Windows and not FSx for Lustre
	• If you see any mention of Lustre, really high-end performance requirements, POSIX, High performance computing, machine learning, big data, or any of these types of scenarios then it's going to be FSx for Lustre
	
# Security, Deployment, and Operations
### AWS Secrets Manager
	• AWS Secrets manager is a product which can manage secrets within AWS. There is some overlap between it and the SSM Parameter Store - but Secrets manager is specialised for secrets.
	• Additionally Secrets managed is capable of automatic credential rotation using Lambda.
	• For supported services it can even adjust the credentials of the service itself.
	• Inside Parameter Store, you can create secure strings which allow you to store passwords = NOT SECRETS MANAGER
	• Secrets Manager shares functionality with Parameter Store
	• Designed specifically for secrets:
		○ Passwords and API Keys
	• Usable from the Console, CLI, API, or SDK's (integration)
		○ Integrated with other applications
	• Supports automatic rotation of secrets using Lambda
	• Directly integrates with some AWS products (RDS)
	• Lambda is invoked periodically to rotate secrets
		○ Products such as RDS are kept in sync
		○ This is what sets Secrets Manager apart from Parameter Store
			§ Parameter store cannot rotate secrets
	• Secrets are stored using KMS
		○ Ensures role separation
			§ Need permissions to both KMS and Secrets Manager
	• If question mentions anything like secrets and/or rotation (or even RDS), then it's most likely Secrets Manager
	• If question mentions storing hierarchical configuration information, configuration of Cloudwatch agent then it typically means Parameter Store
	
### AWS WAF and Shield
	• AWS Shield and Web Application Firewall (WAF) are both products which provide perimeter defence for AWS networks.
	• Shield provides DDOS protection and WAF is a Layer 7 Application Firewall.
	• https://www.cloudflare.com/en-au/learning/ddos/what-is-a-ddos-attack/
	• Web Application Firewall (WAF)
	• AWS Shield:
		○ Provides AWS resources with Distributed Denial of Service (DDoS) protection
		○ Comes in two versions:
			§ Standard - free with Route53 and CloudFront
				□ Protection against Layer 3 and Layer 4 DDoS attacks
			§ Advanced - $3,000 per month
				□ Protects EC2, ELB, CloudFront, Global Accelerator, and Route 53
				□ Provides access to 24/7 365 advanced DDoS Response Team and Financial Insurance
	• Web Application Firewall (WAF):
		○ Application Layer 7 (HTTP/S) Firewall
		○ Protects against complex Layer 7 attacks/exploits
			§ SQL Injections, Cross-site scripting, Geo Blocks, Rate Awareness
		○ Web Access Control List (WebACL) integrated with ALB, API Gateway, and CloudFront
		○ Rules are added to a WebACL and evaluated when traffic arrives
		○ Functions at the edge and can be integrated with ALB, API Gateway, and CloudFront
	• WAF Rules are defined, included in a WebACL which is associated to a CloudFront distribution and deployed to the edge. The WebACL filters traffic at the edge
	• AWS Shield provides Layer 3 and 4 DDoS protection for the ALB, CloudFront, and on requests via Route53
	• DDoS = Shield
	• Layer 7 filtering, HTTP filtering, HTTPS filter = WAF
	• Both provide global perimeter protection
	
### CloudHSM
	• In this lesson I step through the architecture and features of CloudHSM - an AWS provided Hardware Security Module products.
	• CloudHSM is required to achieve compliance with certain security standards such as FIPS 140-2 Level 3
	• https://en.wikipedia.org/wiki/FIPS_140-2
	• Similar to KMS
		○ Creates, manages, and secures cryptographic material (keys)
	• With Key Management Service (KMS)… AWS Manage…Shared but separate
		○ Shared service that is used by other accounts within AWS uses = bad
	• Hardware Security Module = used by KMS in order to manage keys and perform cryptographic operations
	• CloudHSM = true "single tenant" hardware security module (HSM)
	• CloudHSM = AWS provisioned but fully customer managed
	• Standard for cryptographic modules = Federal Information Processing Standard Publication 140-2
		○ Can determine capability of any HSM modules based on compliance with this
	• CloudHSM = Full FIPS 140-2 Level 3 (KMS is L2 Overall, some L3)
	• Exam question that requires 140-2 Level 3, then have to use CloudHSM or on-prem HSM device
	• KMS uses AWS standard APIs
	• CloudHSM accessed with Industry Standard APIs
		○ PKCS#11, Java Cryptography Extensions (JCE), Microsoft CryptoNG (CNG) libraries
	• KMS can use CloudHSM as a custom key store
		○ CloudHSM integration with KMS
	• Deployed into an AWS managed CloudHSM VPC that the user doesn't have any visibility to
	• HSMs keep keys and policies in sync when nodes are added/removed
	• HSMs operate in an AWS managed HSM VPC. Interfaces are added to customer VPC
	• AWS Provision HSM but have no access to secure area where key material is held
	• AWS CloudHSM Client located in customer VPC and connects to CloudHSM VPC
	• CloudHSM Use Cases:
		○ No Native AWS integration
			§ No S3 SSE
		○ Offload the SSL/TLS processing for Web Servers
			§ Much more economical/efficient to have CloudHSM device performing those cryptographic services
		○ Enable Transparent Data Encryption (TDE) for Oracle Databases
		○ Protect the Private Keys for an Issuing Certificate Authority (CA)
	• For anything that's not specific to AWS, then CloudHSM is ideal
		○ Anything that uses standards or has to integrate into AWS
	
# NoSQL Databases and DynamoDB
### DynamoDB - Architecture
	• DynamoDB is a NoSQL fully managed Database-as-a-Service (DBaaS) product available within AWS.
	• NoSQL Public Database-as-a-Service (DBaaS)
		○ Capable of handling simple key/value data or data with a structure like DocumentDB model
		○ Accessible anywhere with access to the public endpoints of DynamoDB
		○ Wide-column key/value
	• No self-managed servers or infrastructure
	• Manual/Automatic provisioned performance IN/OUT or On-Demand
		○ On-demand mode = true as-a-service model
	• Highly Resilient
		○ Across AZs and optionally globally resilient
	• Data replicated across multiple storage nodes by default
	• Really Fast
		○ Single-digit milliseconds (SSD Based)
	• Backups, point-in-time recovery, encryption at rest
	• Event-Driven integration
		○ Do things when data changes
	• Tables:
		○ A Table is a grouping of ITEMS with the same PRIMARY KEY
		○ Item = row in traditional database product
		○ Table can have an infinite number of items
		○ Primary Key (PK):
			§ Simple (Partition)
			§ Composite (Partition and Sort Key (SK))
		○ Each item MUST have a unique value for PK and SK
			§ Can have none, all, mixture, or different attributes (DDB has no rigid attribute schema)
		○ ITEM MAX = 400 KB
		○ On-Demand capacity model
			§ Don't have to set explicit values for capacity on a table
			§ Pay for operations against the DDB table
		○ Provisioned Capacity
			§ Explicitly set the capacity values on a per-table basis
		○ Capacity (Speed) is set on a table
			§ (Writes) 1 WCU = 1KB per second
			§ (Reads) 1 RCU = 4KB per second
	• Backups:
		○ On-Demand Backups
			§ Full backup of the table retained until you manually remove that backup
			§ Can restore to same region or cross-region
			§ Can use backup to store with or without indexes
			§ Can adjust encryption settings as part of the restore
			§ You're responsible for performing and removing backups
		○ Point-in-time Recovery (PITR)
			§ Enabled on a table-by-table basis and NOT ENABLED BY DEFAULT
			§ Continuous record of changes allows replay to any point in the window
			§ 35 day recovery window
				□ Can restore to a new table with a 1 second granularity
	• Any questions mentioning NoSQL then preference DynamoDB in the exam
	• Any questions mentioning relational data then generally NOT DynamoDB
		○ DDB should not be used to implement any relational database system
		○ Not designed for that and doesn't include required features
	• Any questions mentioning Key/Value then preference DynamoDB in the exam
	• Access via console, CLI, or API… DON'T HAVE SQL WHEN USING DDB
		○ Any questions mentioning SQL, then it probably excludes DDB
	• Billed based on RCU, WCU, Storage, and Features
		○ True On-Demand DB product
		○ Pay only for resources you consume
		○ Can purchase reserved allocations for capacity

### DynamoDB - Operations, Consistency, and Performance
	• On-Demand Capacity Mode:
		○ Designed when you have an unknown or unpredictable level of load on a DDB table
		○ Or when you have priority for as little admin overhead as possible
		○ Don't need to explicitly set capacity settings
		○ Pay price per million of read or write units (RCU/WCU)
			§ Price you pay can be as much as 5x provisioned capacity
	• Provisioned Capacity Mode:
		○ RCU and WCU set on a per table basis
	• Every operation consumes at least 1RCU/WCU
		○ 1 RCU is 1 x 4KB read operation per second
		○ 1 WCU is 1 x 1KB write operation per second
	• Every table has a RCU and WCU burst pool (300 seconds)
	• Types of Operations:
		○ Query
			§ Retrieve data from the product
			§ Start with Partition Key 
			§ Query accepts a single PK value and optionally a scan key (SK) or range
			§ Capacity consumed is the size of all returned items
			§ Further filtering discards data - capacity is still consumed
			§ Can ONLY query on PK or PK and SK
			§ Always more efficient to return multiple items in a single operation
			§ Every operation consumes at least 1 RCU
			§ Generally operating an entirety of the item
			§ Anything you're filtering on an item will not be returned but you will still be charged for the entire item
			§ Query operation can only ever query based on a particular PK value
		○ Scan
			§ Least efficient operation but most flexible
			§ SCAN moves through a table consuming the capacity of every ITEM
			§ You have complete control an what data is selected, any attributes can be used, and any filters applied
			§ BUT SCAN consumes capacity for every ITEM scanned through
			§ Scans through entire table
				□ Consumes all the data that you scan through
	• Two consistency modes:
		○ Eventually consistent reads:
			§ Eventually consistent reads check 1 of the storage nodes at random
			§ Could be unlucky with stale data if a node is checked before replication completes
			§ 50% of the cost vs strongly consistent
			§ Not every application or access type can tolerate eventual consistency
		○ Strongly (immediately) consistent reads:
			§ More costly and scales less well than eventually consistent
			§ Strongly consistent reads connect to the leader node to get the most up-to-date copy of data
		○ Consistency = when new data is written to the database and immediately read, is that read data immediately the same as what was uploaded or eventually the same
		○ Leader Storage Node:
			§ If leader ever fails, election happens and a new is chosen
		○ DynamoDB directs writes at the leader storage node which is elected from the storage nodes
		○ The leader node replicates data to other nodes, typically finishing within a few milliseconds
	• WCU Calculation:
		○ If you need to store 10 ITEMS per second…2.5KB average size per ITEM
		○ Calculate WCU per item…Round Up (ITEM Size / 1KB) = 3
		○ Multiply by average number per second (30)
		○ = WCU Required (30)
	• RCU Calculation:
		○ If you need to retrieve 10 ITEMS per second…2.5KB average size
		○ Calculate RCU per ITEM…Round Up (ITEM Size / 4KB) = 1
		○ Multiply by average number per second (10)
		○ = Strongly Consistent RCU Required (10)
		○ (50% of strongly consistent) = Eventually Consistent RCU Required (5)
	
### DyanmoDB - Streams and Lambda Triggers
	• DynamoDB Streams are a 24 hour rolling window of time ordered changes to ITEMS in a DynamoDB table
	• Streams have to be enabled on a per table basis , and have 4 view types:
		○ KEYS_ONLY
			§ Stream will only record the partition key and optionally any applicable sort key value for the item that is changed
			§ Up to stream to determine what has changed
		○ NEW_IMAGE
			§ Stores the entire ITEM with the state as it was after the change
		○ OLD_IMAGE
			§ Store copy of data before the change
		○ NEW_AND_OLD_IMAGES
			§ Actual entry in the stream stores both the pre/post change of that item
			§ If inserting/deleting, the old/new images will be empty
	• Lambda can be integrated to provide trigger functionality - invoking when new entries are added on the stream.
	• Stream = Time ordered list of ITEM CHANGES in a table
		○ 24-hour rolling window
		○ Uses Kinesis streams
		○ Enabled on a per table basis
		○ Records INSERTS, UPDATES, DELETES
		○ Different view types influence what is in the stream
	• View types works as well with inserted/deleted items
	• Database Triggers:
		○ Allow for actions to take place in the event of a change in data
		○ ITEM changes generate an event
		○ That event contains the data which changed
		○ An action is taken using that data
		○ AWS = Streams AND Lambda
		○ Use Lambda to perform a compute operation in response to a data change that caused a stream event
		○ Streams and Triggers good for Reporting and Analytics scenarios
			§ Also good for data aggregation, messaging, or notifications
	• Use Streams and Triggers together to implement a Trigger Architecture in DynamoDB
	
### DynamoDB Local (LSI) and Global Secondary Indexes (GSI)
	• Local Secondary Indexes (LSI) and Global Secondary Indexes (GSI) allow for an alternative presentation of data stored in a base table.
	• LSI allow for alternative SK's whereas with GSIs you can use alternative PK and SK.
	• Query is the most efficient operation in DDB
	• Query can only work on 1 PK value at a time and optionally a single or range of Sort Key values
	• Indexes are alternative views on table data
	• Local Secondary Index (LSI) allows you to create a view using a different Sort Key (SK)
	• Global Secondary Index (GSI) allows you to create a view using a different Partition Key (PK) and Sort Key (SK)
	• When creating the indexes, you can choose which attributes from the base table are projected into them
		○ Some or all attributes (Projection)
	• LSI:
		○ Alternative view on base table data
			§ Allow for alternative sort key for the data in the main tables
			§ Same partition key
		○ Must be created with the base table itself
		○ Cannot add LSI after the base table has been created
		○ Max of 5 LSIs per base table
		○ Alternative SK on the table
		○ Shares the RCU and WCU with the table
		○ Attributes - ALL, KEYS_ONLY, and INCLUDE
		○ LSIs are an alternative view on the base table data using the same PK and a different SK
		○ Indexes are sparse
			§ Only items which have a value in the index alternative sort key are added to the index
		○ Uses same PK
	• GSI:
		○ Can be created at any time
		○ Default limit of 20 per base table
		○ Can define a different PK and SK
		○ Have their own RCU and WCU allocations
		○ Attributes - ALL, KEYS_ONLY, and INCLUDE
		○ GSIs are an alternative view on the base table with alternative PK and SK
			§ They have their own RCU and WCU and can be created at any time
		○ GSIs are sparse
			§ Only ITEMS which have values in the new PK and optional SK are added
		○ GSIs are always eventually consistent
			§ Replication between base and GSI is Asynchronous
	• Careful with projection (KEYS_ONLY, INCLUDE, ALL)
	• Queries on attributes NOT projected are expensive
	• Use GSIs as default and LSI only when strong consistency is required
	• Use indexes for alternative access patterns

### DynamoDB - Global Tables
	• DynamoDB Global Tables provides multi-master global replication of DynamoDB tables which can be used for performance, HA or DR/BC reasons
	• Global tables provides multi-master cross-region replication
	• Tables are created in multiple regions and added to the same global table (becoming replica tables)
	• Last writer wins is used for conflict resolution
		○ Simple
		○ Generates predictable outcomes
		○ DynamoDB picks the most recent write and replicates that to all the other replica tables that are part of the global table
	• Reads and Writes can occur to any region
	• Generally sub-second replication between regions
	• Strongly consistent reads ONLY in the same region as writes
		○ Anything else, it's always eventual consistency
	• Replication is generally sub-second and depends on the load of each of the regions
	• Global eventual consistency
	• Same-region eventual or strongly consistent
	• Multi-master replication
		○ All regions can be used for both read and write operations
	• Provides Global HA and Global Disaster Recovery (DR)/Business Continuity (BC)
	• Last writer wins conflict resolution
	
### DynamoDB - Accelerator (DAX)
	• DynamoDB Accelerator (DAX) is an in-memory cache designed specifically for DynamoDB. It should be your default choice for any DynamoDB caching related questions.
	• Traditional Cache:
		○ Application checks cache for data - a CACHE MISS occurs if data isn't cached
		○ Data is loaded from the database with a separate operation and SDK
		○ Cache is updated with retrieved data. Subsequent queries will load data from cache as a CACHE HIT
		○ Problem = lack of integration between cache and DB
	• DAX:
		○ Application uses the DAX SDK and makes a single call for the data which is returned by DAX
		○ DAX either returns the data from its cache or retrieves it from the database and then caches it
		○ Less complexity for the app developer - tighter integration
		○ Designed for DDB
	• Operates from within a VPC and designed to be deployed into multiple AZs in that VPC
	• DAX = cluster service
		○ Nodes placed in different AZs
		○ Primary and replica nodes
	• Maintains two different caches:
		○ Item cache holds results of (Batch) GetItem
			§ Operates on single items
			§ Must specify items partition key and if present, the sort key
		○ Query cache holds data based on query/scan parameters
			§ Stores the parameters used in that query/scan
	• DAX is accessed via an endpoint
		○ Cache HITS are returned in microseconds
		○ Misses are returned in milliseconds
	• When writing, DAX can use write-through caching
		○ Write-through is supported
		○ Data is written to DDB then DAX
	• If a CACHE MISS occurs, data is also written to the primary node of the cluster
	• Primary Node supports write operations
	• Replicas support read operations
	• Nodes are HA
		○ Primary failure results in an election
			§ New primary node is determined
	• DAX = In-memory cache
		○ Allows for much faster read operations and reduced costs
	• Can either scale UP or scale OUT
		○ UP = BIGGER INSTANCES
		○ OUT = MORE INSTANCES
	• Supports write-through
	• DAX deployed within a VPC
		○ Any application using DAX will need to be deployed in that VPC
	• Choosing between DAX and something else hinges on how much admin overhead you want
	• If applications require strongly consistent reads then DAX will not be suitable
	• If applications is write heavy and very infrequently uses read operations then DAX may not be suitable
	
### Amazon Athena
	• Amazon Athena is serverless querying service which allows for ad-hoc questions where billing is based on the amount of data consumed.
	• Athena is an underrated service capable of working with unstructured, semi-structured or structured data.
	• Serverless Interactive Querying Service
	• Can take data, store it in S3, and perform Ad-Hoc queries on that data
		○ Pay only data consumed while running the query and the storage used
	• Schema-On-Read (table-like translation)
		○ Original data is never changed and remains on S3 in original form
		○ Schema translates data as it's read into a table-like structure that you define in advanced
			§ Schema translates data => relational-like when read
	• ETL = Extract, Transform, Load
		○ Not required in Athena
	• Output can be sent to other services
		○ Visualizations, analysis, etc
	• Architecture
		○ Source data stored on S3
			§ Read Only
			§ Supports standard formats of structured, semi-structured, and unstructured data
			§ Source data is stored on S3
			§ Athena can directly read many AWS data formats such as CloudTrail, ELB Logs, and Flow Logs
			§ Fixed and does not change
		○ Inside the product, you create a schema
			§ Used at the time of querying
		○ Inside the schema, you define tables
			§ Define how to get from the format of the original source data to a table structure
			§ Tables are defined in advance in a data catalog and data is projected through when read
			§ It allows SQL-like queries on data without transforming source data
		○ Output can be sent to visualization tools
		○ No base/constant cost
		○ Billed based on data consumed during query
	• Any questions talking about data being stored inside S3, data is structure/semi-structured/unstructured, and you need to perform Ad-Hoc queries where you're charged for perfoming those queries = Athena most likely
	• Planet OSM
		○ Provides an open set of data maintained and delivered as a set of large data files
			§ Not structured into tables
	• Schema-on-read
		○ 'Tables' are defined in-advance and as data is read through
		○ It's transformed on the fly into that table structure
		○ The original data is unchanged
		
### Elasticache
	• Elasticache is a managed in-memory cache which provides a managed implementation of the redis or memcached engines.
	• It's useful for read heavy workloads, scaling reads in a cost effective way and allowing for externally hosted user session state.
	• https://aws.amazon.com/elasticache/pricing/
	• In-memory database for applications with high performance requirements
	• Managed Redis and Memcached engines
		○ Delivered as-a-service
	• Can be used to cache data for READ HEAVY workloads with low latency requirements
	• Reduces database workloads (expensive)
	• Can be used to store Session Data (Stateless Servers)
	• Requires application code changes
		○ Application needs to understand a caching architecture
		○ Needs to know to look for cache
		○ Needs to write data and understand cache invalidation
	• An in-memory cache allows cost effective scaling of read-heavy workloads and performance improvements at scale
	• Session State Data:
		○ Session data is written and kept updated using Elasticache
		○ If an instance fails, the user connection is moved to another instance by the load balancer
			§ Session State loaded from cache
			§ Session continues with no interruption
	• Two Engines used by Elasticache:
		○ Memcached:
			§ Supports simple data structures only:
				□ String
			§ No replication
			§ Multiple Nodes (Sharding)
			§ No backups
			§ Multi-threaded by design
				□ Can take better advantage of multi-core CPUs
				□ Better performance when using multi-core CPUs
		○ Redis:
			§ Supports advanced structures:
				□ Lists, sets, sorted sets, hashes, bit arrays, and more
			§ Supports replication of data across multiple AZs
				□ HA by design and can be used to scale reads by using replicas
			§ Replication (Scale Reads)
			§ Supports Backup and Restore
				□ Cache can be restores to previous state after a failure
			§ Transactions:
				□ Treat multiple operations as one (all operations work or none do)
		○ Both:
			§ Offer sub-millisecond access to data
			§ Support a range of programming languages
	
### Redshift Architecture
	• Redshift is a column based, petabyte scale, data warehousing product within AWS
	• It's designed for OLTP products within AWS/on-premises to add data to for long term processing, aggregation and tending.
	• Petabyte-scale Data warehouse
		○ Location where many different operational databases from across a business can pump data into for long-term analysis and trending
		○ Designed for reporting and analytics
		○ Not for operational
	• Online Analytical Processing OLAP (Column based)
		○ Designed for complex queries to analyze aggregated historical data from OLTP systems
			§ OLTP puts data into OLAP for more detailed, long-term analysis and trending
	• NOT Online Transaction Processing OLTP (row-transaction)
		○ Captures and stores data from transactions in real time
		○ Ex. Used for adding orders for online store
		○ Inserts, modifies, deletes
	• Redshift stores data in Columns
	• Delivered as a service like RDS
		○ Quick to provision
		○ Pay as you use
	• Direct Query S3 using Redshift Spectrum
		○ Don't need to load S3 in advance
		○ Need Redshift Cluster
	• Direct Query other DBs using federated query
		○ Can query data stored in remote data sources
	• Integrates with AWS tooling such as Quicksight
	• SQL-like interface JDBC/ODBC connections
	• Architecture:
		○ Server based (not serverless)
		○ Not normally used with Ad-Hoc queries for large-scale datasets on S3
			§ Look to Athena
		○ Uses cluster architecture on private network
			§ Runs with multiple nodes
		○ One AZ in a VPC
			§ Not HA by design
			§ Network cost/performance
		○ Leader Node - Query input, planning, and aggregation
			§ Manages communications with client programs and the compute nodes
			§ Develops execution plans to carry out complex queries
			§ Manages distributing data to the slices
		○ Compute Node - performing queries of data
			§ Queries assigned by Leader Node
			§ Partitioned into slices that are allocated a portion of the nodes memory and disk space
				□ Slices work in parallel to complete the operation
				□ Could have 2, 4, 16, or 32 slices
		○ VPC Service:
			§ VPC Security controls, IAM Permissions, KMS at rest encryption, CloudWatch monitoring
		○ Redshift Enhanced VPC Routing - VPC Networking
			§ Default - Redshift uses public routes for traffic when communicating with external services or any AWS services such as S3 when it's loading in data
			§ Traffic routed based on VPC networking configuration
				□ Can be controlled by Security Groups, NACLs
			§ Any customized networking requirements MUST enable VPC Routing
	• Anything outside of the cluster connects to leader node in order to interact with the cluster
		○ Connect with standard JDBC / ODBC compatible applications and visualization suites
		○ Supports most standard applications
			§ e.g. SQL Workbench
	• Data is replicated to 1 additional node when written
		○ System can cope with hardware failure
	• Automatic snapshots to S3 (every 8 hours or 5GB) with retention
	• Manual snapshots to S3 - managed by administrator
		○ Must manage retention
	• These automatic and manual snapshots offer regional resilience
	• Can configure snapshots to be automatically copied across AWS regions - provides global resilience and allows you to create another Redshift cluster in another region
		○ Snapshots configured to copy to another AWS region
		○ Good for DR event
	• Can load/unload data from S3, copy from DynamoDB, migrate data into Redshift using DMS, or stream data using Kinesis Firehose
	
### Redshift Disaster Recovery (DR) and Resilience
	• Redshift runs from only one Availability Zone
		○ If that AZ fails, the entire cluster will fail
	• Can utilize S3 for backups in the form of Snapshots
		○ Automatic incremental backups occur every ~8 hours or 5GB of data and by default have a 1-day retention
			§ Configurable up to 35 days
		○ Manual snaps can be taken at any time and deleted by an admin as required
	• Redshift not resilient across AZs but the data managed by Redshift can be with these backups
		○ Redshift backups into S3 protect against AZ failures
	• Redshift can be configured to copy snapshots to another region for DR with a separate configurable retention period
		○ Regional resilience
