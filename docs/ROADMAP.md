# Aipt Roadmap

This document outlines the development roadmap for **aipt**, the package manager for the [aissembly](https://github.com/flyingtext/aissembly) project.

---

## 🎯 Goals
- **Reproducibility**: Lock dependencies by commit SHA and prompt/grammar hashes.
- **Serverless**: No dedicated registry server. Use GitHub index repository to track packages.
- **LLM-aware**: Treat prompts, grammar (EBNF), and model profiles as first-class citizens.
- **Developer experience**: Familiar commands, clear error reporting, transparent workflows.
- **Security**: Integrity checks, signature support, SBOM generation.

---

## 🚀 MVP (0.1.x)

**Target: Minimal usable package manager**

- [ ] Basic manifest (`Ais.toml`) and lockfile (`aipt.lock`) schema.
- [ ] Core commands:  
  - `aipt init`  
  - `aipt add/remove`  
  - `aipt install`  
  - `aipt build`  
  - `aipt test`
- [ ] Fetch sources directly from GitHub by tag → commit → archive.  
- [ ] Pin commit SHA and archive hash in `aipt.lock`.  
- [ ] LLM profile snapshot (model ID, parser hash, prompt hash, seed).  
- [ ] Simple index repo format (JSON/TOML) and local cache.  
- [ ] Publish workflow: tag → index PR.  
- [ ] Integrity verification (commit SHA, archive hash).  

---

## 🌟 v1.0

**Target: Stable and feature-complete package manager**

- [ ] Workspaces/monorepo support (`Ais.workspace.toml`).  
- [ ] Advanced dependency resolver (partial upgrades, conflict reporting).  
- [ ] Index repo mirrors and fallback configuration.  
- [ ] Signature verification (sigstore/gitsign).  
- [ ] SBOM generation (SPDX / CycloneDX).  
- [ ] Policy engine for supply chain trust levels (internal/external/verified).  
- [ ] Graph visualization (`aipt graph`).  
- [ ] Diagnostic commands (`aipt doctor`, `aipt explain`).  
- [ ] Template support (`aipt init --template ...`).  
- [ ] Plugin system with hooks (pre/post build, publish, etc.).  
- [ ] Enhanced testing (golden prompts, regression suites).  

---

## 📅 Future Ideas
- [ ] Editor/IDE integration (manifest intellisense, dependency graph preview).  
- [ ] CI/CD caching and reproducible pipelines.  
- [ ] Spacetime wiki integration (deploy workflows, analytics plugins).  
- [ ] Built-in golden prompt regression testing framework.  

---

## 👤 Maintainer
- **JiHyeon Yoon**  
  - Email: <flyingtext@nate.com>, <somehowme@gmail.com>
