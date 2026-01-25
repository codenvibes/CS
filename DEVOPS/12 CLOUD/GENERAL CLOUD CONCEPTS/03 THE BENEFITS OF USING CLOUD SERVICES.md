## High availability

When you’re deploying an application, a service, or any IT resources, it’s important the resources are available when needed. High availability focuses on ensuring maximum availability, regardless of disruptions or events that may occur.

When you’re architecting your solution, you’ll need to account for service availability guarantees. These guarantees are part of the service-level agreements (SLAs).

Absolutely — let’s break down **SLAs** in cloud computing, and then I’ll explain the typical percentage guarantees and why even small differences matter.


### What is an SLA?

**SLA** stands for **Service Level Agreement**. It’s a formal contract between a cloud service provider (like AWS, Azure, Google Cloud) and a customer. It defines:
- **What level of service is guaranteed** — typically things like uptime/availability, response time, support response, performance, etc.
- **How service is measured** — for example, “99.9% uptime per month”.
- **Penalties or credits** — what happens if the provider fails to meet the guarantee (e.g., you get a partial refund or credit).

### Common SLA metrics

The main one is **availability** — how much time the service must be operational during a given period (usually a month).
For example:
- **99% uptime**
- **99.9% uptime** (often called “three nines”)
- **99.99% uptime** (“four nines”)
- **99.999% uptime** (“five nines” — very rare and expensive)


### What do the percentages actually mean?

Here’s how downtime works out per month:

|SLA %|Max downtime per month|
|---|---|
|99%|~7.3 hours|
|99.9%|~43.8 minutes|
|99.99%|~4.38 minutes|
|99.999%|~26 seconds|

So the difference between 99.9% and 99.99% is about **39 extra minutes of uptime** per month — which can be critical for services that need to run 24/7, like financial systems or medical apps.


### Why small % differences matter

- **Revenue loss**: For e-commerce, minutes of downtime can cost thousands or millions in lost sales.
- **Reputation**: Frequent outages hurt customer trust.
- **Regulatory or safety impact**: Some sectors like healthcare, banking, or airlines simply can’t afford significant downtime.


### Things to watch out for

- **Exclusions**: SLAs often exclude planned maintenance or downtime due to things outside the provider’s control.
- **Compensation**: SLA breaches usually result in small credits, not big payouts.
- **Shared responsibility**: The SLA covers only what the provider manages — if your own app or config fails, that’s on you.


An SLA is both a guarantee and a risk management tool — but the percentage guarantees must align with how critical uptime is for your business.

---

## Scalability

Another major benefit of cloud computing is the scalability of cloud resources. ==Scalability refers to the ability to adjust resources to meet demand.== If you suddenly experience peak traffic and your systems are overwhelmed, the ability to scale means you can add more resources to better handle the increased demand.

The other benefit of scalability is that you aren't overpaying for services. Because the cloud is a consumption-based model, you only pay for what you use. If demand drops off, you can reduce your resources and thereby reduce your costs.

Scaling generally comes in two varieties: vertical and horizontal. Vertical scaling is focused on increasing or decreasing the capabilities of resources. Horizontal scaling is adding or subtracting the number of resources.

### Vertical scaling

With vertical scaling, if you were developing an app and you needed more processing power, you could vertically scale up to add more CPUs or RAM to the virtual machine. Conversely, if you realized you had over-specified the needs, you could vertically scale down by lowering the CPU or RAM specifications.

### Horizontal scaling

With horizontal scaling, if you suddenly experienced a steep jump in demand, your deployed resources could be scaled out (either automatically or manually). For example, you could add additional virtual machines or containers, scaling out. In the same manner, if there was a significant drop in demand, deployed resources could be scaled in (either automatically or manually), scaling in.


---

## Reliability

==Reliability is the ability of a system to recover from failures and continue to function.== 
The cloud, by virtue of its decentralized design, naturally supports a reliable and resilient infrastructure. With a decentralized design, the cloud enables you to have resources deployed in regions around the world. With this global scale, even if one region has a catastrophic event other regions are still up and running. You can design your applications to automatically take advantage of this increased reliability. In some cases, your cloud environment itself will automatically shift to a different region for you, with no action needed on your part. 

---

## Predictability

Predictability in the cloud lets you move forward with confidence. Predictability can be focused on performance predictability or cost predictability.

### Performance

Performance predictability focuses on predicting the resources needed to deliver a positive experience for your customers. Autoscaling, load balancing, and high availability are just some of the cloud concepts that support performance predictability. If you suddenly need more resources, autoscaling can deploy additional resources to meet the demand, and then scale back when the demand drops. Or if the traffic is heavily focused on one area, load balancing will help redirect some of the overload to less stressed areas.

### Cost

Cost predictability is focused on predicting or forecasting the cost of the cloud spend. With the cloud, you can track your resource use in real time, monitor resources to ensure that you’re using them in the most efficient way, and apply data analytics to find patterns and trends that help better plan resource deployments. By operating in the cloud and using cloud analytics and information, you can predict future costs and adjust your resources as needed. 

---

## Security and Governance in the cloud

Whether you’re deploying infrastructure as a service or software as a service, cloud features support governance and compliance. Things like set templates help ensure that all your deployed resources meet corporate standards and government regulatory requirements. Plus, you can update all your deployed resources to new standards as standards change. Cloud-based auditing helps flag any resource that’s out of compliance with your corporate standards and provides mitigation strategies. Depending on your operating model, software patches and updates may also automatically be applied, which helps with both governance and security.

On the security side, you can find a cloud solution that matches your security needs. If you want maximum control of security, infrastructure as a service provides you with physical resources but lets you manage the operating systems and installed software, including patches and maintenance. If you want patches and maintenance taken care of automatically, platform as a service or software as a service deployments may be the best cloud strategies for you.

And because the cloud is intended as an over-the-internet delivery of IT resources, cloud providers are typically well suited to handle things like distributed denial of service (DDoS) attacks, making your network more robust and secure.

By establishing a good governance footprint early, you can keep your cloud footprint updated, secure, and well managed.

---

## Manageability

A major benefit of cloud computing is the manageability options. There are two types of manageability for cloud computing that you’ll learn about in this series, and both are excellent benefits.

### Management of the cloud

Management of the cloud speaks to managing your cloud resources. In the cloud, you can:
- Automatically scale resource deployment based on need.
- Deploy resources based on a preconfigured template, removing the need for manual configuration.
- Monitor the health of resources and automatically replace failing resources.
- Receive automatic alerts based on configured metrics, so you’re aware of performance in real time.

### Management in the cloud

Management in the cloud speaks to how you’re able to manage your cloud environment and resources. You can manage these:
- Through a web portal.
- Using a command line interface.
- Using APIs.

---

## References

https://learn.microsoft.com/en-us/training/modules/describe-benefits-use-cloud-services/