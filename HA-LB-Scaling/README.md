**Scalability**
- Ability to handle greater loads
- Types:
	- Vertical Scalability
		- Increasing size of the instance
		- Can be used for Databases, non distributed applications
		- e.g. RDS, ElasticCache 
		- Hardware limit exists
	- Horizontal Scalability
		- Increasing no of instances
		- Can be used of web apps, distributed applications
		- e.g. increasing the no of EC2 instance.

**High Availability**
- Passive - Multi AZ
- Active - Horizontal scaling

**Load Balancing**
 - Distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions
 - Single Availability Zone or across multiple Availability Zones
 - Supports both internal and external LB's
 - **Type of Load Balancers**:
	 - **Classic Load Balancers**:
		 - Request & Connection level
		 - For EC2-Classic Network
		 - single Availability Zone or multiple Availability Zones
		 - Detect health of EC2 instances
		 - SSL Offloading
		 - Sticky sessions - based on user cookies
		 - Supports IPV4 and IPV6  
	- **Application Load Balancers**:
		- Layer 7
		- HTTP termination
		- Server Name indication(SNI) for specifying hostname to connect to 
		- Targets : IP address, Lambda, Containers, EC2 instances.
		- Routing : Host, path, HTTP header and method, Query string parameter, Source IP address CIDR.
		- Port mapping to redirect to dynamic port
		- IP of the client is inserted in **X-Forwarded-For**, port - **X-Forwarded-Port**, Proto - **X-Forwarded-Proto**
	- **Network Load Balancers**:
		 - Layer 4
	      - TCP based
	      - High throughput, low latency
	      - Supports source IP, static IP, Elastic IP 
	  
 - **Cross Zone load balancing**:
          -  If Enabled - Equal traffic across all instances across Target group.
          - If Disabled - Split traffic among Target groups.
          - NLB - disabled, ALB - enabled, CLB - disabled in CLI/SDK/API mode and enabled in Console.
  
 - **Stickiness**:
		  - Works for CLB and ALB
		  - User does not lose session data, makes use of cookies
		  - Load on instances would be high if enabled. 

	      

