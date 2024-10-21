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

Now, you will notice that it is currently detached, indicating that it is not associated with any VPC. 

  ![image](https://github.com/user-attachments/assets/ac5f54d4-4214-4f2b-bc4d-50961ab4a527)


To enable internet connectivity, you must attach the Internet Gateway to the VPC you have previously created.

  ![image](https://github.com/user-attachments/assets/26fb603c-377a-45a4-a33f-a32e4f6a3d5e)

Now attach to a VPC


  ![image](https://github.com/user-attachments/assets/e2441801-0cd7-4d65-bd9d-d369a2242298)

  ![image](https://github.com/user-attachments/assets/fac6d3e4-58ea-42e8-8a68-a5529b98aab6)

Part -4

1. Proceed to the "Route Tables" option located on the left sidebar.

a) Once there, click on the "Create route table" button.

  ![image](https://github.com/user-attachments/assets/1cb7ee51-d2a1-4406-9274-73c011c256bb)


2. Enter the name of the route table and select the VPC you previously created.

   
a) Finally, click on the "Create route table" button to proceed.

  ![image](https://github.com/user-attachments/assets/f0749ff7-24dc-48e8-b63b-515f582d2ab5)


b) Next, click on "Subnet associations," followed by "Edit subnet associations" to associate the subnet with this route table, We'll associate the public subnet with this route table.

  ![image](https://github.com/user-attachments/assets/8197c724-c873-47b4-b64b-90cfb1fe2108)


3. Choose the public subnet and click on save association.

  ![image](https://github.com/user-attachments/assets/3e84701d-77fc-47a9-b030-13858872cdac)

4. Navigate to "Routes" and then click on "Edit routes."

  ![image](https://github.com/user-attachments/assets/6976b5dd-d316-403a-a5f6-e175262f5b3f)

5. Click on add route.

  ![image](https://github.com/user-attachments/assets/a890a33b-4e27-4d62-a364-c184b73982fc)

6. Select "Destination" as "0.0.0.0/0," indicating that every IPv4 address can access this subnet.

   
8. In the "Target" field, choose "Internet Gateway," and then select the Internet Gateway you created. Finally, save the changes.

  ![image](https://github.com/user-attachments/assets/3d3ef0dd-c714-4915-866e-bc0c535d0788)

  
  ![image](https://github.com/user-attachments/assets/a02b72b9-def8-4d3c-873d-86a5488f526d)


The route table has now been configured to route traffic to the Internet Gateway, allowing connectivity to the Internet. Since only the subnet named "my-public-subnet-l" is associated with this route table, only resources within that subnet can access the internet.

  ![image](https://github.com/user-attachments/assets/a6112488-87a7-4c70-9fca-9f15ead0b7ca)

This is the respresentation of our infastructure so far


  ![image](https://github.com/user-attachments/assets/cd37badb-f13d-4abc-9171-d1b7137f20ab)


Part-5

1. Navigate to the "NAT Gateways" section, then click on "Create NAT Gateway."

  ![image](https://github.com/user-attachments/assets/4da4fee5-dc36-421c-8cd0-0de0d69f93f5)

2. Then mention the name of the NAT Gateway.

 ![image](https://github.com/user-attachments/assets/d91d87aa-04af-446e-b44d-b6ecb9b24c4b)


3. Now, choose the Private subnet and connectivity type as private

  ![image](https://github.com/user-attachments/assets/83a332c6-f513-4bc6-aec9-a554427e77be)

4. Then click on Create NAT Gateway.

  ![image](https://github.com/user-attachments/assets/58580c89-b196-449b-b026-922faf808fca)

Your NAT Gateway is created successfully.

  ![image](https://github.com/user-attachments/assets/37746157-4f73-4718-b84a-2b3fad7134e8)

5. Select your NAT Gateway.

   
6. Then navigate to the "Details" tab.

   
7. From there, locate the subnet ID and click on it.

  ![image](https://github.com/user-attachments/assets/b3f5b22c-4c0b-4a0b-b738-c2f36084c429)

8. In the subnet page, navigate to the "Route Table" section.

    
9. Then click on the "route table ID" - In our case - 1"rtb-053d3876b518b4d49"

  ![image](https://github.com/user-attachments/assets/e81547ae-abb7-4c7f-ae15-0ed0d7ffa7d6)

10. Proceed to the "Routes" section, then click on "Edit routes."

  ![image](https://github.com/user-attachments/assets/ba74abc3-b98a-4cb4-bf25-222cc193cdb5)

11. Click on "Add routes"

  ![image](https://github.com/user-attachments/assets/2c9cb322-6ce5-4d8b-93df-31346be57c70)

a) Select "Destination" as "0.0.0.0/0."


b) In the "Target" field, choose "NAT Gateway,"


c) Then select the NAT Gateway you created.


d) Finally, save the changes.

![image](https://github.com/user-attachments/assets/6abddffc-37b3-403b-9827-77e4f640b702)

12. On the subnet association section, click on edit subnet association.

  ![image](https://github.com/user-attachments/assets/8acf1f85-3734-4ac8-b631-e9be52d45029)

a) Choose the private subnet and click on "Save associations"

  ![image](https://github.com/user-attachments/assets/8777b94f-2ad8-4cc0-bdfd-c7567fd36031)


Now, the subnet has been successfully attached with the route table.


![image](https://github.com/user-attachments/assets/d42ce23c-6383-40ef-97a4-3edfd7cfd8eb)


![image](https://github.com/user-attachments/assets/683baac7-d57c-4f4e-aacd-e72aca739958)


Difference between Internet Gateway and NAT Gateway

Internet Gateway:
Think of it like a door to the internet for your subnet. When you attach an Internet Gateway to a subnet, it allows the resources in that subnet (like EC2 instances) to reach out to the internet and also allows internet traffic to reach those resources. 

It's like having a door both to enter and exit the subnet.



NAT Gateway:

Imagine it as a one-way street sign for your subnet's traffic. When you attach a NAT Gateway to a subnet, it lets the resources in that subnet (like EC2 instances) access the internet, but it doesn't allow incoming traffic from the internet to reach those resources. 

It's like the resources can go out to the internet, but the internet traffic can't directly come in.


  ![image](https://github.com/user-attachments/assets/a1eaa169-24f4-4e4b-879e-ec56f7d47a22)

Now, let's proceed further and come to our next part that involves Establishing VPC Peering Connections. For this let's first understand some terms-


Note- An EC2 instance is a virtual server in AWS that you can use to run applications. It offers flexible computing power and can be easily scaled up or down. EC2 instances are widely used for hosting websites, running software, and processing data in the cloud.

What is VPC Peering?

VPC peering is like connecting two virtual offices in the cloud so they can talk to each other directly. Just imagine two neighboring offices sharing files and chatting without going through a middleman.
- By default, EC2 instances in different VPCs cannot communicate with each other.
- To enable communication between EC2 instances in different VPCs, you can set up VPC peering, VPN connections, or AWS Direct Connect.
- VPC peering establishes a direct network connection between the VPCs, allowing EC2 instances in one VPC to communicate with EC2 instances in the other VPC.


Part -6

1. Let's begin by creating two VPCs in the same region. Alternatively, you may choose a different region if needed.


  ![image](https://github.com/user-attachments/assets/fd7046f4-539a-4e1e-b20a-8c1928422790)


  ![image](https://github.com/user-attachments/assets/fdd16393-ab39-4bd4-93be-7abd55a854ec)



2. Navigate to the "Peering Connections" option on the left sidebar.

   
a) Upon clicking, you'll be directed to the VPC peering page.


b) From there, proceed to click on the "Create Peering Connection" button.

  ![image](https://github.com/user-attachments/assets/4b0eefb1-9cae-4a8f-bd62-782350914424)

3. Now, provide a name for the VPC peering connection.

a) select the requester VPC.

b) Choose the account "My account" since the VPCs are in our own AWS account.

c) Ensure to use the same region, "This Region (ap-southeast-1)," as the VPCs were created in the same region.

d) Next, select the accepter VPC.

e) proceed by clicking on the "Create Peering Connection" button.

  ![image](https://github.com/user-attachments/assets/f49077f7-e094-4eea-9ef7-233bca7ccd74)


Then, you'll see this:

  ![image](https://github.com/user-attachments/assets/03655eca-b072-4d5e-a8ed-76363d43368a)



4. In the Peering Connection page, locate the "Actions" option on the right side.
   
a) Click on it, then select "Accept Request."

 ![image](https://github.com/user-attachments/assets/032f812e-f6e8-4590-ac22-e728e2bf7636)


b) Click on Accept request.

  ![image](https://github.com/user-attachments/assets/2de21dab-ce27-4217-82bd-1da106358529)


5. Now, click on Main route table ID of the accepter VPC.

  <img width="1434" alt="image" src="https://github.com/user-attachments/assets/ebeb93e4-fbde-4105-be52-15826c4b5c47">

6. Choose the route table.

   
a) then navigate to the "Routes" section.


b) Click on "Edit route."

  ![image](https://github.com/user-attachments/assets/0b5df5e6-4f02-4965-8bd3-c5ad1b9e51b0)


c) Click on add route.


  ![image](https://github.com/user-attachments/assets/56f46312-8b43-45d1-a23e-9cf0d424d449)


7. Go to the VPC page

   
a) select the requester VPC.

b) In the details tab, you'll find the IPv4 CIDR. (in this case - 	172.16.0.0/16)


c) Copy this CIDR and paste it in the "Destination" field when adding a route.

  ![image](https://github.com/user-attachments/assets/d00f9065-9b8f-407f-a224-9548639a5071)

d) In the target, choose VPC peering and then choose the peering connection you have created. Click on save changes.

8. Now, copy the IPv4 CIDR of the accepter VPC. (in this case - 192.168.0.0/16)

  ![image](https://github.com/user-attachments/assets/33ec3e5c-36cd-4559-9ecd-aaa9cf3f46c5)

9. Now, click on Main route table ID of the requester VPC.

  ![image](https://github.com/user-attachments/assets/89bd0095-972a-4b7d-867d-5a0c111e5af6)
  

10. Choose the route table, then navigate to the "Routes" section. Click on "Edit route."
    

  ![image](https://github.com/user-attachments/assets/1df034e9-0d85-44a1-8048-112fe5260df6)


11. Click on add route.

    
a) Paste the CIDR in the "Destination" field.


b) In the target, choose VPC peering


c) Then choose the peering connection you have created.


  ![image](https://github.com/user-attachments/assets/84eec17a-5390-4351-99b4-4439e0468577)

The connection has been successfully established. Now, resources in the accepter VPC can connect to resources in the requester VPC, and vice versa.

![image](https://github.com/user-attachments/assets/9a0bb248-49b1-4b14-acde-5ff294887aa2)


Let's see some points that you need to know about VPC Peering, VPC Peering Basics: VPC peering allows direct communication between two VPCs using private


IP addresses. Region compatibility: VPC peering can be set up between VPCs in the same AWS region or different regions and the same AWS account or different
AWS accounts.


For more reference, you can go through the  [Create a VPC peering connection](https://docs.aws.amazon.com/vpc/latest/peering/create-vpc-peering-connection.html#same-account-same-region)


CIDR Blocks: The CIDR blocks of the VPCs involved in the peering connection should not overlap or conflict with each other. Each VPC must have a unique CIDR block.
IP Addressing: Resources in one VPC can communicate with resources in the peered VPC using their private IP addresses.


Security Groups and NACLs: Ensure proper configuration of Security Groups and Network Access Control Lists (NACLs) to allow traffic between peered VPCs.


Direct Communication: Resources in one VPC can directly communicate with resources in the peered VPC without requiring internet access.


Transitive Traffic: Traffic cannot flow through a VPC peering connection to reach other VPCs not directly peered.


Routing: Update route tables in both VPCs to allow traffic to flow through the peering connection. Each VPC's route table must contain a route entry for the CIDR block of the peer VPC, pointing to the peering connection.


Limitations: There are limits on the number of VPC peering connections that can be established per VPC, as well as limitations on the number of route entries per route table.
Now, let's understand some more terms,


What is VPC endpoint?


Think of a VPC endpoint like a dedicated, secure tunnel between your house (VPC) and a library (AWS service). Instead of going through the bustling streets (public internet), you have a direct pathway from your home to the library. This pathway ensures that only you and authorized users can access the library's resources, like books or documents, without exposing them to outside risks. It's a private, efficient way to access what you need, keeping your data safe from prying eyes on the internet.

Let's understand the problem we were facing,
When you're backing up data from an EC2 instance to an $3 bucket, it usually goes over the internet, whether the instance is in a public or private subnet. But if the data is sensitive, that means it's risky because hackers could try to get it while it's traveling over the internet.
  

  ![image](https://github.com/user-attachments/assets/1fd82538-4a41-489c-80f5-dcb5a911163e)

To avoid this risk, we can use something called VPC endpoints. These endpoints make a private connection between the VPC and S3, so the data doesn't have to go over the internet. This way, even sensitive data stays safe from hackers and other threats.

  ![image](https://github.com/user-attachments/assets/951c2555-c53c-4a41-b547-51a464576b9f)





































  









