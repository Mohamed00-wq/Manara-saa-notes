# Summary — AWS Global Infrastructure


* The AWS Cloud spans 39+ Regions and 123+ Availability Zones worldwide.
* A Region is a geographic area containing at least 3 Availability Zones, connected via AWS's private global network.
* Regions launched after March 2019 are disabled by default and must be manually enabled.
* Local Zones, Wavelength Zones, and Outposts are distinct infrastructure extensions — don't confuse them.
* Data does not automatically replicate across Regions — that is your responsibility as an architect.

**SAA Exam Tip:** AZ identifiers (a, b, c) are mapped differently per AWS account — `us-east-1a` in your account is not necessarily the same physical location as `us-east-1a` in another account. The exam tests this distinction.


# Summary — Availability

10 mins read

* High availability means a system stays accessible with minimal downtime, even during failures.
* AWS achieves this through multiple AZs, Elastic Load Balancing, Auto Scaling, and built-in fault-tolerant services (S3, RDS, DynamoDB).
* Distributing resources across AZs allows an application to keep running if one AZ fails.
* Auto Scaling and Load Balancing work together to maintain performance under varying demand.

**SAA Exam Tip:** High availability = multiple AZs in the same Region. Disaster recovery = multiple Regions. Know the difference — the exam tests this distinction regularly.


# Summary — Edge Locations

10 mins read

* Edge locations are globally distributed endpoints, primarily used by Amazon CloudFront (CDN), to reduce latency.
* PoPs (Points of Presence) consist of 600+ edge locations and 13+ regional mid-tier caches.
* Regional edge caches sit between edge locations and the origin server, caching less-popular content to avoid a full origin round-trip.
* Edge locations are also used by Route 53 and AWS Global Accelerator, not just CloudFront.

**SAA Exam Tip:** Know which AWS service uses which part of the edge network (CloudFront vs. Route 53 vs. Global Accelerator) — scenario questions frequently test this.