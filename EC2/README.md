# EC2

**Features:**
- Elastic compute cloud
- Virtual computing environments, known as **instances**
- Preconfigured templates for your instances, known as **Amazon Machine Images (AMIs)**, that package the bits you need for your server (including the operating system and additional software)
- Various configurations of CPU, memory, storage, and networking capacity for your instances, known as **instance types**
- Secure login information for your instances using key pairs (AWS stores the public key, and you store the private key in a secure place)
- Storage volumes for temporary data that's deleted when you stop or terminate your instance, known as **instance store** volumes
- Persistent storage volumes for your data using **Amazon Elastic Block Store (Amazon EBS)**, known as Amazon EBS volumes
- Multiple physical locations for your resources, such as instances and Amazon EBS volumes, known as Regions and Availability Zones
- A firewall that enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups
- Static IPv4 addresses for dynamic cloud computing, known as **Elastic IP** addresses.
  - IPv4 allows for 3.7 billion different addresses in the public space
  - IPv4: [0-255].[0-255].[0-255].[0-255].
  - |Public IP|Private IP   |
    | ------------ | ------------ |
    | Identified on internet WWW  | Indentified on private n/w only   |
    | Unique across whole web  | Unique across private n/w , 2 separate private n/w can have  same range of private IP(s)|
    | Geo-located  | Connect to internet via internet gateway  |
    | Wide range of public IP(s)  | Limited Private IP(s)  |
- Metadata, known as tags, that you can create and assign to your Amazon EC2 resources
- Virtual networks you can create that are logically isolated from the rest of the AWS cloud, and that you can optionally connect to your own network, known as **virtual private clouds (VPCs)**


**Elastic IP:**
- Restarting EC2 instance changes public IP
- For fixed public IP use Elastic IP
- Only attach 1 instance at a time
- By default 4 Elastic IP(s) for an account
- Not a good architecture


**EC2 User data:**
- Bootstrap(launching commands) when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
  - Installing updates
  - Installing software
  - Downloading common files from the internet
  - Anything you can think of
- The EC2 User Data Script runs with the root user


**EC2 Instance Launch Types:**
- **On demand**
  - Pay-per-use model, no upfront cost
  - Recommended for short-term and un-interrupted workloads, where 
you can't predict how the application will behave
- **Reserve instance**
  - Reservation period can be 1 or 3 years
  - Reserve a specific instance type
  - Recommended for steady state usage applications (think database)
  - **Convertible Reserved Instance**
    - can change the EC2 instance type
    - Up to 54% discount
  - **Scheduled Reserved Instances**
    - launch within time window you reserve
    - When you require a fraction of day / week / month
 - **Spot Instances**
    - You bid a price and get the instance as long as its under the price
    - Price varies based on offer and demand
    - Spot instances are reclaimed with a 2 minute notification warning when 
the spot price goes above your bid
    - Used for batch jobs, Big Data analysis, or workloads that are resilient to 
failures.
 - **Dedicated Hosts**
    - Physical dedicated EC2 server for your use
    - Full control of EC2 Instance placement
    - Visibility into the underlying sockets / physical cores of the hardware
    - Allocated for your account for a 3 year period reservation
    - More expensive
    - Useful for software that have complicated licensing model (BYOL–Bring Your Own License) Or for companies that have strong regulatory or compliance needs
 - **Dedicated Instances:**
    - Instances running on hardware that’s dedicated to you
    - May share hardware with other instances in same account
    - No control over instance placement (can move hardware after Stop / Start)

**EC2 Instance Type:**
  - R: applications that needs a lot of RAM – in-memory caches
  - C: applications that needs good CPU – compute / databases
  - M: applications that are balanced (think “medium”) – general / web app
  - I: applications that need good local I/O (instance storage) – databases
  - G: applications that need a GPU – video rendering / machine learning
  - T2 / T3: burstable instances (up to a capacity) - When CPU goes beyon certain capacity.
  - T2 / T3 - unlimited: unlimited burst

**AMI:**
  - Amazon Machine Image
  - Can be built on Linux or Windows Machine
  - **Advantages:**
    - Pre-installed packages
    - Faster boot time
    - Can pre load softwares for monitoring security etc.
    - Control on maintainence and update
  - Built for a specific region
  - Public AMI(s) can be used from Amazon Marketplace.
  - AMI(s) are stored in S3 and are private and locked for the region by default
  - Can make the AMI(s) public and share with other accounts or users using Amazon Marketplace.
  
  - **Cross Account AMI copy:**
    - You can share an AMI with another AWS account. 
    - Sharing an AMI does not affect the ownership of the AMI. 
    - If you copy an AMI that has been shared with your account, you are the owner of the target AMI in 
your account. 
    - To copy an AMI that was shared with you from another account, the owner of the source AMI must 
grant you read permissions for the storage that backs the AMI, either the associated EBS snapshot 
(for an Amazon EBS-backed AMI) or an associated S3 bucket (for an instance store-backed AMI).
    - Limits:
        - You can't copy an encrypted AMI that was shared with you from another account. Instead, if the 
underlying snapshot and encryption key were shared with you, you can copy the snapshot while re-
encrypting it with a key of your own. You own the copied snapshot, and can register it as a new AMI.
        - You can't copy an AMI with an associated billingProduct code that was shared with you from another 
account. This includes Windows AMIs and AMIs from the AWS Marketplace. To copy a shared AMI 
with a billingProduct code, launch an EC2 instance in your account using the shared AMI and then 
create an AMI from the instance

**Placement Group:**
- Placement stratergy for EC2 instances
- Types:
    - Cluster
      
