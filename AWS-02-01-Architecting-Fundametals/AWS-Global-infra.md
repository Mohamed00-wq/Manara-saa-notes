# AWS Global Infrastructure


* AWS offers 200+ fully featured services from data centers across the globe.

* The AWS Cloud spans 123+ Availability Zones across 39+ geographic Regions (these numbers grow regularly — always verify at the AWS Global Infrastructure page).

* A **Region** is a physical geographic location containing a cluster of data centers, grouped into at least 3 Availability Zones (some newer regions launched with fewer, but the current standard is 3+).

* Regions are connected to ISPs and AWS's private global network, which reduces latency compared to the public internet.

* Regions launched after March 20, 2019 (e.g., Asia Pacific (Hong Kong), Middle East (Bahrain)) are **disabled by default** and must be manually enabled via the AWS Management Console.

* Certain Regions, like **AWS GovCloud (US)**, have restricted access for regulatory compliance.

* Regions are isolated for fault tolerance — **data is not automatically replicated across Regions**; this is the architect's responsibility.

* Not all AWS services are available in every Region.

* **Region selection factors:** Latency, Cost, Compliance, Service Availability.

* An **Availability Zone (AZ)** consists of one or more data centers, is designed for fault isolation, and is interconnected with other AZs in the same Region via high-speed private links.

* For certain services, you can choose your specific AZ. AWS recommends replicating across AZs for resiliency.

* **SAA Exam Tip:** AZ letter identifiers (a, b, c) are mapped per AWS account — `us-east-1a` in your account may not be the same physical data center as `us-east-1a` in another account. AWS shuffles these to distribute load evenly.

* **Local Zones** bring AWS services (compute, storage, databases) closer to areas without a full Region — designed for latency-sensitive apps (real-time gaming, media creation, ML), offering single-digit millisecond latency. Each Local Zone is an extension of an AWS Region and integrates with EC2, VPC, and EBS.

* **SAA Exam Tip — don't confuse these three infrastructure extension types:**
  - **Local Zones** — metro-area latency for cities without a full Region (e.g., Los Angeles Local Zone)

  - **Wavelength Zones** — embed AWS compute inside telecom 5G networks for ultra-low latency mobile/edge workloads

  - **AWS Outposts** — fully managed AWS rack deployed in your on-premises data center; same APIs, same console
  - If a scenario mentions 5G/mobile edge → Wavelength. On-prem/data center extension → Outposts. Low-latency for a major metro city → Local Zone.

* **AWS Data Centers:** house the actual data; you don't choose a specific data center for your resources. Failures are rare but can happen — if all instances are in one data center, a failure there can affect availability. Automated systems reroute traffic to keep services running. Core applications use **N+1 redundancy** for load balancing across other sites if a data center goes down. AWS uses custom networking equipment from multiple manufacturers, designed to meet its specific needs.


# Availability


* **High availability (HA)** = the ability of a system/application to remain accessible and operational with minimal downtime, even during failures or disruptions.

* AWS achieves HA through 4 mechanisms:
  1. **Multiple Availability Zones (AZs):** Regions are divided into isolated AZs (separate data centers). Distributing resources across multiple AZs lets applications keep running even if one AZ fails.
  2. **Load Balancing:** AWS Elastic Load Balancers (ELB) distribute traffic across healthy instances in multiple AZs, ensuring continued availability during failures or traffic spikes.
  3. **Auto Scaling:** AWS Auto Scaling automatically adjusts the number of instances based on demand, maintaining performance and availability.
  4. **Fault Tolerance:** Services like Amazon S3, RDS, and DynamoDB are designed with built-in fault tolerance, ensuring data availability and reliability.

* Together, these features minimize downtime and ensure a system remains accessible under various conditions.


# AWS Edge Locations


* **Edge locations** are data centers located globally that serve as endpoints for AWS services, primarily for content delivery and caching. They are part of **Amazon CloudFront** (AWS's CDN) and are designed to reduce latency by bringing content closer to users.

* **Key purposes of edge locations:**
  1. **Content Delivery:** cache copies of static and dynamic content (web pages, videos, images) to reduce load times.

  2. **Reduced Latency:** serving content from the nearest edge location to the user minimizes data travel time, improving performance.

  3. **Global Reach:** AWS has many edge locations worldwide, allowing fast content delivery to users in different regions.

* **PoPs (Points of Presence)** are comprised of **600+ edge locations** and **13+ regional mid-tier caches**. PoPs are the initial destination for a CloudFront request.

* **SAA Exam Tip:** Edge locations are used by **CloudFront**, **Route 53**, and **AWS Global Accelerator** — know which service uses which part of the network, as this comes up frequently in scenario questions.

* **Regional Edge Caches:**
  - Bring more content closer to viewers, even when it's not popular enough to stay at a PoP.

  - Used **by default** with CloudFront.

  - Absorb content that isn't accessed frequently enough to remain at an edge location.
  
  - Provide an alternative to fetching content directly from the origin server, helping improve performance.