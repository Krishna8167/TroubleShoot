#  Dependencies for `.env` Troubleshooting Guide

This document outlines the key dependencies, tools, and environments referenced in the `.env` troubleshooting guide. It helps developers understand the context and install relevant packages when applying the guide.

---

##  Node.js Dependencies

These packages help load and manage `.env` files in Node.js projects:

| Package         | Purpose                                      | Install Command                      |
|----------------|----------------------------------------------|--------------------------------------|
| `dotenv`        | Loads `.env` into `process.env`              | `npm install dotenv`                 |
| `dotenv-expand` | Supports variable expansion like `${VAR}`    | `npm install dotenv-expand`          |
| `cross-env`     | Cross-platform environment variable support  | `npm install cross-env`              |
| `env-cmd`       | CLI tool to run scripts with `.env` loaded   | `npm install env-cmd`                |

---

##  Python Dependencies

Use these to load `.env` files into Python applications:

| Package           | Purpose                                  | Install Command                      |
|------------------|------------------------------------------|--------------------------------------|
| `python-dotenv`   | Loads `.env` into `os.environ`           | `pip install python-dotenv`          |

---

##  Docker Integration

Docker supports `.env` files natively:

- Use `--env-file .env` with `docker run`
- Use `env_file: .env` in `docker-compose.yml`
- Ensure `.env` uses LF line endings (`\n`)

---

##  Kubernetes Integration

Use `.env` values via:

- **ConfigMaps**: for non-sensitive config
- **Secrets**: for sensitive values
- Mount using `envFrom` or `valueFrom` in Pod specs

---

##  CI/CD Pipelines

Environment variables in CI/CD tools:

- **GitHub Actions**: `env:` block or GitHub Secrets
- **GitLab CI**: `variables:` block or CI/CD Settings
- **Bitbucket Pipelines**: `definitions` → `env`

Use `.env` locally; use pipeline secrets in production.

---

##  React / Next.js Requirements

| Framework | Prefix Required     | Notes                              |
|-----------|---------------------|------------------------------------|
| React     | `REACT_APP_`        | Rebuild required after changes     |
| Next.js   | `NEXT_PUBLIC_`      | Only these are exposed to frontend |

---

##  Development Tools

Helpful utilities for managing `.env` files:

| Tool            | Purpose                                      |
|-----------------|----------------------------------------------|
| `dotenv-cli`     | Run scripts with `.env` loaded               |
| `dotenv-linter`  | Lint `.env` files for syntax issues          |
| `dos2unix`       | Convert CRLF to LF line endings              |
| `iconv`          | Fix encoding issues                          |
| VS Code Plugin   | Auto-load `.env` files in development        |

---

## 📦 Optional Enhancements

- `.env.example`: Share variable names without values
- `.env.local`: Override values for local dev
- `.env.development`, `.env.production`: Environment-specific configs

---

## 🔐 Security Best Practices

- Add `.env` to `.gitignore`
- Never log full `process.env`
- Rotate secrets regularly
- Use secrets manager in production

---

## 📚 References

- [dotenv GitHub](https://github.com/motdotla/dotenv)
- [12 Factor App: Config](https://12factor.net/config)
- [Docker Docs: env-file](https://docs.docker.com/compose/env-file/)
- [GitHub Actions: Environment Variables](https://docs.github.com/en/actions/learn-github-actions/environment-variables)
- [Next.js Environment Variables](https://nextjs.org/docs/basic-features/environment-variables)








#  Environment Variable Troubleshooting Guide

This guide covers 30+ common issues and solutions when working with environment variables in `.env` files across Node.js, Python, Docker, CI/CD, and more.

##  1. `.env` File Not Found
- File must be named `.env`, not `.env.txt`
- Place in project root
- Use `dotenv` or equivalent loader

##  2. Variables Not Loaded
- Use `require('dotenv').config()` in Node.js
- Use `load_dotenv()` in Python
- Restart app after changes

##  3. Incorrect Syntax
- Format: `KEY=value`
- No spaces around `=`
- Avoid quotes unless needed

##  4. Debugging Values
- Print with `console.log(process.env.MY_VAR)`
- Shell: `env | grep MY_VAR`

##  5. Secrets in Git
- Add `.env` to `.gitignore`
- Use `.env.example` for sharing keys

##  6. Missing Newline
- Ensure final line ends with newline

##  7. Conflicting System Variables
- OS variables override `.env`
- Use fallback logic in code

##  8. Encoding Issues
- Save as UTF-8 without BOM

##  9. Variable Expansion Not Supported
- Use `dotenv-expand` for nested variables

##  10. Boolean Values Misinterpreted
- Use strings: `DEBUG=true`

##  11. Numeric Values Misparsed
- Wrap in quotes if needed

##  12. Comments Misplaced
- Only use `#` at line start

##  13. Duplicate Keys
- Last key wins — avoid duplicates

##  14. Docker `.env` Issues
- Use `--env-file` flag
- Ensure LF line endings

##  15. CI/CD Pipeline Failures
- `.env` may be excluded from build
- Use secrets manager or pipeline vars

##  16. React Requires Prefix
- Use `REACT_APP_` prefix
- Rebuild after changes

##  17. Next.js Requires `NEXT_PUBLIC_`
- Only `NEXT_PUBLIC_` vars exposed to frontend

##  18. Kubernetes ConfigMaps
- Mount `.env` as ConfigMap or Secret

##  19. Bash Exporting
- Use `export VAR=value`
- Source with `source .env`

##  20. Windows vs Unix Line Endings
- Use LF (`\n`) not CRLF (`\r\n`)
- Convert with `dos2unix`

##  21. File Permissions
- Use `chmod 600 .env` for sensitive files

##  22. Multiple `.env` Files
- Use `.env.development`, `.env.production`
- Load based on `NODE_ENV`

##  23. Variable Not Defined
- Check spelling and casing
- Use fallback defaults

##  24. Logging Secrets by Mistake
- Avoid logging `process.env` directly

##  25. IDE or GUI Not Loading `.env`
- Restart IDE
- Check plugin settings

##  26. Testing Frameworks Ignore `.env`
- Load manually in test setup

##  27. YAML or JSON Config Conflicts
- Avoid mixing formats

##  28. CI/CD Variable Precedence
- Pipeline vars override `.env`

##  29. Misleading Error Messages
- Validate with `dotenv-cli` or `env-cmd`

##  30. Debugging Tools
- Use `dotenv-cli`, `cross-env`

## 📚 References
- [dotenv GitHub](https://github.com/motdotla/dotenv)
- [12 Factor App](https://12factor.net/config)
- [Docker Docs: env-file](https://docs.docker.com/compose/env-file/)
