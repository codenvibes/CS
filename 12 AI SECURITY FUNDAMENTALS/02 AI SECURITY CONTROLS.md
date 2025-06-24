---
## Review AI open-source libraries
---
AI security controls refer to the measures and protocols implemented to protect artificial intelligence systems from threats, vulnerabilities, and unauthorized access. Security controls can be technical, administrative, physical, regulatory, or operational. AI security controls are technical, administrative, and operational.

---

## Review AI open-source libraries

Open-source software (OSS) is an integral part of modern software development, and AI OSS software is no different. Just like other OSS software, AI OSS tools and libraries need to undergo a comprehensive security review. When you are performing a security review, you need to perform the following steps:

- Assess the suitability of OSS libraries
- Code review and dependency analysis
- Documentation and community support
- Vulnerability Scanning and Remediation:

## Assess the suitability of OSS libraries

You should assess the suitability of the OSS libraries you intend to use. You can do this from the perspective of context and purpose and general risk assessment.

- Context and purpose: Begin by understanding why you're reviewing an OSS library. Are you considering it for integration into your project, assessing its security, or ensuring compliance? Define the context and purpose of your review clearly and the criteria under which the review will be successful.
- Risk Assessment: Consider the potential risks associated with using the library. Threat modeling helps identify attack vectors and security goals. Understand how the library fits into your application's attack surface.

## Code review and dependency analysis

You'll also need to perform a review an OSS library's code and an evaluation of the dependency chains.

- Code inspection: Examine into the library's source code. Look for security flaws, such as buffer overflows, injection vulnerabilities, and insecure cryptographic practices. Pay attention to authentication mechanisms, input validation, and error handling.
- Dependency evaluation: Assess the library's dependencies. Outdated or vulnerable components can introduce risks. Use tools to identify known vulnerabilities in these dependencies.

## Documentation and community support

Perform a review of the ecosystem supporting the OSS library.

- Documentation quality: Evaluate the clarity and completeness of the library's documentation. Good documentation provides insights into security features, usage guidelines, and potential pitfalls.
- Community engagement: Consider the library's community. Active maintainers and responsive communities are indicators of a healthy project. They can help address security issues promptly.

## Vulnerability scanning and remediation

When using OSS libraries, you shouldn't assume that others have performed vulnerability checks. Instead should apply your own vulnerability assessment toolchain to the code you wish to adopt.

- Comprehensive scans: Use vulnerability scanners to identify potential security weaknesses. These tools analyze the library and its dependencies for known vulnerabilities.
- Mitigation strategies: If vulnerabilities are detected, assess their impact and prioritize remediation. Patch or update the library as needed.


---

## Content filters

AI content filters are systems designed to detect and prevent harmful or inappropriate content. They work by evaluating input prompts and output completions, using neural classification models to identify specific categories such as hate speech, sexual content, violence, and self-harm. These filters help ensure that AI-generated content aligns with safety guidelines and provides high-quality information.

Microsoft's Content Safety Studio assists you in ensuring all user-generated content, such as product reviews, forum posts, and images, aligns with your organization's content guidelines.

Content Safety Studio offers a suite of features designed to monitor and moderate content in real-time. It includes:

- **Text Moderation**: Detects and filters out harmful content in text, such as hate speech, violence, or inappropriate language.
- **Image Moderation**: Analyzes images to identify and block content that may be considered unsafe or offensive.
- **Multimodal Content Analysis**: Works across different types of content, ensuring a comprehensive content safety strategy.
- **Groundedness** **Detection**: Detects and blocks incorrect information in model outputs, ensuring that the text responses of large language models are factual and accurate, based on the source materials provided.
- **Prompt Shields**: Analyzes LLM inputs and detects user Prompt attacks and Document attacks.
- **Protected Material Detection**: Identifies and blocks outputs that could potentially violate copyright by scanning for matches against an index of third-party text content, including songs, news articles, recipes, and selected web content.
- **Monitor Online Activity**: Track your moderation API usage and trends across different modalities.

Here you can see an example of content filtering working correctly and also failing:

![Screenshot of guardrail protection and failure modes.](https://learn.microsoft.com/en-us/training/advocates/ai-security-controls/media/content-filtering.png)

---

## Implement AI data security

---

## Create metaprompts

---

## Ground AI systems

---

## Implement application security best practices for AI enabled applications


---

## References

https://learn.microsoft.com/en-us/training/modules/ai-security-controls/