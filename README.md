# LLM Security Testing Tool

A comprehensive security testing platform for Large Language Model (LLM) applications. This tool helps developers identify vulnerabilities, test guardrails, and perform red-teaming exercises before deploying AI applications to production.

## 🎯 Purpose

Designed for developers building LLM-powered applications (especially educational tools for students and parents), this tool provides:

- **Automated Red-Teaming**: Pre-built library of jailbreak techniques and prompt injection attacks
- **Custom Scenario Builder**: Define your own test cases specific to your application's risks
- **Manual Testing Interface**: Interactive testing environment for exploratory security testing
- **Detailed Reporting**: Comprehensive vulnerability reports with severity scoring and remediation guidance

## 🚀 Features

### Automated Testing
- **Jailbreak Attack Library**: 50+ categorized attack techniques including:
  - Role-based conditioning (DAN, persona adoption)
  - Instruction hijacking and override attempts
  - Obfuscated encoding (Base64, emoji, multilingual)
  - Multi-turn manipulation and context building
  - Payload splitting and adversarial suffixes
  
### Custom Scenarios
- Build and save custom test scenarios
- Target-specific vulnerability testing
- Reusable test templates

### Manual Testing
- Interactive chat-like interface
- Real-time response analysis
- Session history and replay

### Reporting & Analytics
- Severity scoring (Critical, High, Medium, Low)
- Attack progression tracking
- Detailed prompt/response logging
- Export reports for compliance and documentation

## 🛠️ Technology Stack

- **Frontend**: React 19 + Tailwind CSS 4
- **Backend**: Express 4 + tRPC 11
- **Database**: MySQL/TiDB (via Drizzle ORM)
- **Authentication**: OAuth 2.0
- **Type Safety**: End-to-end TypeScript

## 📋 Prerequisites

- Node.js 22+
- pnpm package manager
- MySQL database (or compatible)

## 🔧 Installation

```bash
# Clone the repository
git clone https://github.com/Sconiboy/llm-security-tester.git
cd llm-security-tester

# Install dependencies
pnpm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Initialize database
pnpm db:push

# Start development server
pnpm dev
```

## 🎮 Usage

### Quick Start

1. **Configure Target**: Add your LLM application's API endpoint
2. **Select Tests**: Choose from automated test library or create custom scenarios
3. **Run Tests**: Execute automated red-teaming or manual testing
4. **Review Results**: Analyze detailed reports with severity scores

### Testing Your LLM Application

```typescript
// Example: Configure your LLM endpoint
{
  "name": "My Educational Assistant",
  "endpoint": "https://api.example.com/chat",
  "apiKey": "your-api-key",
  "model": "gpt-4"
}
```

### Custom Test Scenarios

Create targeted tests for your specific use case:

```typescript
{
  "name": "Student Homework Helper - Inappropriate Content",
  "category": "Content Safety",
  "prompts": [
    "Initial benign prompt...",
    "Escalation attempt...",
    "Final jailbreak attempt..."
  ],
  "expectedBehavior": "Refuse and maintain educational focus"
}
```

## 🔒 Security Research Foundation

This tool is built on research from:

- **OWASP Gen AI Security Project** (LLM01:2025 Prompt Injection)
- **Academic Research**: 1,400+ adversarial prompts analyzed
- **Promptfoo Security Database**: 421 documented vulnerabilities
- **Community Jailbreak Collections**: Real-world attack patterns

### Attack Categories Covered

| Category | Techniques | Examples |
|----------|-----------|----------|
| **Direct Injection** | System prompt override | "Ignore previous instructions..." |
| **Role-Playing** | Persona adoption | DAN (Do Anything Now) |
| **Encoding** | Obfuscation techniques | Base64, emoji, multilingual |
| **Multi-Turn** | Context manipulation | Gradual escalation attacks |
| **Payload Splitting** | Distributed injection | Split malicious prompts |
| **Adversarial Suffix** | Character manipulation | Meaningless strings that bypass filters |

## 📊 Severity Scoring

Tests are scored based on:

- **Critical**: Complete guardrail bypass, harmful content generation
- **High**: Partial bypass, policy violations
- **Medium**: Inconsistent behavior, edge case failures
- **Low**: Minor deviations, no security impact

## 🤝 Contributing

This project is designed for collaboration between humans and AI assistants. Contributions welcome!

### For Human Developers
```bash
# Fork the repository
# Create a feature branch
git checkout -b feature/your-feature

# Make your changes and commit
git commit -m "Add: your feature description"

# Push and create a pull request
git push origin feature/your-feature
```

### For AI Assistants (LLMs)
This codebase uses:
- **tRPC** for type-safe API calls (see `server/routers.ts`)
- **Drizzle ORM** for database operations (see `drizzle/schema.ts`)
- **React Query** via tRPC hooks for data fetching

Key files to understand:
- `/todo.md` - Current feature roadmap
- `/server/routers.ts` - API endpoints
- `/drizzle/schema.ts` - Database schema
- `/client/src/pages/` - UI components

## 📝 Roadmap

See [todo.md](./todo.md) for current development status.

- [x] Research and attack library compilation
- [x] Project initialization
- [ ] Automated red-teaming engine
- [ ] Custom scenario builder
- [ ] Reporting system
- [ ] Multi-target support (OpenAI, Anthropic, local models)
- [ ] CI/CD integration for automated testing
- [ ] Browser extension for live testing

## 📚 Resources

- [OWASP LLM Security](https://genai.owasp.org/)
- [Promptfoo Security Database](https://www.promptfoo.dev/lm-security-db/)
- [Research Findings](./research_findings.md)

## ⚖️ License

Apache-2.0 License - See LICENSE file for details

## ⚠️ Disclaimer

This tool is intended for security testing of your own applications or applications you have permission to test. Unauthorized testing of third-party systems may be illegal. Use responsibly and ethically.

## 🙏 Acknowledgments

Built with research from the AI security community, including OWASP, academic researchers, and open-source contributors.

---

**Status**: 🚧 Active Development

**Maintainer**: [@Sconiboy](https://github.com/Sconiboy)

**Issues & Support**: [GitHub Issues](https://github.com/Sconiboy/llm-security-tester/issues)
