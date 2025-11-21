## What is this PR about?

<!-- Describe what this PR adds or changes -->
- [ ] New service/template
- [ ] Update to existing service
- [ ] Bug fix
- [ ] Documentation update
- [ ] Other (please describe)

**Service Name:** [e.g., nginx, redis, postgres]

**Structure Type:**
- [ ] Flat file (`compose-files/service-name.yml`)
- [ ] Folder structure (`compose-files/services/service-name/`)

## Checklist

Before submitting this PR, please make sure that:

### General Requirements
- [ ] I have read the [README.md](https://github.com/hhftechnology/Marketplace/blob/main/README.md) and followed the submission guidelines
- [ ] I have tested the template/service in my instance
- [ ] The Docker image(s) are publicly accessible (no private registries)
- [ ] I have used `${VARIABLE_NAME}` syntax for configurable values
- [ ] I have used descriptive volume placeholders (e.g., `/WORK_DIR` instead of absolute paths)
- [ ] Timezone is set to `Etc/UTC` (if applicable)

### Docker Compose File
- [ ] Includes inline comments (ScaleTail style) for clarity
- [ ] Minimized unnecessary ports, environment variables, or configurations
- [ ] Uses `latest` tag where possible (or specific version if required)
- [ ] Multi-service support is properly configured (if applicable)

### Folder Structure (If Applicable)
- [ ] `docker-compose.yml` is included and properly formatted
- [ ] `template.toml` is included (if template variables/domain config needed)
- [ ] `.env.example` is included (if environment variables are needed)
- [ ] `README.md` is included (if detailed setup instructions are needed)

### Testing
- [ ] I have tested the service deployment
- [ ] I have verified all environment variables work correctly
- [ ] I have checked that volumes and ports are correctly configured
- [ ] I have verified the service starts and runs without errors

## Files Changed

<!-- List the files you've added or modified -->
- `compose-files/[service-name].yml` (flat file structure)
- OR
- `compose-files/services/[service-name]/docker-compose.yml`
- `compose-files/services/[service-name]/template.toml` (if applicable)
- `compose-files/services/[service-name]/.env.example` (if applicable)
- `compose-files/services/[service-name]/README.md` (if applicable)

## Additional Notes

<!-- Any additional context, screenshots, or information that would help reviewers -->

## Issues Related (if applicable)

Close automatically the related issues using the keywords: `closes #ISSUE_NUMBER`, `fixes #ISSUE_NUMBER`, `resolves #ISSUE_NUMBER`

Example: `closes #123`