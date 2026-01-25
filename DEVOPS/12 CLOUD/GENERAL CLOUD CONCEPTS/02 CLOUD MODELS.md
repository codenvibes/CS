What are cloud models? ==Cloud models define the deployment type of cloud resources.== The three main cloud models are: private, public, and hybrid.

---

## Private cloud

Let’s start with a private cloud. A private cloud is, in some ways, the natural evolution from a corporate datacenter. It’s a cloud (delivering IT services over the internet) that’s used by a single entity. Private cloud provides much greater control for the company and its IT department. However, it also comes with greater cost and fewer of the benefits of a public cloud deployment. Finally, a private cloud may be hosted from your on site datacenter. It may also be hosted in a dedicated datacenter offsite, potentially even by a third party that has dedicated that datacenter to your company.

**Real-Life Example:**
A bank has strict data compliance rules and runs its own private cloud using OpenStack on servers in its own data center. Only the bank’s departments access it.

---

## Public cloud

A public cloud is built, controlled, and maintained by a third-party cloud provider. With a public cloud, anyone that wants to purchase cloud services can access and use resources. The general public availability is a key difference between public and private clouds.

**Real-Life Example:**
A startup runs its entire website and databases on AWS EC2 and S3 — no servers in their office, everything is in Amazon’s data centers.

---

## Hybrid cloud

A hybrid cloud is a computing environment that uses both public and private clouds in an inter-connected environment. A hybrid cloud environment can be used to allow a private cloud to surge for increased, temporary demand by deploying public cloud resources. Hybrid cloud can be used to provide an extra layer of security. For example, users can flexibly choose which services to keep in public cloud and which to deploy to their private cloud infrastructure.

**Real-Life Example:**
A bank has strict data compliance rules and runs its own private cloud using OpenStack on servers in its own data center. Only the bank’s departments access it.

The following table highlights a few key comparative aspects between the cloud models.

|**Public cloud**|**Private cloud**|**Hybrid cloud**|
|---|---|---|
|No capital expenditures to scale up|Organizations have complete control over resources and security|Provides the most flexibility|
|Applications can be quickly provisioned and deprovisioned|Data is not collocated with other organizations’ data|Organizations determine where to run their applications|
|Organizations pay only for what they use|Hardware must be purchased for startup and maintenance|Organizations control security, compliance, or legal requirements|
|Organizations don’t have complete control over resources and security|Organizations are responsible for hardware maintenance and updates||

---

## Multi-cloud

A fourth, and increasingly likely scenario is a multi-cloud scenario. In a multi-cloud scenario, you use multiple public cloud providers. Maybe you use different features from different cloud providers. Or maybe you started your cloud journey with one provider and are in the process of migrating to a different provider. Regardless, in a multi-cloud environment you deal with two (or more) public cloud providers and manage resources and security in both environments.

---

## References

https://learn.microsoft.com/en-us/training/modules/describe-cloud-compute/5-define-cloud-models