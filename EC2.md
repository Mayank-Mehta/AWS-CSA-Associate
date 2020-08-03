## Elastic Cloud compute

- Virtual Machine in cloud

### Benefits
 - Time to market
 - Scalablity
 - Reliability
 - Security
 - Control
 - services Integration - RDS, AWS mail
 - Cost efficiency
 
 ### EC2 deployment
 1. AMI (Amazon Machine Image)- Snapshot of virtual machine at particular configuration state.
 2. Configure networking/security
 3. Choose Instance type
 4. Choose Availablity zone
 5. attach storage (EBS)
 6. start instance.
 
 ### EC2 Instance types
 
 - General Purpose
   - T2, M5, M4, M3
   - balance of memory and network resource
   - T2 provide burst performance - credits are build for idle time, credit used to burst performance.
 
 - Comupte Optimized
   - C3,C4,C5
   - CPU instensive application -> Media coding, Intensive batch jobs, gaming servers etc..
  
 - Memory Optimized
   - R3, R4, X1e, X1
   - High memory requirement - Processing large data sets, In memory database, Big data processing.
  
 - Storage optimized
   - H1, I3, D2
   - High sequential read/write to local storage -> Relational database, Datawarehousing, Image storage and processing
  
 - Advance computing
   - P3, P2, G3 and F1
   - special hardware compute requirement -> GPU, FPGA
  
## EC2 pricing

https://aws.amazon.com/ec2/pricing/

- On Demand
  - Charged for usage time at a flat rate
  - 60 sec increments rounded up

- Reserved
  - Hours 
  - Reserve usage minimum 1 year
  - Can be less expensive than on-demand
  - all upfront, partial upfront, no up-front
  
- Spot
  - Bid on unused compute time
  - up to 90% discount on on-demand
  
# EBS 
 - persistent block storage
 - Requires an EBS optimized instance
 - Magnetic or SSD - General purpose or PIOPS
 
# EC2 setup
- ec2-user is default user
- key pair would be required to access this EC2 instance from outside

# Tenancy
 ## Shared Tenancy
  - Multiple customers share the time and space on the physical machine
  - Default behaviour
  - Pros:
    - Reduced costs
    - Simpler deployment
  - Cons
    - Lower performance
    - Less control - at physical infra level
    - on restart, we dont know which host your instance will come on.
  ## Dedicated Host
   - Physical Machine - Run the virtual machines
   - Used by one customer
   - Must be explicitly configured
   - Not available in free tier
   - Pros:
    - More accurate licensing management
    - Compliance management
    - determine host placement during instance restarts.
   Cons:
    - More cost.
    - Also allows BYOL : bring your own licence.
    
 ## Dedicated Instance 
   - Runs on a physical machine
    - Only instance running on that machine
    - On restart, may be moved to one of customer another machine.
   - Used by one customer
   - Must be explicitly configured
   - Pros:
    - runs on hardware dedicated to the customer
    - Provides performance advantage of a dedicated host
   - Cons:
    - less accurate licensing management.
   
 # AMI Virtualisation
  - Blueprint with server configuration details
  - Similar to localized imaging solutions
  - All instances are created from an AMI
  - Sources
   - Amazon (free)
   - AWS marketplace (free/$)
   - Community (free)
  - Launching AMI
   - public : Anyone
   - Explicit: Specified
   - Implicity: Owner
   - Default is implicit
   
   ## HVM AMIs
   - Hardware Virtual Machine
    - AMIs fully virtualizes hardware
    - Requires hardware-assisted virtualization
    
   ## PV AMIs
   - Paravirtual
    - Run on hosts without specific support for virtualization
    - Doesn't perform as well as HVM AMIs
    
   ## Instance Root Volume
   
   - Contains the boot sector
   - Boot sector initiates the boot loader
   - Boot loader launches the OS.
   - Two Types: instance store-backed AMI, EBS-backed AMI
   - Store backed AMI 
     - Root volume is stored in S3
     - No support for stop action - instance always terminated
     - On failure, data in the instance store is lost.
   - EBS backed AMI
     - Root volume is stored in an EBS volume
     - Support for the stop action
     - On failure, data in the EBS volume is not lost.
    
 
