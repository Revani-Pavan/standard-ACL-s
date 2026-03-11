# standard-ACL-s

Securing the Perimeter: Understanding & Configuring ACLs 

I’ve been diving deep into Network Security lately, specifically focusing on Access Control Lists (ACLs). Whether you’re managing a small office or an enterprise-level data center, knowing how to control traffic flow is non-negotiable.

What is an ACL?

An Access Control List (ACL) is a set of rules used by routers and switches to filter network traffic. It looks at the packet headers (like Source IP or Port Number) and decides whether to Permit (let it through) or Deny (block it).

 Types of ACLs

Standard ACLs: Filter traffic based only on the Source IP address. These are usually placed as close to the destination as possible.

Extended ACLs: Filter traffic based on Source/Destination IP, Protocol (TCP/UDP), and Port numbers (HTTP, SSH, etc.). These are more precise and placed as close to the source as possible.

Numbered vs. Named: You can identify an ACL using a number (e.g., 1-99 for standard) or a descriptive name for better organization.

Why use them?

Security: Block unauthorized networks from accessing sensitive servers.

Traffic Flow Control: Limit network updates or restrict high-bandwidth traffic.

Privacy: Ensure different departments (like HR and Engineering) can't snoop on each other's local traffic.

 My Lab Configuration
 <img width="1506" height="812" alt="Screenshot 2026-03-11 105244" src="https://github.com/user-attachments/assets/00481919-119a-4924-9128-bb322a259532" />

I configure  R1 and R2 to meet specific lab requirements. Here’s a breakdown of how I tackled the requirements using both Standard Numbered 

The Mission:

Allow only specific hosts (PC1 & PC3) to reach the 192.168.1.0/24 subnet.

Prevent cross-talk between the 172.16.1.0 and 172.16.2.0 subnets.

Block the 172.16.2.0 network from accessing the Server on 192.168.2.0.

How I Built It:

On R1: I used Numbered ACLs applied to the outbound interfaces of G0/0 and G0/1. This effectively "walled off" the two local subnets from each other.

On R2: I implemented the more flexible Named ACLs to permit specific host IPs (172.16.1.1 and 172.16.2.1) while denying others.
<img width="744" height="146" alt="Screenshot 2026-03-11 093845" src="https://github.com/user-attachments/assets/d10b1b70-ec34-419b-95fb-8692d14e3cd3" />



<img width="756" height="620" alt="Screenshot 2026-03-11 093323" src="https://github.com/user-attachments/assets/12314e58-af54-4532-aafb-84affb7743ff" />
<img width="948" height="595" alt="Screenshot 2026-03-11 092548" src="https://github.com/user-attachments/assets/7c6c04db-50b1-4bdd-b488-62f66427d8f8" />

Here is the confirmation of the ACLs from each PC's
<img width="1051" height="1301" alt="Screenshot 2026-03-11 112648" src="https://github.com/user-attachments/assets/53c14ce6-a543-421d-9053-d142a6a22174" />
<img width="1026" height="1240" alt="Screenshot 2026-03-11 112520" src="https://github.com/user-attachments/assets/a32e7158-82c3-49a5-9683-0331a0241303" />
<img width="935" height="1094" alt="Screenshot 2026-03-11 112456" src="https://github.com/user-attachments/assets/1b241956-e2f1-4856-8624-11c610db65b8" />
<img width="1004" height="1255" alt="Screenshot 2026-03-11 112301" src="https://github.com/user-attachments/assets/0429dc8b-a3ea-4d93-a939-548177dfbd10" />
<img width="1003" height="1297" alt="Screenshot 2026-03-11 112052" src="https://github.com/user-attachments/assets/d1e35fb5-5c40-4b31-8bb0-3132d6897f4d" />





