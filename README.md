# 🚀 AWS Three-Tier Highly Available Web Application Architecture

<p align="center">

<img src="https://img.shields.io/badge/AWS-Solutions%20Architect%20SAA--C03-orange?style=for-the-badge&logo=amazonaws">

<img src="https://img.shields.io/badge/Architecture-Three--Tier-blue?style=for-the-badge">

<img src="https://img.shields.io/badge/Focus-High%20Availability-green?style=for-the-badge">

<img src="https://img.shields.io/badge/Cloud-AWS%20%7C%20Azure-purple?style=for-the-badge">

</p>


<h3 align="center">
📘 AWS Certified Solutions Architect – Associate (SAA-C03) Study Notes
</h3>


<p align="center">
A complete breakdown of designing a secure, scalable, highly available enterprise web application architecture on AWS.
</p>


---

# 📌 About This Project

This repository documents my learning journey while preparing for the:

<div align="center">

## ☁️ AWS Certified Solutions Architect – Associate (SAA-C03)

</div>


The goal of this project is to understand how production-grade applications are designed using AWS best practices:

✅ High Availability  
✅ Fault Tolerance  
✅ Security  
✅ Scalability  
✅ Disaster Recovery  
✅ Cost Optimization  


---

# ⚠️ Disclaimer

> This repository represents my personal understanding and interpretation of AWS concepts while studying for the AWS SAA-C03 certification.

The explanations, notes, documentation structure, and redesign of concepts have been created and refined by me.

The AWS architecture diagrams used are **not my original work**. They were sourced from publicly available educational resources. Credit belongs to their respective creators.

All AWS concepts are explained using my own understanding based on AWS documentation and learning materials.

---

# 🏗️ Architecture Overview


## Three-Tier Application Design


```
                  🌍 Users
                     |
                     |
              Amazon Route 53
                     |
                     |
              AWS Shield + WAF
                     |
                     |
              Amazon CloudFront
                     |
                     |
        Application Load Balancer
                     |
        ┌────────────┴────────────┐
        |                         |
    Web Tier                  Web Tier
      EC2                       EC2
        |
        |
 Internal Load Balancer
        |
        |
 Application Tier
        |
        |
 Amazon ElastiCache
        |
        |
 Amazon RDS Multi-AZ
```


---

# 🧩 Architecture Layers


<table>
<tr>
<td width="33%" align="center">

## 🌐 Presentation Layer

Handles user interaction.

Examples:

- React
- Angular
- Nginx
- Apache

</td>

<td width="33%" align="center">

## ⚙️ Application Layer

Handles business logic.

Examples:

- Authentication
- Payments
- Reports
- APIs

</td>

<td width="33%" align="center">

## 🗄️ Database Layer

Stores application data.

Examples:

- Amazon RDS
- Backups
- Replication

</td>

</tr>
</table>


---

# 🔄 Request Flow


## User Request Journey


| Step | Service | Responsibility |
|-|-|-|
| 1️⃣ | Route 53 | Converts domain name into IP address |
| 2️⃣ | AWS Shield | Protects against DDoS attacks |
| 3️⃣ | AWS WAF | Blocks malicious requests |
| 4️⃣ | CloudFront | Delivers cached content |
| 5️⃣ | Load Balancer | Distributes traffic |
| 6️⃣ | EC2 | Processes application requests |
| 7️⃣ | ElastiCache | Provides fast data retrieval |
| 8️⃣ | RDS | Stores permanent data |


---

# ☁️ AWS Services Explained


## 🌎 Amazon Route 53

### Purpose

AWS managed DNS service.

### Features

| Feature | Description |
|-|-|
| 🌐 DNS Resolution | Converts domain names into IP addresses |
| ❤️ Health Checks | Detects unhealthy endpoints |
| 🔀 Routing Policies | Controls traffic direction |
| 🔁 Failover | Redirects traffic automatically |


---

# 🛡️ AWS Shield


## Purpose

Protects applications from Distributed Denial of Service attacks.


### Provides

- Network protection
- Traffic filtering
- Availability protection


---

# 🔥 AWS WAF


## Web Application Firewall


Protects applications from:

```
❌ SQL Injection
❌ Cross Site Scripting
❌ Malicious Bots
❌ Suspicious IP Addresses
```


Example:


```
https://example.com?id=' OR 1=1
```

Blocked before reaching the application.


---

# 🌍 Amazon CloudFront


## Content Delivery Network


CloudFront stores frequently accessed content closer to users.


### Cached Content

📷 Images  
🎥 Videos  
📄 Documents  
🎨 CSS  
⚡ JavaScript  


Benefits:

| Benefit | Result |
|-|-|
| 🚀 Speed | Faster response |
| 💰 Cost | Less server traffic |
| 🌎 Global | Edge locations worldwide |


---

# 📦 Amazon S3


## Object Storage


Used for:

```
📷 Images
🎥 Videos
📄 Documents
💾 Backups
🌐 Static Websites
```


Advantages:

✅ Unlimited scalability  
✅ High durability  
✅ Low cost  


---

# 🏢 Amazon VPC


## Virtual Private Cloud


A private AWS network environment.


```
VPC

├── Public Subnet
│     ├── Load Balancer
│     └── NAT Gateway
│

└── Private Subnet
      ├── EC2 Servers
      ├── Application Servers
      └── Databases
```


---

# 🚪 NAT Gateway


Allows private resources to access the internet securely.


Used for:

- Software updates
- Package downloads
- Security patches


Private servers:

```
CAN → Internet Access

CANNOT → Receive Internet Connections
```


---

# ⚖️ Elastic Load Balancer


Distributes incoming traffic.


Without Load Balancer:


```
10,000 Users
      |
      |
  Single Server
      |
     💥
```


With Load Balancer:


```
10,000 Users

      |
      |
Load Balancer

 |     |     |

EC2  EC2  EC2

```


---

# 📈 Auto Scaling


Automatically adjusts resources based on demand.


Example:


| Time | Servers |
|-|-|
| Morning | 2 EC2 |
| Peak Hours | 8 EC2 |
| Night | 2 EC2 |


Benefits:

🚀 Performance  
💰 Cost Saving  
🛡️ Availability  


---

# ⚡ Amazon ElastiCache


Memory-based caching service.


Without Cache:


```
1000 Requests
       |
       |
1000 Database Queries
```


With Cache:


```
1000 Requests

       |

Redis Cache

       |

Database
```


Benefits:

⚡ Faster response  
📉 Reduced database load  


---

# 📂 Amazon EFS


Shared file storage.


Example:


```
EC2 Server A
      |
      |
   Amazon EFS
      |
      |
EC2 Server B
```


---

# 🗄️ Amazon RDS Multi-AZ


Managed relational database.


Architecture:


```
Primary Database
        |
        |
Replication
        |
        |
Standby Database
```


If failure occurs:

```
Primary ❌

Standby becomes Primary ✅
```


---

# 🔐 Security Architecture


| Layer | AWS Service | Protection |
|-|-|-|
| 🌐 DNS | Route 53 | Domain Security |
| 🛡 Network | Shield | DDoS Protection |
| 🔥 Application | WAF | Web Attacks |
| 🏢 Network | VPC | Isolation |
| 🔑 Access | IAM | Permissions |
| 🔒 Data | Encryption | Data Protection |


---

# 🚀 High Availability


The architecture achieves availability through:


✅ Multiple Availability Zones  
✅ Load Balancing  
✅ Auto Scaling  
✅ Multi-AZ Databases  
✅ Route 53 Health Checks  
✅ CloudFront Distribution  


---

# 📊 Scalability


Services providing scalability:


| Service | Purpose |
|-|-|
| EC2 Auto Scaling | Adds/removes servers |
| ELB | Distributes traffic |
| CloudFront | Global content delivery |
| S3 | Unlimited storage |
| ElastiCache | Faster applications |


---

# 🌩 AWS vs Azure


| AWS | Azure |
|-|-|
| Route 53 | Azure DNS |
| CloudFront | Azure Front Door |
| AWS Shield | Azure DDoS Protection |
| EC2 | Azure VM |
| Auto Scaling | VM Scale Sets |
| VPC | Virtual Network |
| S3 | Blob Storage |
| RDS | Azure SQL |
| EFS | Azure Files |
| ElastiCache | Azure Cache Redis |


---

# 🎯 Learning Outcomes


After completing this study:

✔ Understand AWS enterprise architecture  
✔ Design highly available applications  
✔ Understand AWS networking  
✔ Understand security layers  
✔ Understand scaling strategies  
✔ Prepare for SAA-C03 exam scenarios  


---

# 👨‍💻 Author


## Christion W. E. Mushariwa

Software Engineer  
AWS Solutions Architect Associate Candidate


---

# ⭐ Support

If this repository helped your AWS learning journey:

⭐ Star this repository

📚 Share knowledge

🚀 Keep building cloud solutions


---

# 📜 License

Educational purposes only.

AWS trademarks belong to Amazon Web Services, Inc.
