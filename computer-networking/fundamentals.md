# Computer Networking

- Computer networking enables multiple nodes (computers/servers) to exchange data over interconnected links (like roads connecting cities).
- The Internet relies on undersea fiber cables, ISPs, data centers, and protocols (HTTP/HTTPS) to move data across the globe.
- DNS translates human-friendly domains into machine-usable IP addresses, acting like a phonebook for the internet.
- OSI and TCP/IP models explain layered responsibilities in networking and help debug issues logically.
- IP addresses identify devices; subnetting divides large networks for efficient address management.
- IPv4 addresses are limited; IPv6 provides astronomically more space.
- DevOps engineers frequently depend on VPCs, subnets, gateways, NAT, load balancers, and firewalls/security groups to design secure, scalable networks.
- Practical diagnostics include ping, traceroute, nslookup, and systemctl for service checks.
- Real-world steps include launching an EC2 instance, securing it, installing a web server, and mapping a custom domain via DNS.


## Commands Used

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


## References

- OSI Model (7 layers): Application, Presentation, Session, Transport, Network, Data Link, Physical
- TCP/IP Model (4 layers): Application, Transport, Internet, Network Access
- AWS VPC components: VPC, subnets (public/private), route tables, Internet Gateway (IGW), NAT Gateway, security groups, NACLs
- Common web stack example: React (frontend), Node.js (backend), MongoDB (database), Redis (cache), Load Balancer (fronting public traffic)

***

## 1) Introduction to Computer Networking

- Definition: A computer network is a group of connected nodes (computers/servers) that exchange data.
- Analogy: Roads connecting cities = networks connecting devices. Vehicles = data moving between endpoints.
- Importance for DevOps: Daily activities include transferring artifacts, executing code across servers, troubleshooting connectivity, and securing services across regions.


## 2) How the Internet Works

- Components:
    - Undersea fiber-optic cables connect continents and data centers.
    - ISPs provide last-mile connectivity and route traffic.
    - Data centers host application servers and storage.
- Accessing a website:
    - Type a URL (e.g., www.netflix.com) in a browser using HTTPS; the browser retrieves HTML/CSS/JS assets from servers.
    - DNS resolves the domain to an IP address.
    - Requests traverse local network → ISP → backbone → destination data center and back.


## 3) DNS (Domain Name System)

- Purpose: Translates domain names to IP addresses; like a phonebook for the internet.
- Common records:
    - A (IPv4), AAAA (IPv6), CNAME (alias), NS (name servers), MX (mail).
- Practical:
    - Map a domain or subdomain to a server’s public IP with an A record.
    - TTL controls caching duration (e.g., 600 seconds).


## 4) Core Networking Models

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


## 5) IP Addressing and Subnetting

- IPv4: 32-bit addresses (~4.29B addresses), dotted-decimal (e.g., 192.168.1.10).
- IPv6: 128-bit addresses (~340 undecillion), hexadecimal with colons.
- Subnetting:
    - Splits larger networks into smaller subnets for address conservation and routing efficiency.
    - Subnet mask/CIDR (e.g., 192.168.1.0/24) define host/network portions.
- Practical insights:
    - Many devices per household require addresses; NAT helps share a single public IP.
    - For cloud design, plan CIDR ranges to avoid overlap and to scale (e.g., 10.0.0.0/16 VPC with multiple /24 subnets).


## 6) Network Security: Firewalls \& Security Groups

- Firewalls control inbound/outbound traffic via rules (by IPs, ports, protocols).
- In AWS:
    - Security Groups are stateful firewalls attached to instances.
    - Common rules:
        - Allow SSH (22) from admin IP only.
        - Allow HTTP (80) and HTTPS (443) from 0.0.0.0/0 when serving public sites.
    - Use NACLs for subnet-level stateless filtering when needed.


## 7) Practical Diagnostics and Tools

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


## 8) Cloud Networking — VPC \& Subnets

- VPC: Private, isolated virtual network in cloud (e.g., AWS).
- Subnets:
    - Public subnets: Routable to the internet via an Internet Gateway (IGW).
    - Private subnets: No direct internet route; use NAT Gateway for outbound-only internet access (e.g., pulling updates).
- VPC Peering:
    - Connect two VPCs to allow private routing between them (must handle overlapping CIDRs and route tables).
- Load Balancers:
    - Distribute traffic across multiple instances; fronted in public subnets with targets in private subnets for secure architectures.


## 9) Hands-On: Launching a Web Server on AWS

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

## 10) Domain → Server Mapping (DNS)

- Registrar (e.g., GoDaddy/Route 53) → DNS management → Create A record:
    - Name: @ (root) or subdomain (e.g., app)
    - Type: A
    - Value: <EC2_PUBLIC_IP>
    - TTL: 600
- Test:

```bash
nslookup yourdomain.com
ping yourdomain.com
```

- Note: DNS propagation can take minutes depending on TTL and caches.


## 11) NAT and Private/Public Access

- NAT allows instances in private subnets to access internet for updates without exposing them publicly.
- Typical pattern:
    - Public subnet: ALB, bastion hosts
    - Private subnet: application servers, databases, caches
    - NAT Gateway in public subnet for private outbound traffic


## 12) Security Reminders

- Restrict SSH to trusted IPs.
- Use HTTPS (TLS) where appropriate.
- Keep OS and packages patched.
- Principle of least privilege across security groups, IAM, and network policies.


## 13) Multi-Tier Architecture (Example)

- Tier 1 (Frontend): React (public subnet, behind ALB)
- Tier 2 (Backend): Node.js (private subnet, targeted by ALB)
- Tier 3 (Database): MongoDB (private subnet, no public access)
- Optional: Redis cache in private subnet
- Observability: Add logging/metrics; secure inter-tier traffic via SG rules.


## 14) Quick Troubleshooting Guide

- Can’t reach site on port 80:
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

## References (General Orientation)

- OSI and TCP/IP models (layered networking fundamentals)
- DNS basics (A/AAAA/CNAME/MX/NS records, TTLs)
- AWS VPC, Subnets, Security Groups, Internet Gateway, NAT Gateway
- Load balancers and multi-tier architectures

***
