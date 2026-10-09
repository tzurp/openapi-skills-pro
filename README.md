
# openapi-skills Pro
**OpenAPI & GraphQL CLI** — Explore APIs, generate artifacts, validate schemas, compare API versions, and enable AI agent workflows.

openapi-skills-pro is a cross-platform CLI for OpenAPI and GraphQL workflows. It supports schema exploration, local mock servers, interactive HTML API documentation, schema comparison, code-first OpenAPI generation, validation, and AI agent automation.

[![GitHub stars](https://img.shields.io/github/stars/tzurp/openapi-skills-pro?style=flat)](https://github.com/tzurp/openapi-skills-pro/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/tzurp/openapi-skills-pro?style=flat)](https://github.com/tzurp/openapi-skills-pro/issues)
![Platforms: Windows, macOS, Linux](https://img.shields.io/badge/platforms-Windows%20%7C%20macOS%20%7C%20Linux-blue)

<p align="center">
<img src="https://raw.githubusercontent.com/tzurp/images/refs/heads/main/openapi-skills-pro-stripe.jpg">
</p>

### Work with OpenAPI and GraphQL from your terminal, or let AI agents use the built-in Skills bundle to explore APIs, prepare requests, validate schemas, and generate code and tests. openapi-skills Pro brings the v2 toolkit together in a commercial, self-contained CLI for Windows, macOS, and Linux.

## Quick Links

- [Install openapi-skills Pro](#install-openapi-skills-pro)
- [Quick start](#quick-start)
- [Run a local mock server](#run-a-local-mock-server)
- [Compare API schemas](#5-compare-two-versions-of-the-same-api-schema)
- [Generate HTML API docs](#generate-api-docs)
- [AI agent integration](#ai-agent-integration)

## What openapi-skills Pro adds

The core free CLI provides the foundational API exploration workflow. openapi-skills Pro builds on that foundation with the following v2 capabilities:

- OpenAPI 2.0, 3.0, and 3.1 support with an extensible parser architecture designed to accommodate future specification versions.
- Mock server: Spin up realistic mock APIs directly from your OpenAPI schema for rapid prototyping and testing.
- HTML schema export: Generate a beautiful, interactive HTML documentation view of your API schema that you can share or host.
- Schema version comparison: Compare two versions of the same API schema operation by operation, see exactly what changed, and detect breaking changes with precision.
- Code-first OpenAPI bootstrap: Create OpenAPI annotations from API handlers across languages and frameworks and generate a usable OpenAPI document directly with the CLI.
- Performance and UX improvements: Faster commands, clearer errors, and smoother workflows across the CLI.

With Skills enabled, AI agents such as Copilot, Claude, and Cursor can explore your API, prepare and execute live requests, validate schemas, and generate client code, tests, and workflows from natural-language instructions.

## Get openapi-skills Pro

**Purchase:** [https://openapi-skills.lemonsqueezy.com](https://openapi-skills.lemonsqueezy.com)

**Installer download:** [https://app.lemonsqueezy.com/my-orders](https://app.lemonsqueezy.com/my-orders)

openapi-skills Pro is distributed as a self-contained installer. The installer attempts a system installation, and falls back to a per-user install if elevation is declined or unavailable. The installer prompts for your license key. The license file stays in your user profile.

These platforms are supported: Windows x64, macOS x64, macOS arm64 and Linux x64. 

> **Code-first bootstrap tip:** If your project is still code-first and doesn’t yet have an OpenAPI schema, install the optional `openapi-skills-annotator` skill to annotate source code, then run `openapi-skills generate-openapi` to write the OpenAPI document.


## Overview — OpenAPI & GraphQL CLI

openapi-skills Pro is a command-line toolkit for exploring OpenAPI and GraphQL schemas, preparing and executing API requests, validating schemas and responses, generating API artifacts and documentation, and comparing API versions.

## Why openapi-skills Pro

Working with API schemas can be slow and error‑prone. `openapi-skills` provides:

- A consistent way to explore any API  
- Automatic artifact generation  
- Request templates you can execute immediately  
- Built‑in validation tools  
- Optional AI integration for natural-language workflows  

## Manual CLI + AI Skills

openapi-skills Pro works as a traditional CLI. Explore endpoints, inspect schemas, prepare requests, and execute live API calls directly from the terminal.

Enable the optional Skill bundle, and AI agents (Copilot, Claude, Cursor, etc.) can operate the CLI for you: exploring operations, preparing and executing requests, validating schemas, and even generating client code, tests, and multi-step workflows from natural language.

## AI Agent Integration

The built-in Skill bundle enables AI agents such as GitHub Copilot, Claude, and Cursor to use the openapi-skills CLI through natural-language instructions. Agents can:

- Explore OpenAPI and GraphQL schemas and find operations
- Prepare and execute live API requests
- Validate schemas and API responses
- Generate client code and tests
- Build multi-step API workflows
- Start a local mock server and send requests to it

## Features

- Explore operations by method, path, tag, or keyword  
- Describe endpoints with full request/response details  
- Compare two versions of the same API schema or selected operations with automatic artifact extraction
- Prepare and execute live API requests (Postman‑like, no code needed)  
- Parse OpenAPI 2.0, 3.0, and 3.1 schemas, plus GraphQL schemas  
- Generate artifacts (`endpoints.json`, `schemas/`)
- Work with multiple API schemas simultaneously (stored under: .openapi-skills/<apiName>/ directory)
- Validate schemas and API responses  
- Build multi-step scenarios  
- Run a local mock server from generated artifacts; use it through the CLI or any HTTP client  
- AI Skills bundle for agent-driven workflows (code, tests, clients, docs)

## Workflow

**parse → index → understand → execute → validate → generate code/tests (via agent)**

## Quick start

### Install openapi-skills Pro

Download the installer for your operating system from [https://app.lemonsqueezy.com/my-orders](https://app.lemonsqueezy.com/my-orders), run it, and enter your license key when prompted. The installer configures the `openapi-skills` command and PATH.

### Install the Skill

If your project has no OpenAPI schema yet, install the optional annotator skill with `--skills-annotator`:

```bash
openapi-skills install --skills
openapi-skills install --skills-annotator
openapi-skills install --skills --skills-annotator
```
Select your preferred path from  the menu and confirm

### Generate OpenAPI from annotations

```bash
openapi-skills generate-openapi --apis "src/routes/**/*.ts" --apis "docs/api/annotations/**/*.js" --out docs/api/generated/openapi.json --openapi-version 3.1.0
```

`--apis` is repeatable and required. `--out` and `--openapi-version` are required. The output extension determines the format: use `.json` for JSON or `.yaml`/`.yml` for YAML. Relative source patterns and output paths resolve from the current working directory unless `--project-root` is provided. The title defaults to `OpenAPI`, and the API version defaults to `1.0.0` (`--api-version` overrides it). This command writes only the OpenAPI document; it does not create `.openapi-skills` artifacts.

To generate YAML, change the output extension:

```bash
openapi-skills generate-openapi --apis "src/routes/**/*.ts" --out docs/api/generated/openapi.yaml --openapi-version 3.1.0
```

### Generate artifacts from a schema

```bash
openapi-skills generate https://petstore.swagger.io/v2/swagger.json --base-url=https://petstore.swagger.io/v2
```

This creates:

```
.openapi-skills/
  petstore/
    endpoints.json
    schemas/
```

### Explore the API manually

```bash
openapi-skills list --api petstore --method POST --index 0:10
openapi-skills list --api petstore --method GET --path /pet --tag pet
openapi-skills describe addPet --api petstore
openapi-skills compare --surface --api petstore --api petstore-v2
openapi-skills compare --api petstore --api petstore-v2
openapi-skills compare --api petstore addPet --api petstore-v2 addPetV2
openapi-skills compare --api petstore --api petstore-v2 --op addPet
```

### Prepare and execute a request manually

```bash
openapi-skills request addPet --api petstore --force --update-request '{"body.id":1,"body.name":"Fluffy"}'
```

### Run a local mock server

```bash
openapi-skills mock-server --api petstore
```

The mock server serves routes from generated artifacts for the selected API and persists the running URL in `.openapi-skills/config.json` as `apis.<apiName>.mockUrl`. Once started, you can use it in either of two ways:

1. **Use any HTTP client:** Send requests directly to the reported mock server URL as if it were your API's base URL. This works with `fetch`, Axios, curl, Postman, Insomnia, or your own app.
2. **Use the CLI:** Add `--mock` to an `openapi-skills request` command to send that CLI request to the local mock server instead of the configured live `baseUrl`:

```bash
openapi-skills request addPet --api petstore --mock
```

The mock server also exposes a reserved `GET /mock-health` endpoint that returns a small JSON status payload:

```json
{ "ok": true, "apiName": "petstore", "status": "running" }
```

If a saved `response.json` exists, the mock server replays it. If it is missing, the server generates a deterministic JSON fallback from the available schema artifacts.

### Generate API docs

```bash
openapi-skills docs main-schema/openapi.json
openapi-skills docs main-schema/openapi.json --out docs/
openapi-skills docs main-schema/openapi.json --rename petstore --dark --open
openapi-skills docs https://example.com/openapi.json --out docs/
```

The `docs` command accepts an absolute path, a path relative to the project root, or an HTTP(S) URL to an OpenAPI 2/3 schema. It copies or downloads the schema into the output directory, generates an `index.html`, and starts a local HTTP server by default so Redoc can render reliably. The default output directory is `.openapi-skills/<schemaName>/out`, and `--rename` changes the schema name used in that default path.

Use `--dark` for the dark theme, `--open` to launch the browser, and `--no-serve` if you only want the generated files.

---

## ⚡ One‑line agent command

Once the Skills bundle is installed, the entire Quick start can be replaced with a single natural-language instruction:

```
In Agent mode write: /openapi-skill make live request to addPet with name "Fluffy" using the schema https://petstore.swagger.io/v2/swagger.json and base url https://petstore.swagger.io/v2
```

The agent will:

- Parse the schema  
- Generate artifacts  
- Index endpoints  
- Prepare the request  
- Set `"name": "Fluffy"`  
- Execute it live  
- Show the response  

All from **one sentence**.

### Example questions you can ask the Skill if you feel stuck

You can always ask the skill question to progress in your work. For example:
 - `/openapi-skills what can you do?`
 - `/openapi-skills how do I add an auth token to a live request?`

#### Examples for the `openapi-skills-annotator` skill (`--skills-annotator`)

Use this skill when route code is the source of truth and the project does not yet have a usable OpenAPI schema.

| Natural language request | What the skill does |
|--------------------------|---------------------|
| “My API is defined in route code, but I don't have an OpenAPI file. Document the routes using OpenAPI 3.1.” | Creates API documentation from the routes and asks about details it cannot determine. |
| “I changed my routes. Update the OpenAPI file and check that it's valid.” | Updates the route annotations, generates the schema, and validates it. |
| “Update the API docs to match the latest routes, and summarize what changed.” | Refreshes the generated API reference files and reports route changes. |
| “Look for request or response formats that repeat. Share them where it makes the schema clearer.” | Reuses common formats when the code clearly supports it, without changing the API behavior. |
| “Create a browsable HTML reference from my finished OpenAPI file.” | Passes the completed schema to `openapi-skills` to generate API documentation. |

---

## 5‑minute tutorial

### 1. Install openapi-skills Pro

Download the platform installer from [your orders](https://app.lemonsqueezy.com/my-orders). The installer requests elevation for a system-wide installation and continues with a per-user installation if elevation is declined. Enter your license key when prompted.

### Install the Skill

If your project has no OpenAPI schema yet, prefer the openapi-skills-annotator skill with `--skills-annotator`:

```bash
# Local install (default)
openapi-skills install --skills
```
```bash
# Global install (user home)
openapi-skills install --skills --global
```
```bash
# openapi-skills-annotator skill bundle
openapi-skills install --skills-annotator
openapi-skills install --skills-annotator --global
```

During installation, the CLI shows a small menu where you choose the Skill’s location:

- `.cursor/skills/`
- `.agent/skills/`
- `.claude/skills/`
- `.github/skills/`
- `other` (custom path)

Select your preferred path and confirm — that’s it.

> **💡 Note:**
>
> Installing the skill bundle allows AI agents to understand your API structure and execute CLI commands automatically.  
> See the section on [AI agent capabilities](#ai-agent-capabilities-some-examples).


### 2. Parse a public API and set its base URL

```bash
openapi-skills generate https://petstore.swagger.io/v2/swagger.json --base-url=https://petstore.swagger.io/v2 --rename petstore-v2
```

### 3. Explore operations

```bash
openapi-skills list --api petstore --method POST --index 0
openapi-skills describe addPet --api petstore
openapi-skills compare --surface --api petstore --api petstore-v2
```

### 4. Build and execute a request

```bash
openapi-skills request addPet --api petstore --force --update-request '{"body.id":1,"body.name":"Fluffy"}'
```

### 5. Compare two versions of the same API schema

```bash
openapi-skills compare --api petstore --api petstore-v2
openapi-skills compare --surface --api petstore --api petstore-v2
openapi-skills compare --api petstore addPet --api petstore-v2 addPetV2
openapi-skills compare --surface --json --api petstore --api petstore-v2
openapi-skills compare --api petstore --api petstore-v2 --json > comparison.json
```

The two `--api` values should identify two versions of the same API schema, for example `petstore-v1` and `petstore-v2`. Compare automatically extracts missing `endpoints.json` and operation schema artifacts before diffing, so you do not need to run `describe` or `request` first.
With only two `--api` flags, compare first reports the operation-surface diff and then compares schemas for every operation ID common to both versions. The structured JSON result is written to stdout; `--json` suppresses the colored human summary on stderr, and shell redirection can save the JSON to a file. In an interactive terminal, compare highlights conservative breaking-change findings.

### 6. Validate the schema

```bash
openapi-skills generate https://petstore.swagger.io/v2/swagger.json --validate
```

## Examples of what AI agents can do when the Skill is enabled

| Natural language request | CLI/Skill executed |
|--------------------------|--------------------|
| “Make a live request to addPet with name Fluffy.” | Postman‑like API call via `request --update-request` |
| “Show me the first POST operation.” | Explore endpoints via `list` |
| “Describe the addPet operation.” | Operation breakdown via `describe` |
| “Validate this API schema.” | Schema validation via `generate --validate` |
| “Generate a Jest test for addPet.” | Agent writes full Jest test using CLI metadata |
| “Create a Playwright API test for addPet.” | Agent generates Playwright test using endpoint + schema |
| “Build a TypeScript API client for this API.” | Agent generates typed client functions + models |
| “Create a 3-step scenario: add, fetch, delete pet.” | Multi-step workflow via `request` |
| “Start a local mock server for petstore and send requests to it.” | `mock-server`, then either use an HTTP client with the reported URL or use `request --mock` |

Agents combine CLI output with code generation to produce:
- typed API clients  
- integration & contract tests  
- Playwright API tests  
- mocks & fixtures  
- multi-step workflows  
- documentation  

Additional compare examples:

- “Compare addPet between v1 and v2.” -> `compare --api ... --api ... --op addPet`
- “Show API surface changes between two specs.” -> `compare --surface`

## 🎥 Video demo

A short video clip demonstrating the CLI in action is available here:

[https://github.com/tzurp/openapi-skills-cli/releases#release-video](https://github.com/tzurp/openapi-skills-cli/releases#release-video)

## Support

If you run into issues or have questions:

- Report bugs or request features via GitHub Issues: [https://github.com/tzurp/openapi-skills-pro/issues](https://github.com/tzurp/openapi-skills-pro/issues)
- General questions can be sent directly to: [bedekbyte@outlook.com](mailto:bedekbyte@outlook.com)
- Check CLI help for up-to-date usage:
  ```bash
  openapi-skills --help
  openapi-skills <command> --help
  ```

> **✨TIP**
>
> When opening an issue or sending an email, include the CLI version, the command you ran, and any relevant logs or schema snippets.

## Links

- GitHub repository: [https://github.com/tzurp/openapi-skills-pro](https://github.com/tzurp/openapi-skills-pro)
- Free OpenAPI and GraphQL CLI: [openapi-skills-cli](https://github.com/tzurp/openapi-skills-cli)
- Code-first OpenAPI annotation skill: [openapi-skills-annotator](./skill-templates/openapi-skills-annotator/)
- Publisher website: [Bedekbyte](https://bedekbyte.com)

## Keywords

OpenAPI CLI, GraphQL CLI, API explorer, schema validation, schema diff, API version comparison, mock server, HTML API documentation, code-first OpenAPI, API testing, AI agent skills
```
