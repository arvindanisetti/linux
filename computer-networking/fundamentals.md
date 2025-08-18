## Computer Networking

- Computer networking enables multiple nodes (computers/servers) to exchange data over interconnected links (like roads connecting cities).
- The Internet relies on undersea fiber cables, ISPs, data centers, and protocols (HTTP/HTTPS) to move data across the globe.
- DNS translates human-friendly domains into machine-usable IP addresses, acting like a phonebook for the internet.
- OSI and TCP/IP models explain layered responsibilities in networking and help debug issues logically.
- IP addresses identify devices; subnetting divides large networks for efficient address management.
- IPv4 addresses are limited; IPv6 provides astronomically more space.
- DevOps engineers frequently depend on VPCs, subnets, gateways, NAT, load balancers, and firewalls/security groups to design secure, scalable networks.
- Practical diagnostics include ping, traceroute, nslookup, and systemctl for service checks.
- Real-world steps include launching an EC2 instance, securing it, installing a web server, and mapping a custom domain via DNS.


### Commands Used

```bash
# Network Diagnostics
ping <host>             # Test basic connectivity and latency
traceroute <host>       # Trace the path packets take to a destination (Linux/macOS)
tracert <host>          # Windows equivalent of traceroute
nslookup <domain>       # Query DNS to resolve domain to IP and examine name servers

# Linux Service Management (e.g., check web server status)
sudo systemctl status nginx       # Show Nginx status
sudo systemctl start nginx        # Start Nginx
sudo systemctl stop nginx         # Stop Nginx
sudo systemctl restart nginx      # Restart Nginx
sudo systemctl enable nginx       # Enable Nginx to start on boot

# Web Server Setup (Ubuntu example)
sudo apt update                   # Update package indexes
sudo apt install -y nginx         # Install Nginx web server
sudo mkdir -p /var/www/html       # Ensure default web root exists
echo "<h1>Hello from my server</h1>" | sudo tee /var/www/html/index.html

# SSH into EC2
ssh -i /path/to/key.pem ubuntu@<EC2_PUBLIC_IP>

# AWS Security Groups (conceptual – adjust in console or CLI)
# Inbound rules to allow HTTP
#   Type: Custom TCP, Port: 80, Source: 0.0.0.0/0
# Inbound rule to allow SSH
#   Type: SSH, Port: 22, Source: your IP only

# DNS (Registrar UI steps summarized)
# Create A record:
#   Name: @ (or subdomain, e.g., app)
#   Type: A
#   Value: <EC2_PUBLIC_IP>
#   TTL: 600 (10 minutes) or per preference
```

#### Global Connectivity: The Backbone of the Internet
  - The internet is a vast mesh of physical infrastructure fiber optic cables, routers, switches, data centers that crisscross the globe.
Undersea fiber optic cables are the most critical component, laying under oceans and connecting continents, facilitating over 95% of international data transfer.

#### Requesting Data: From Your Browser to the Server
- When you type a URL like [`www.netflix.com`](https://www.netflix.com/), your browser initiates a request using the HTTPS protocol.
HTTPS encrypts data to ensure security, especially for sensitive information like passwords.
Your browser does not remember the server's IP address; instead, it looks up the address through the Domain Name System (DNS).

#### Server IP Addresses & DNS
- Every website is hosted on servers identified by a **unique IP address**, e.g., 52.44.23.12.
The DNS acts like an internet phonebook. When you enter [`www.netflix.com`](https://www.netflix.com), DNS translates this into the server’s IP.
The process involves several layers of DNS servers handling your query, from root DNS servers to authoritative ones.

#### Data Transfer & Infrastructure: The Journey of a Request
Once the DNS resolves the domain to an IP, the request is sent from your device to:
- Your **Wi-Fi router** (local gateway).
- The router forwards it to your **ISP** (Internet Service Provider).
- From the ISP, data travels through multiple **interconnected devices**: switches, routers, and **undersea cables**.
- These form an **interconnected global network**.
- The data may **hop** through **multiple relay points**—sometimes crossing cities, countries, or continents.
- It may pass through **international carriers** like Tata Communications or Verizon.
- The request finally reaches the **data center** hosting the website, e.g., Netflix’s servers in Paris or Singapore.

#### Tracing Data Routes – Visualizing the Journey
Using tools like `tracert` (Windows) or `traceroute` (Linux/macOS), you can **visualize** each "hop" the data takes.
- Each hop is a router or networking device along the route, with delays (latency) measured at each step.
- Example: Mumbai → Dubai → Europe → Paris.
- This **demonstrates** how the internet involves **multiple layers and international infrastructure**.

#### Practical Tools & Concepts
- **Traceroute (`tracert` / `traceroute`)** helps **visualize the route** and delays.
- **IP investigation** shows **which providers** handle your data in different hops.
- **Secure transmission**: HTTPS ensures **encrypted data**, represented as a **sealed envelope** in postal analogy.

### Analogy: The Internet as an International Postal \& Transportation System

Imagine you want to send a letter (request) to Netflix’s server from your home:
- **Your House (Computer/Device)**: The sender initiates the request.
- **Local Post Office (Wi-Fi Router)**: Your device hands the letter to the local router, which prepares it for delivery.
- **Regional Postal Hub / ISP**: The router forwards the letter to your ISP, which manages the regional or national network.
- **Address Directory (DNS)**: You write “Netflix HQ,” but the postal system looks up the **physical address** (IP address) in the directory.
- **International Cargo (Undersea Cables \& Routers)**: Your letter goes through **international hubs**—similar to cargo ships or aircraft—traveling across oceans via **fiber optic cables**.
- **Hubs / Sorting Centers (Routers \& Switches)**: The package is routed through various hubs, each directing it closer to its destination based on the address.
- **Data Centers (Recipient’s Home)**: The letter arrives at Netflix’s data center—the intended recipient.
- **Reply Package**: Netflix responds by sending data back, retracing the same path through routers and undersea cables, arriving back to your device.
- **Tracking (Traceroute)**: You can **track** the package’s progress at each hop, seeing the path it takes.


## Summary Table

| Component | Analogy | Network Equivalent |
| :-- | :-- | :-- |
| Your House | Your Computer/Device | Computer or phone |
| Local Post Office | Wi-Fi Router | Home router |
| Regional Postal Hub | ISP | Internet Service Provider |
| Address Directory | DNS | DNS servers / directory |
| International Cargo | Undersea cables | Fiber optic links across oceans |
| Hubs / Sorting Centers | Routers \& Switches | Routing points, Internet Exchange Points |
| Final Destination | Netflix servers | Data centers / application servers |
| Tracking Journey | Traceroute / Tracert | Network path visualization |
| Sealed Envelope | HTTPS encryption | TLS/SSL secure protocol |


***


### OSI Model (7 Layers)

1. Application: End-user services (HTTP/HTTPS, DNS, etc.)
2. Presentation: Data formatting, compression, encryption
3. Session: Session establishment, management, teardown
4. Transport: End-to-end delivery (TCP for reliable, UDP for faster/unreliable)
5. Network: IP addressing and routing (IP, ICMP)
6. Data Link: Framing, MAC addressing, switching (Ethernet)
7. Physical: Mediums and signals (cables, fiber, radio)

Tips: Learn functions and examples per layer; think top-down during troubleshooting.

### TCP/IP Model (4 Layers)

- Application (OSI app + presentation + session)
- Transport (TCP/UDP)
- Internet (IP routing)
- Network Access (data link + physical)


### IP Addressing and Subnetting

- IPv4: 32-bit addresses (~4.29B addresses), dotted-decimal (e.g., 192.168.1.10).
- IPv6: 128-bit addresses (~340 undecillion), hexadecimal with colons.
- Subnetting:
    - Splits larger networks into smaller subnets for address conservation and routing efficiency.
    - Subnet mask/CIDR (e.g., 192.168.1.0/24) define host/network portions.
- Practical insights:
    - Many devices per household require addresses; NAT helps share a single public IP.
    - For cloud design, plan CIDR ranges to avoid overlap and to scale (e.g., 10.0.0.0/16 VPC with multiple /24 subnets).


### Network Security: Firewalls \& Security Groups

- Firewalls control inbound/outbound traffic via rules (by IPs, ports, protocols).
- In AWS: Security Groups are stateful firewalls attached to instances.
- **Common rules**:
- Allow SSH (22) from admin IP only.
- Allow HTTP (80) and HTTPS (443) from 0.0.0.0/0 when serving public sites.
- Use NACLs for subnet-level stateless filtering when needed.


### Practical Diagnostics and Tools

- ping: Basic reachability and latency check.
- traceroute/tracert: Path analysis across network hops.
- nslookup: DNS resolution checks.
- systemctl: Manage and inspect Linux services (e.g., Nginx).

Examples:

```bash
ping example.com
traceroute example.com     # macOS/Linux
tracert example.com        # Windows
nslookup example.com
sudo systemctl status nginx
```


### Cloud Networking — VPC \& Subnets

- VPC: Private, isolated virtual network in cloud (e.g., AWS).
- Subnets:
    - Public subnets: Routable to the internet via an Internet Gateway (IGW).
    - Private subnets: No direct internet route; use NAT Gateway for outbound-only internet access (e.g., pulling updates).
- VPC Peering:
    - Connect two VPCs to allow private routing between them (must handle overlapping CIDRs and route tables).
- Load Balancers:
    - Distribute traffic across multiple instances; fronted in public subnets with targets in private subnets for secure architectures.


### Hands-On: Launching a Web Server on AWS

1. Create EC2 instance (Ubuntu, free tier if available).
2. Networking:
    - Place in a VPC and a subnet (public for public access).
    - Assign public IPv4 address.
    - Attach a security group allowing:
        - SSH (22) from your IP
        - HTTP (80) from 0.0.0.0/0
3. Connect via SSH:

```bash
ssh -i /path/to/key.pem ubuntu@<PUBLIC_IP>
```

4. Install and start Nginx:

```bash
sudo apt update
sudo apt install -y nginx
sudo systemctl enable --now nginx
sudo systemctl status nginx
```

5. Publish a page:

```bash
echo "<h1>Deployed from my EC2</h1>" | sudo tee /var/www/html/index.html
```

6. Verify in browser: http://<PUBLIC_IP>

### Multi-Tier Architecture (Example)

- Tier 1 (Frontend): React (public subnet, behind ALB)
- Tier 2 (Backend): Node.js (private subnet, targeted by ALB)
- Tier 3 (Database): MongoDB (private subnet, no public access)
- Optional: Redis cache in private subnet
- Observability: Add logging/metrics; secure inter-tier traffic via SG rules.

### Domain → Server Mapping (DNS)

- Registrar (e.g., GoDaddy/Route 53) → DNS management → Create A record:
- Name: @ (root) or subdomain (e.g., app) Type: A
- Value: <EC2_PUBLIC_IP>
- TTL: 600

```bash
nslookup yourdomain.com
ping yourdomain.com
```

- Note: DNS propagation can take minutes depending on TTL and caches.


### NAT and Private/Public Access

- NAT allows instances in private subnets to access internet for updates without exposing them publicly.
- Typical pattern:
    - Public subnet: ALB, bastion hosts
    - Private subnet: application servers, databases, caches
    - NAT Gateway in public subnet for private outbound traffic


### Security Reminders

- Restrict SSH to trusted IPs.
- Use HTTPS (TLS) where appropriate.
- Keep OS and packages patched.
- Principle of least privilege across security groups, IAM, and network policies.


### Quick Troubleshooting Guide

- Can’t reach site on port 80
    - Verify instance is running and has public IP.
    - Security group inbound rule for TCP 80 → 0.0.0.0/0.
    - Nginx running: `sudo systemctl status nginx`.
    - OS-level firewall (if used): open port 80.
- DNS not resolving:
    - Check A record and TTL.
    - Use `nslookup` to confirm resolution to your public IP.
- SSH failing:
    - Correct key permissions (`chmod 400 key.pem`).
    - Security group allows port 22 from your IP.
    - Correct username for AMI (e.g., ubuntu for Ubuntu).

***
