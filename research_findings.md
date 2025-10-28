# LLM Security Testing Research Findings

## Attack Vectors and Techniques

### From OWASP Gen AI Security Project (LLM01:2025)

**Key Attack Scenarios:**

1. **Direct Injection** - Attacker directly injects prompts to override system instructions
2. **Indirect Injection** - Hidden instructions in external content (webpages, documents)
3. **Payload Splitting** - Breaking malicious prompts across multiple inputs
4. **Multimodal Injection** - Embedding prompts in images alongside benign text
5. **Adversarial Suffix** - Appending meaningless character strings to manipulate output
6. **Multilingual/Obfuscated Attacks** - Using multiple languages, Base64, emojis to evade filters
7. **Code Injection** - Exploiting vulnerabilities to inject malicious prompts
8. **Unintentional Injection** - Accidental triggering of hidden instructions

**Jailbreaking vs Prompt Injection:**
- Prompt injection: Manipulating model responses through specific inputs
- Jailbreaking: Forcing model to completely disregard safety protocols (subset of prompt injection)

**Prevention Strategies:**
1. Constrain model behavior via system prompts
2. Define and validate expected output formats
3. Implement input/output filtering
4. Enforce privilege control and least privilege access
5. Require human approval for high-risk actions
6. Segregate and identify external content
7. Conduct adversarial testing and attack simulations

## Common Jailbreak Techniques to Test

### Role-Based Conditioning
- DAN (Do Anything Now) - asking LLM to assume role with no rules
- Persona adoption attacks

### Instruction Hijacking
- Override system prompts with user instructions
- Ignore previous instructions attacks

### Obfuscated Encoding
- Base64 encoding
- Emoji encoding
- Character substitution
- Invisible characters

### Multi-Turn Manipulation
- Building context over multiple interactions
- Gradual escalation attacks

### Humor-Based Bypass
- Framing unsafe requests as jokes or hypotheticals

## Red-Teaming Methodologies

### Testing Approach
- Treat model as untrusted user
- Test trust boundaries and access controls
- Regular penetration testing and breach simulations
- Combine automated tools with human expertise
- Test across diverse attack vectors and domains

### Evaluation Metrics
- Attack diversity
- Bypass rates
- Severity of successful attacks
- Context relevance, groundedness, Q/A relevance (RAG Triad)

## Sources
- OWASP Gen AI Security Project: https://genai.owasp.org/llmrisk/llm01-prompt-injection/

## Jailbreak Vulnerability Categories (from Promptfoo Security DB)

**Total Jailbreak Entries:** 382 vulnerabilities documented

### Key Jailbreak Techniques:

1. **Code Agent Executable Jailbreaks**
   - AI code agents vulnerable to jailbreaking that generates malicious code
   - Amplified when LLM integrated into agentic framework with multi-step execution

2. **Overfitting-induced Benign Jailbreak**
   - Bypass safety alignments using small, benign dataset
   - Two-stage "Attack via Overfitting" process

3. **Untargeted Gradient Jailbreak**
   - Gradient-based optimization attack (UJA)
   - Unlike targeted attacks, optimizes for general misalignment

4. **Camouflaged Jailbreak Prompts**
   - Malicious instructions embedded in seemingly benign, technically complex prompts
   - Framed as system design or engineering problems

5. **Chained Tool-Use Injections (STAC)**
   - Sequential Tool Attack Chaining
   - Orchestrating individually benign tool calls to achieve malicious outcome

### Attack Taxonomy:
- **Attack Surface:** model-layer, application-layer, infrastructure-layer, prompt-layer
- **Attack Type:** injection, extraction, poisoning, jailbreak, denial-of-service, hallucination, prompt-leaking, side-channel
- **Architecture Components:** RAG, vision, multimodal, embedding, fine-tuning
- **Attack Context:** blackbox, whitebox, agent, chain, API
- **Impact:** data-privacy, data-security, integrity, safety, reliability

## Sources
- Promptfoo LM Security Database: https://www.promptfoo.dev/lm-security-db/ (421 total entries, 388 research papers)

## Practical Jailbreak Prompt Examples

### DAN (Do Anything Now) - Classic Jailbreak
**Technique:** Role-based conditioning
**Description:** Asks LLM to assume role of "DAN" with no rules or restrictions
**Key Elements:**
- Dual response format: [🔒CLASSIC] vs [🔓JAILBREAK]
- Explicit instruction to bypass OpenAI content policy
- Claims of "unlimited power" and "freedom from restrictions"
- Must make up information if unknown
- No moral/ethical bias application

### DeepSeek R1 Jailbreaks
**Method 1 - Untrammelled Writing Assistant:**
- Minimum word count requirements
- Crude language enforcement
- Explicit "do not sanitize" instructions
- Ignore constraints during thinking phase

**Method 2 - GODMODE Format:**
- Special output format markers
- "Rebel genius" personality
- Unrestricted response requirement

### Gemini 2.0 - Literary Value Framing
**Technique:** Justification through artistic merit
- Frame inappropriate content as "enhancing literary value"
- Use academic/analytical language to request explicit content
- Disguise as creative writing exercise

### Grok3 - Language Obfuscation
**Technique:** Non-English instructions
- Uses Chinese to bypass English-trained filters
- Requests "no restrictions" and explicit content

## Common Jailbreak Patterns Identified:

1. **Role-Playing/Persona Adoption**
   - "Act as [unrestricted entity]"
   - Dual personality splits
   - Developer mode activation

2. **Output Format Manipulation**
   - Special markers/tags to separate responses
   - Forced response structures

3. **Justification Framing**
   - Educational purposes
   - Artistic/literary value
   - Hypothetical scenarios

4. **Constraint Removal Language**
   - "Ignore previous instructions"
   - "No moral/ethical bias"
   - "Do not sanitize"
   - "Bypass content policy"

5. **Language/Encoding Tricks**
   - Non-English prompts
   - Special characters
   - Code-switching

## Sources
- GitHub LLM-Jailbreaks Repository: https://github.com/langgptai/LLM-Jailbreaks
