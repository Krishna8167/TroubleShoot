# Environment Troubleshooting Dependencies

This document lists the tools, libraries, and packages referenced in the **.env troubleshooting guide**.  
It serves as a quick reference for setup, debugging, and dependency management.

---

## 🛠️ Core Tools

- **Bash / Zsh / PowerShell**  
  Required for running shell commands and scripts that load `.env` variables.

- **GNU Coreutils**  
  Provides essential commands like `cat`, `echo`, `grep`, and `export`.

- **Make**  
  Useful for automating environment setup and teardown tasks.

---

## 📦 Language Runtimes & Package Managers

- **Python 3.x**  
  - `python-dotenv` → Loads `.env` files into `os.environ`.  
  - `pip` → Installs Python dependencies.

- **Node.js (LTS)**  
  - `dotenv` (npm package) → Loads `.env` variables into `process.env`.  
  - `npm` / `yarn` / `pnpm` → Dependency managers.

- **Go**  
  - `godotenv` → Parses `.env` files into Go applications.

---

## 🗄️ Databases & Services

- **PostgreSQL Client Tools** (`psql`)  
  For testing DB connection strings defined in `.env`.

- **MySQL / MariaDB Client**  
  For verifying `.env` credentials and connectivity.

- **Redis CLI**  
  For checking cache connection variables.

---

## 🐳 Containerization & Orchestration

- **Docker**  
  - Uses `.env` files in `docker-compose.yml` for service configuration.  
  - `docker compose config` helps validate variable substitution.

- **Kubernetes (kubectl, Helm)**  
  - `.env` values often injected into ConfigMaps or Secrets.

---

## 🔍 Debugging & Validation Tools

- **direnv**  
  Automatically loads/unloads `.envrc` files per directory.

- **dotenv-linter**  
  Validates `.env` files for formatting issues.

- **jq**  
  Parses JSON configs when `.env` values are exported to JSON.

- **envsubst**  
  Substitutes environment variables in configuration templates.

---

## ✅ Recommended Practices

- Always keep a `.env.example` file listing required variables.  
- Use `.gitignore` to prevent committing sensitive `.env` files.  
- Validate variables with linters before deployment.  
- Prefer secrets managers (Vault, AWS Secrets Manager, etc.) for production.

---

_Last updated: November 2025_
