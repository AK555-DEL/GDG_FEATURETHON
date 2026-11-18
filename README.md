# GDG Featurethon

Welcome! In this 4–5 hour Featurethon, choose one project and build a focused feature. Each project stays in its original GitHub repository; this central repository provides the links and quick-start guides.

## Choose a project

| Project | Required Node.js | Package manager | Additional requirements | Setup difficulty / readiness |
| --- | --- | --- | --- | --- |
| [Simple React Ecommerce](https://github.com/alim1496/simple-react-ecommerce) · [Guide](./simple-react-ecommerce/README.md)<br>Frontend shop demo with cart and wishlist. | 18+; not 19 (use 20+ LTS) | npm | Internet for product data | Low · **NOT READY:** clean install not confirmed |
| [Tripix](https://github.com/MiladJoodi/Tripix) · [Guide](./Tripix/README.md)<br>Travel search and sample booking demo. | 20.9+ | npm | None | Low · **READY WITH WARNINGS:** lint script fails |
| [PancakeMaker](https://github.com/momentmaker/pancakemaker) · [Guide](./pancakemaker/README.md)<br>Offline-first expense tracker. | 20+ | npm 10.9.0 | Cloudflare and Resend only for optional sync | Low · **READY WITH WARNINGS:** lockfile version mismatch |

## Before you start

- [Git](https://git-scm.com/install/) and a project-compatible [Node.js LTS installer](https://nodejs.org/en/download) are required. npm comes with Node.js.
- [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional; any editor and modern browser work.
- Use PowerShell. The documented local workflows do not require Docker or WSL.
- Follow each guide's package-manager version and install command. Do not delete or regenerate lockfiles.

## Participant workflow

1. Choose one project and check its readiness note before installing.
2. Fork that project's original repository on GitHub, then clone your fork using its guide.
3. Create a feature branch: `git switch -c feat/short-feature-name`.
4. Make a focused change, run the checks in the guide, then commit and push to your fork.
5. Follow the submission method announced by organizers. No submission URL or judging rules are defined here. Open an upstream pull request only if the maintainers allow it.

Never commit `.env` files, API keys, passwords, or other secrets. If setup fails, share the project, operating system, command, and first useful error with organizers; redact credentials.
