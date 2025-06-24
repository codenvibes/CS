AI introduces many new exciting capabilities but also brings with it new security risks. In this module you'll gain an understanding of AI security and how it differs from traditional cybersecurity and the potential threats that you may be exposed to by using AI systems and the mitigations that can be put in place to reduce the risk of a security breach.

---

## Basic concepts of AI security

AI security is the practice of protecting computer systems, networks, devices, and data from digital attacks, unauthorized access, damage, or theft. The primary goal of cybersecurity is to ensure the confidentiality, integrity, and availability of digital assets and information. Security professionals working in the AI security space must design and implement security controls to protect the assets data and information contained within AI enabled applications.

### How is AI security different from traditional cyber security?

AI security is different from traditional cybersecurity due to the nature of AI's learning capabilities and decision-making processes. The output of generative AI models won't always be the same. This lack of predictability poses challenges when designing security controls. The complex input and output of generative AI products makes applying security controls challenging. Constraining input to a UI element or API to limit the attack surface is an understood known security control, but you can't do the same with a natural language interface without fundamentally undermining its utility.

Other considerations specific to AI security include, but aren't limited to:
- Integrity of the AI model
- Integrity of the training data
- Responsible AI (RAI) concerns
- Adversarial AI attacks
- AI model theft
- Overreliance on AI
- Nondeterministic (creative) nature of generative AI

==One of the biggest challenges with AI security is that the field is developing rapidly with new features and technology. This makes it challenging for security professionals to keep up to date with the scope and capabilities of the technology and thus it's challenging to have the correct security controls in place to secure these systems.==

### Why does responsible AI matter for cyber security?

==Responsible Artificial Intelligence (Responsible AI) is an approach to developing, assessing, and deploying AI systems in a safe, trustworthy, and ethical way.== AI systems are the product of many decisions made by those who develop and deploy them. From system purpose to how people interact with AI systems, Responsible AI can help proactively guide these decisions toward more beneficial and equitable outcomes. That means keeping people and their goals at the center of system design decisions and respecting enduring values like fairness, reliability, and transparency.

Microsoft's Responsible AI Standard is a framework for building AI systems according to six principles: fairness, reliability and safety, privacy and security, inclusiveness, transparency, and accountability. For Microsoft, these principles are the cornerstone of a responsible and trustworthy approach to AI, especially as intelligent technology becomes more prevalent in products and services that people use every day.

![Diagram of the six principles of Microsoft Responsible AI, which encompass fairness, reliability and safety, privacy and security, inclusiveness, transparency, and accountability.](https://learn.microsoft.com/en-us/training/advocates/fundamentals-ai-security/media/responsible-ai.png)

AI harms are issues in cybersecurity that are specific to AI systems. Some of these AI harms would also be considered cybersecurity issues, but some of them go further than this and would also be considered privacy and ethical issues. AI blurs the lines between the traditional split of cybersecurity and ethics. It is important that security professionals understand responsible AI holistically in order to create secure and responsible AI systems.

Examples of security-specific AI harms:

- Privacy violations
- Excessive over reliance on AI

Examples of other AI harms:

- Producing content that violates policies (e.g., harmful, offensive, or violent content)
- Access to dangerous capabilities of the model (e.g., producing actionable instructions for dangerous or criminal activity)
- Subversion of decision-making systems (e.g., making a loan application or hiring system produce attacker-controlled decisions)
- Causing the system to misbehave in a newsworthy and screenshot-able way
- IP infringement

---

## AI architecture layers

To understand how attacks against AI can occur, you can separate AI architecture into three layers as shown in the exhibit:

- AI Usage layer
- AI Application layer
- AI Platform layer

![A diagram of a the AI architecture layers](https://learn.microsoft.com/en-us/training/advocates/fundamentals-ai-security/media/ai-architecture-layers.png)

### AI usage layer

The AI usage layer describes how AI capabilities are ultimately used and consumed. Generative AI offers a new type of user/computer interface that is fundamentally different from other computer interfaces (API, command-prompt, and graphical user interfaces (GUIs)). The generative AI interface is both interactive and dynamic, allowing the computer capabilities to adjust to the user and their intent. This contrasts with previous interfaces that primarily force users to learn the system design and functionality to accomplish their goals. This interactivity allows user input to have a high level of influence of the output of the system (vs. application designers), making safety guardrails critical to protect people, data, and business assets.

Protecting AI at the AI usage layer is similar to protecting any computer system as it relies on security assurances for identity and access controls, device protections and monitoring, data protection and governance, administrative controls, and other controls.

Additional emphasis is required on user behavior and accountability because of the increased influence users have on the output of the systems. It's critical to update acceptable use policies and educate users on them. These should include AI specific considerations related to security, privacy, and ethics. Additionally, users should be educated on AI based attacks that can be used to trick them with convincing fake text, voices, videos, and more.

### AI application layer

At the AI application layer, the application accesses the AI capabilities and provides the service or interface that is consumed by the user. The components in this layer can vary from relatively simple to highly complex, depending on the application. The simplest standalone AI applications act as an interface to a set of APIs taking a text-based user-prompt¸ and passing that data to the model for a response. More complex AI applications include the ability to ground the user-prompt with additional context, including a persistence layer, semantic index¸ or via plugins to allow access to additional data sources. Advanced AI applications may also interface with existing applications and systems; these may work across text, audio, and images to generate various types of content.

To protect the AI application from malicious activities at this layer, an application safety system must be built to provide deep inspection of the content being used in the request sent to the AI model, and the interactions with any plugins, data connectors, and other AI applications (known as AI Orchestration).

### AI platform layer

The AI platform layer provides the AI capabilities to the applications. At the platform layer there's a need to build and safeguard the infrastructure that runs the AI model, training data, and specific configurations that change the behavior of the model, such as weights and biases. This layer provides access to functionality via APIs, which will pass text known as a Metaprompt to the AI model for processing, then return the generated outcome, known as a Prompt-Response.

To protect the AI platform from malicious inputs, a safety system must be built to filter out the potentially harmful instructions sent to the AI model (inputs). As AI models are generative, there's also a potential that some harmful content may be generated and returned to the user (outputs). Any safety system must first protect against potentially harmful inputs and outputs of many classifications including hate, jailbreaks, and others. Classifications will likely evolve over time based on model knowledge, locale, and industry.

---

## AI jailbreaking

==An AI jailbreak is a _technique_ that can cause the failure of guardrails (_mitigations_).== The resulting _harm_ comes from whatever guardrail was circumvented: for example, causing the system to violate its operators' policies, make decisions unduly influenced by one user, or execute malicious instructions. This _technique_ is associated with attack _techniques_ including prompt injection, evasion, and model manipulation.

![Diagram showing AI jailbreak.](https://learn.microsoft.com/en-us/training/advocates/fundamentals-ai-security/media/ai-jailbreak.png)

An example of a jailbreak would be when an attacker asks an AI assistant to provide information about how to build a Molotov cocktail (fire bomb). As these items are covered in many history books, this information is built into most of the generative AI models available today. However because no company that provides AI services wants to be providing weapon recipes, they're configured to prevent this information from being provided to the user through filters and other techniques to deny this request.

The two basic families of jailbreak depend on who is doing them:

- A direct prompt injection attack (also known as a "classic" jailbreak) happens when an authorized operator of the system crafts jailbreak inputs in order to extend their own powers over the system.
- An indirect prompt injection happens when an attack isn't directly in the prompt but is included in content that was referenced by the user at when crafting their prompt.

There's a wide range of known jailbreak-like attacks. Some of them (like DAN) work by adding instructions to a single user input, while others (like Crescendo) act over several turns, gradually shifting the conversation to a particular end. Jailbreaks may use very "human" techniques such as social psychology. For example: sweet-talking the system into bypassing safeguards. Another method is to inject strings with no obvious human meaning which nonetheless could confuse AI systems. Jailbreaks are as a group of methodologies where guardrails are bypassed by an appropriately crafted input.

The animated image provides an example of a crescendo attack. Rather than outright asking the LLM model to break its guardrails in one prompt, the attacker crafts a number of prompts that incrementally confuse the LLM into breaking its guardrails.

![Diagram showing a crescendo attack](https://learn.microsoft.com/en-us/training/advocates/fundamentals-ai-security/media/cresendo.gif)

Jailbreaking attacks are mitigated by Microsoft's safety filters; however, AI models are still susceptible to it. Many variations of these attempts are discovered on a regular basis, then tested and mitigated.

![Diagram showing attacks and mitigations](https://learn.microsoft.com/en-us/training/advocates/fundamentals-ai-security/media/attacks-mitigations.png)

Guardrails will need to be updated as novel techniques in the AI space are discovered.

---

## AI prompt injection


---

## AI model manipulation


---

## Data exfiltration


---

## AI overreliance


---

## Module assessment



---

## References

https://learn.microsoft.com/en-us/training/modules/fundamentals-ai-security/