==Cloud computing is the on-demand delivery of IT resources/services over the internet with pay as you go pricing.==

Because cloud computing uses the internet to deliver these services, it doesn’t have to be constrained by physical infrastructure the same way that a traditional datacenter is. That means if you need to increase your IT infrastructure rapidly, you don’t have to wait to build a new datacenter—you can use the cloud to rapidly expand your IT footprint.

---

## Careers In Cloud Computing

| **Domain**     | **Role Title**                | **Role Description**                                                                                                                                      |
| -------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Architecture   | Solutions Architect           | Design, develop, and manage cloud infrastructure and assets; work with DevOps to migrate applications to the cloud.                                       |
| Architecture   | Application Architect         | Design significant aspects of application architecture including UI, middleware, and infrastructure, ensuring scalable, reliable, and manageable systems. |
| Data Analytics | Cloud Data Engineer           | Automate collection and processing of structured/semi-structured data; monitor data pipeline performance.                                                 |
| Development    | Software Development Engineer | Develop, construct, and maintain software across platforms and devices.                                                                                   |
| Operations     | Systems Administrator         | Install, upgrade, and maintain computer components and software; integrate automation processes.                                                          |
| Operations     | Cloud Engineer                | Implement and operate networked computing infrastructure; implement security systems for data safety.                                                     |
| DevOps         | Test Engineer                 | Embed testing and quality best practices for software development from design to release throughout the product life cycle.                               |
| DevOps         | Cloud DevOps Engineer         | Design, deploy, and operate large-scale global hybrid cloud environments; advocate for automated CI/CD pipelines.                                         |
| DevOps         | DevSecOps Engineer            | Accelerate enterprise cloud adoption while enabling rapid and stable delivery using CI/CD principles and technologies.                                    |
| Security       | Cloud Security Engineer       | Design computer security architecture and detailed cyber security designs; develop, execute, and track security measures to protect information.          |
| Security       | Cloud Security Architect      | Design and implement enterprise cloud solutions; apply governance to identify, communicate, and minimize business and technical risks.                    |
| Networking     | Network Engineer              | Design and implement computer and information networks such as LANs, WANs, intranets, extranets, etc.                                                     |
| AI/ML          | Prompt Engineer               | Design, test, and refine text prompts to optimize AI language model performance.                                                                          |
| AI/ML          | Machine Learning Engineer     | Research, build, and design AI systems to automate predictive models; design machine learning systems, models, and schemes.                               |
| AI/ML          | Machine Learning Ops Engineer | Build and maintain AI/ML platforms and infrastructure; design, implement, and support AI/ML model deployment infrastructure.                              |
| AI/ML          | Data Scientist                | Develop and implement AI/ML models to solve business problems; train, fine-tune, and evaluate models.                                                     |

---

## Shared Responsibility Model

In a traditional corporate datacenter the company is responsible for maintaining the physical space, ensuring security, and maintaining or replacing the servers if anything happens. The IT department is responsible for maintaining all the infrastructure and software needed to keep the datacenter up and running. They’re also likely to be responsible for keeping all systems patched and on the correct version.

With the shared responsibility model, these responsibilities get shared between the cloud provider and the consumer. Physical security, power, cooling, and network connectivity are the responsibility of the cloud provider. The consumer isn’t collocated with the datacenter, so it wouldn’t make sense for the consumer to have any of those responsibilities.

> _Collocated_ = physically together in the same location.

At the same time, the consumer is responsible for the data and information stored in the cloud. (You wouldn’t want the cloud provider to be able to read your information.) The consumer is also responsible for access security, meaning you only give access to those who need it.

Then, for some things, the responsibility depends on the situation. If you’re using a cloud SQL database, the cloud provider would be responsible for maintaining the actual database. However, you’re still responsible for the data that gets ingested into the database. If you deployed a virtual machine and installed an SQL database on it, you’d be responsible for database patches and updates, as well as maintaining the data and information stored in the database.

==With an on-premises datacenter, you’re responsible for everything. With cloud computing, those responsibilities shift. The shared responsibility model is heavily tied into the cloud service types: infrastructure as a service (IaaS), platform as a service (PaaS), and software as a service (SaaS). IaaS places the most responsibility on the consumer, with the cloud provider being responsible for the basics of physical security, power, and connectivity. On the other end of the spectrum, SaaS places most of the responsibility with the cloud provider. PaaS, being a middle ground between IaaS and SaaS, rests somewhere in the middle and evenly distributes responsibility between the cloud provider and the consumer.==

The following diagram highlights how the Shared Responsibility Model informs who is responsible for what, depending on the cloud service type.

![Diagram showing the responsibilities of the shared responsibility model.](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/shared-responsibility-b3829bfe.svg)

When using a cloud provider, you’ll always be responsible for:
- The information and data stored in the cloud
- Devices that are allowed to connect to your cloud (cell phones, computers, and so on)
- The accounts and identities of the people, services, and devices within your organization

The cloud provider is always responsible for:
- The physical datacenter
- The physical network
- The physical hosts

Your service model will determine responsibility for things like:
- Operating systems
- Network controls
- Applications
- Identity and infrastructure

---

## References

http://learn.microsoft.com/en-us/training/modules/describe-cloud-compute/

