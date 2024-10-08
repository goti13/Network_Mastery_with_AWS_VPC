# Network Mastery with AWS VPC

## Project Goals:
* Understand the fundamentals of Virtual Private Cloud (VPC) and its components.
* Gain hands-on experience in setting up and configuring VPC, subnets, internet gateway,
* NAT gateway, and VPC peering connections.
* Learn how to enable internet connectivity securely within a VPC.
* Implement outbound internet access through the NAT gateway.
* Establish direct communication between VPCs using VPC peering.

## Learning Outcomes:
* Acquired knowledge about VPC and its essential components, such as subnets, gateways, and route tables.
* Developed skills in creating and configuring VPC resources using AWS management console.
* Learned how to set up routing tables to enable internet connectivity and outbound internet access securely.
* Gained understanding of VPC peering and its significance in connecting multiple VPCs within the same or different regions.
* Enhanced understanding of network security principles and best practices for cloud environments.

## What is VPC, Subnets, Internet Gateway and NAT Gateway?

* A VPC is a virtual private cloud, which works like a private network to isolate the resources within it.

* A route table contains a set of rules, called routes, that are used to determine where network traffic is directed

* A subnet is a defined set of network IP addresses that are used to increase the security and efficiency of network communications. You can think of them like postal codes, used for routing packages from one location     to another. The Subnets list in the Amazon VPC console displays subnet IDs and also their associated VPC IDs, route tables, and network ACLs.

* A security group is a set of rules that controls the network access to the resources it is associated with. Access is permitted only to and from the components defined in the security group's inbound and outbound        rules. If no rules are defined, the security group prevents all access.
  A security group therefore acts as a virtual firewall for your ec2 instances to control incoming and outgoing traffic.

## Connection between Gateway and Route table
Gateways:
* Gateways are devices (like routers or firewalls) that serve as entry and exit points between different networks.
* They connect networks with different IP address ranges, such as your local network and the internet.
* Gateways receive incoming data packets and determine where to send them next based on routing information.
  
Route Tables:

* Route tables are tables maintained by networking devices (like routers or switches) that contain information about how to route data packets to their destinations.
* Each entry in a route table specifies a destination network and the next hop (gateway) to reach that network.
* Devices consult the route table to determine the best path for forwarding data packets

Connection:
* When a device (like a computer or server) wants to send data to a destination outside of its local network, it checks its route table.
* The route table provides te information needed to determine the next hop (gateway) for reaching the destination network.
* The device then forwards the data packet to the specified gateway, which continues the process until the packet reaches its final destination.

In summary, gateways and route tables work together to facilitate the routing of network traffic between different networks. Gateways serve as the entry and exit points between networks, while route tables provide the necessary routing information to determine how data packets should be forwarded to their destinations.


## VPC setup steps

Steps -
1. Setting Up a Virtual Private Cloud (VPC)
2. Configuring Subnets within the VPC
3. Creating Internet Gateway and attaching it to VPC
4. Enabling Internet Connectivity with the Internet Gateway by setting up Routing tables
5. Enabling Outbound Internet Access through NAT Gateway
6. Establishing VPC Peering Connections
Let's come to the first one which involves Setting Up a Virtual Private Cloud (VPC)

Part-1
 

1.  Navigate to the search bar

   
a) Enter "VPC." Upon locating the relevant result, proceed to click on it, directing you to the Virtual Private Cloud (VPC) page.

  <img width="1171" alt="image" src="https://github.com/user-attachments/assets/81208e40-1498-4492-aae2-09466dc594c2">

2.  Navigate to the "Create VPC" section and click on it

  <img width="750" alt="image" src="https://github.com/user-attachments/assets/d1632535-8823-46e9-9243-e7f7f5b8d649">

3.  select the "VPC only" option, specify the IPv4 CIDR block, and proceed by clicking on the "Create VPC" button.

  <img width="773" alt="image" src="https://github.com/user-attachments/assets/7db68525-5f55-4adb-bd7d-b0f91377421f">

  <img width="802" alt="image" src="https://github.com/user-attachments/assets/e76ee0a5-829c-4365-b74f-af16d7cd9c0c">

This is the VPC created:

  <img width="1154" alt="image" src="https://github.com/user-attachments/assets/31f80d03-afbc-4fa5-a6e2-767dc0946e44">


Part -2


1. Navigate to the "Subnets" option located on the left sidebar.

a) Upon clicking, you will be directed to the "Subnets" page.

b) From there, proceed to click on the "Create subnet" button.
  
 <img width="910" alt="image" src="https://github.com/user-attachments/assets/564216a8-7998-45fa-84a2-445ba8812035">

2. Select the VPC id created in the previous step
   
 <img width="734" alt="image" src="https://github.com/user-attachments/assets/098df37e-ac55-4a6b-8b91-591f63439592">

3. Now, enter the subnet name,, and specify the IPv4 CIDR for the subnet.

   
a) Choose the availability zone

b) And specify the IPv4 CIDR for the subnet.

c) To create another subnet, click on the "Add subnet" button.

  <img width="809" alt="image" src="https://github.com/user-attachments/assets/7f32b409-d032-48ed-b47a-9ff72f0bb62a">

d) Repeat the same steps for the second subnet

e) ensuring to specify the subnet name, choose the availability zone, and provide the IPv4 CIDR.

f) Once completed, click on the "Create" button to create the subnet.

To maintain consistency with our intention of creating both a public and a private subnet, ensure that the naming convention reflects this distinction appropriately.

  <img width="854" alt="image" src="https://github.com/user-attachments/assets/2601889c-7d10-4a65-9a2b-53612ed2a8e0">

Here you will see your subnets being created

  <img width="1167" alt="image" src="https://github.com/user-attachments/assets/9a1de4bd-c3a2-41eb-857f-887a5731db93">

 
This is the diagramatic representation of our created resources


  ![image](https://github.com/user-attachments/assets/de2ddc3b-714d-4ca3-9586-25acd077d05e)


With the creation of subnets, the second part of the task is now completed. Let's proceed to the next part, which involves creating an Internet Gateway and attaching it to VPC.


Part-3


1. Navigate to the "Internet Gateway" option on the left sidebar.

   
a) Upon clicking, you will be directed to the Internet Gateway page.

<img width="1380" alt="image" src="https://github.com/user-attachments/assets/a1433d5d-678d-4aff-89ee-7139514cad3a">

2. Specify the name of the internet gateway

(a) Proceed by clicking the button 'create internet gateway'

  <img width="850" alt="image" src="https://github.com/user-attachments/assets/59bde0b5-82cd-42bc-92ad-9d80c5887c12">








