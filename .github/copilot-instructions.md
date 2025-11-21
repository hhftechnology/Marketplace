# Marketplace Repository - Copilot Instructions

## Project Overview

This repository maintains Docker Compose templates for deploying open-source applications. The core structure revolves around the `compose-files/` directory, where each subdirectory represents a deployable service (e.g., `compose-files/nginx/` for Nginx web server).

Key components:

- **Compose Files**: Self-contained templates with `docker-compose.yml` (service definitions).
- **meta.json**: Centralized index of all templates. Entries include `id`, `name`, `version`, `description`, `logo`, `links`, and `tags`.
- **Scripts**: Node.js tools in root and `build-scripts/` for maintaining `meta.json` (deduplication, sorting, validation).

Data flow: New templates added to `compose-files/` → Metadata updated in `meta.json` → Processing scripts ensure consistency → Templates ready for deployment.

The "why": Enables rapid, standardized deployment of 300+ OSS apps without manual config. Structure prioritizes simplicity—each template is independent, no shared state or complex interdependencies.

## Key Files and Directories

- `meta.json`: Array of template objects. Always process after edits using `node dedupe-and-sort-meta.js` to remove duplicates (by `id`) and sort alphabetically.
- `compose-files/<service>/`:
  - `docker-compose.yml`: Standard Docker Compose v3.8. May include ports, volumes, and environment variables as needed.
  - `logo.svg/png`: Service icon, referenced in `meta.json`.
- `dedupe-and-sort-meta.js`: Standalone script—reads `meta.json`, removes duplicate `id`s (keeps first), sorts by `id` (case-insensitive), creates timestamped backup.
- `build-scripts/process-meta.js`: Advanced processor with CLI options (`--verbose`, `--no-backup`, `--input`/`--output`), JSON schema validation (required: `id`, `name`, `version`, `description`, `links.github`, `logo`, `tags` array).

Exemplary template: `compose-files/nginx/`—`docker-compose.yml` defines Nginx service; meta entry tags as ["proxy", "web-server"].

## Development Workflow

1. **Add/Update Template**:

   - Create `compose-files/<id>/` (e.g., `nginx`).
   - Implement `docker-compose.yml` (single or multiple services; use volumes for persistence).
   - Add/update `meta.json` entry with exact `id` matching folder.
   - Run `node dedupe-and-sort-meta.js --backup` to validate/sort.
   - Commit and push changes.

2. **Local Development**:

   - Meta processing: `node build-scripts/process-meta.js --verbose` or `node dedupe-and-sort-meta.js --backup`.
   - Test template: Use `docker-compose up` in the service directory to test locally.

3. **CI/CD**:
   - `.github/workflows/validate-meta.yml`: Runs validation on push/PR—fails on duplicates, invalid JSON, missing fields.
   - Integrate processing: Add `node build-scripts/process-meta.js` to build steps; use `--no-backup` in CI.

No tests in repo—focus on manual validation via scripts and Docker Compose testing. Debug: Check console output from processing scripts for warnings (e.g., missing `id`).

## Conventions and Patterns

- **Template IDs**: Lowercase, kebab-case (e.g., `active-pieces`); unique across repo—enforced by dedupe script.
- **Docker Compose**: Standard Docker Compose v3.8 format. Include `restart: unless-stopped`, persistent volumes (e.g., `- db-data:/var/lib/postgresql/data`). Services typically named after folder (e.g., `nginx` service).
- **Meta.json**: Entries as JSON objects; tags array of lowercase strings (e.g., ["monitoring", "database"]); links object with `github`, `website`, `docs`.
- **Versions**: Use `latest` tag or pin to specific versions in `docker-compose.yml` (e.g., `nginx:1.25-alpine`); match in `meta.json.version`.
- **Logos**: SVG preferred; size ~128x128; file name in `meta.json.logo` (e.g., "nginx.svg").

Cross-component: No runtime communication—templates independent. Each template can be deployed standalone using Docker Compose.

## Integration Points

- **Docker Compose**: Templates can be deployed directly using `docker-compose up`. Test deploys validate env interpolation and service configuration.
- **External Deps**: Docker Compose (v3.8+). No runtime deps beyond Node.js for meta processing scripts.

When editing, always re-run meta processing and validate template deployment.
