# Contributing to Evance Chapuma's Automation Portfolio

Thank you for your interest in contributing! This repository showcases real-world AI automation workflows. Contributions that improve documentation, fix errors, or add workflow examples are very welcome.

## How to Contribute

### Reporting Issues
Use the [bug report template](.github/ISSUE_TEMPLATE/bug_report.md) to flag:
- Broken documentation or dead links
- Incorrect setup instructions
- Outdated dependencies or API references

### Submitting Changes

1. **Fork** this repository
2. **Create a branch** with a descriptive name:
   ```bash
   git checkout -b docs/fix-vapi-setup-instructions
   git checkout -b feat/add-make-workflow-example
   ```
3. **Make your changes** — keep them focused and minimal
4. **Commit** using [Conventional Commits](https://www.conventionalcommits.org/) format:
   ```
   docs: fix broken Twilio webhook URL in project 02
   feat: add Make.com variant for Google Review Responder
   fix: correct env variable name in .env.example
   chore: update shields.io badge URLs
   ```
5. **Open a Pull Request** against `main` with a clear description of what changed and why

## Code / Workflow Standards

- **No real credentials** — all env vars must use placeholder values (e.g. `YOUR_TWILIO_ACCOUNT_SID`)
- **Mermaid diagrams** — architecture diagrams should be in Mermaid format for native GitHub rendering
- **README sections** — project READMEs should follow the template in `templates/workflow-readme-template.md`
- **Workflow JSON files** — if adding n8n/Make exports, sanitize all credentials before committing

## Questions?

Open an issue or reach out via [Upwork](https://www.upwork.com/freelancers/evancechapuma).
