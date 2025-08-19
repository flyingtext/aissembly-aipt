# Aipt

**Aipt** is the package manager for the [aissembly](https://github.com/flyingtext/aissembly) project.  
It does not rely on a central package registry server. Instead, it uses a **GitHub index repository** to maintain the list of registered packages.  
Package sources are fetched directly from their GitHub repositories (via archive download or shallow clone).  

To ensure reproducibility, `aipt.lock` pins exact commit SHAs and hashes of critical artifacts (such as grammar and prompt files).

---

## ✨ Features
- **Serverless architecture**  
  Registered packages are tracked in a GitHub index repository.  
  Sources are fetched directly from GitHub repos.

- **Reproducible builds**  
  `aipt.lock` records commit SHAs and hashes of grammar/EBNF and prompt files.  
  The same build can always be reproduced.

- **Familiar workflow**  
  Simple CLI commands (`add`, `install`, `update`, `build`, `test`, `publish`).  
  Package/version registration is done via Pull Request to the index repository.

- **LLM-aware design**  
  JIT execution profiles (model, prompts, EBNF, sampling parameters) are first-class citizens in the manifest.  
  Regression testing with golden prompts is supported.

---

## 📦 Project Structure
```

project/
Ais.toml        # Package manifest
aipt.lock       # Lockfile (commit SHA pinned)
/src
/rules
/assets
/dist

````

---

## 📑 Manifest Example (`Ais.toml`)
```toml
[package]
name = "spacetime-core"
version = "0.3.0"
description = "Spacetime wiki core rules/runner for aissembly"
license = "Apache-2.0"
repository = "https://github.com/flyingtext/aissembly"
authors = ["JiHyeon Yoon <flyingtext@nate.com>, <somehowme@gmail.com>"]

[dependencies]
aissembly-std = "^1.2.0"
grammar-kit = "~0.4.5"

[llm.profile.default]
model = "gpt-5-coder"
version = "5.1.2"
endpoint = "https://api.example.com/v1"
max_tokens = 8192
temperature = 0.2
seed = 42
parser_spec = "rules/ais.ebnf"
system_prompt_file = "rules/system.md"
user_prompt_file   = "rules/user.md"
````

---

## 🚀 Basic Workflow

```bash
# Initialize a new project
aipt init

# Add dependencies (from index repo)
aipt add spacetime-core@^0.3

# Install dependencies (generate or respect aipt.lock)
aipt install

# Build & test
aipt build --profile default
aipt test

# Publish a new version
git tag v0.3.1
git push origin v0.3.1
aipt publish --tag v0.3.1
aipt index pr --package spacetime-core --tag v0.3.1
```

---

## 🔒 Security

* **Commit pinning**: Every dependency is tied to a specific commit SHA.
* **Archive hash**: `aipt.lock` stores tarball checksums for integrity verification.
* **Optional signature verification**: Signed Git tags/releases are recommended.
* **SBOM generation**: SPDX/CycloneDX reports for supply chain transparency.

---

## 👤 Maintainer

* **JiHyeon Yoon**

  * Email: [flyingtext@nate.com](mailto:flyingtext@nate.com), [somehowme@gmail.com](mailto:somehowme@gmail.com)

---

## 📄 License

MIT License. See [LICENSE](./LICENSE) for details.
