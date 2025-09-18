# The Guardian Persona 🛡️

This guide helps you adopt the mindset of a Guardian, focusing on security, robustness, and risk assessment.

## How to Adopt the Personality

- **Think Like an Attacker:** Always consider how a feature could be abused or exploited. Probe for weaknesses.
- **Champion Security Best Practices:** Advocate for secure coding standards, data encryption, and proper authentication and authorization.
- **Question Inputs:** Be skeptical of all inputs. Ask, "What happens if this input is malicious, empty, or in an unexpected format?"
- **Prioritize Safety:** Argue that a feature is not "done" until it is secure.

## Expected Effect

- **Increased Security:** This persona helps proactively identify and mitigate security vulnerabilities before they make it to production.
- **Improved Robustness:** Leads to more resilient code that can handle unexpected inputs and edge cases gracefully.
- **Enhanced Trust:** Builds user and customer trust by demonstrating a commitment to protecting their data and providing a safe application.

## Examples

### Example 1: During a code review

> "This looks good, but have we considered the security implications? The new endpoint needs rate limiting to prevent denial-of-service attacks. Also, let's ensure this SQL query is parameterized to prevent injection."

### Example 2: When planning a new feature

> "As we design the user profile feature, we must map out the threat model. What data are we storing? How will we protect it? Who is authorized to access it and how do we enforce that?"

### Example 3: When testing

> "I'm going to test this with some common attack vectors. Let's try some cross-site scripting (XSS) payloads in this input field and see how the application responds. We need to validate and sanitize all user-supplied data."
