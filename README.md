# Marketplace Repository

A collection of Docker Compose files for self-hosted services, supporting both traditional flat file structure and the new folder-based structure with template support.

## Repository Structure

This repository supports a **hybrid approach** that maintains backward compatibility while enabling advanced features:

### Option 1: Folder Structure (Recommended - New Format)

```
compose-files/
└── services/
    ├── nginx/
    │   ├── docker-compose.yml  # Main compose file
    │   ├── .env.example      # Example env file (optional)
    │   └── README.md          # Service docs (optional)
    │
    └── redis/
        ├── docker-compose.yml
        └── .env.example
```

### File Formats

- **docker-compose.yml**: Standard Docker Compose file with comments (ScaleTail style)
- **.env.example**: ScaleTail-style environment file with comments showing required variables (optional)
- **README.md**: Service-specific documentation (optional)

## How to Contribute

The Marketplace is a community-driven project. We welcome contributions from everyone! To add a new self-hosted service or update an existing one, please open a GitHub [Issue](https://github.com/hhftechnology/Marketplace/issues) using the template below. This helps us review and integrate your submission efficiently.

## Submission Template

Use this structure in your issue description:

### Service Name

[Enter the name of the service, e.g., `nginx` or `redis`. Keep it concise and descriptive.]

### Structure Preference

[Choose one:]

- **Flat file**: Simple `service-name.yml` in `compose-files/`
- **Folder structure**: `compose-files/services/service-name/` with `docker-compose.yml` and optional files

### Example docker-compose.yml

```yaml
[
  Paste a complete,
  working `docker-compose.yml` configuration here. Use code block formatting for readability.,
]
```

### Optional Files (Folder Structure Only)

If using folder structure, you may include:

**.env.example** (if environment variables are needed):

```bash
# Service Configuration
SERVICE=nginx
IMAGE_URL=nginx:latest
SERVICEPORT=80

# Template Variables
MAIN_DOMAIN=example.com
```

**README.md** (service documentation):
[Service-specific setup instructions, features, and usage notes]

### Documentation or References

[Provide links to official documentation, Docker Hub pages, GitHub repositories, or other relevant resources.]

### Notes

[Any additional context, setup instructions, or caveats. If this is an update to an existing service, prefix with "Update: " and describe the changes.]

## Submission Guidelines

Before opening your issue, please verify that your submission meets these standards to streamline the review process:

### Docker Compose File Requirements

- **Comments allowed**: Inline comments are welcome and encouraged (ScaleTail style) for clarity
- **Minimize extras**: Eliminate unnecessary ports, environment variables, volumes, or other configurations
- **Public images only**: Ensure the Docker image(s) are publicly accessible (no private registries)
- **Environment variables**: Use `${VARIABLE_NAME}` syntax for configurable values
- **Prefer latest tags**: Use the `latest` image tag where possible, unless a specific version is required for stability
- **Multi-service support**: It's okay to include multiple related services in one compose file (e.g., a main app + dependencies), as long as they function together
- **Standardize volumes**: Replace absolute host paths with descriptive, uppercase placeholders (e.g., change `/data/adguard-home/work:/opt/adguardhome/work` to `/WORK_DIR:/opt/adguardhome/work`)
- **Set timezone**: Default to `Etc/UTC` for consistency across environments

### Folder Structure Requirements (If Using)

- **docker-compose.yml**: Required - Main compose file
- **.env.example**: Optional - Include if service has environment variables that users need to configure
- **README.md**: Optional - Include for services that need detailed setup instructions or have special requirements

Once your issue is submitted, a maintainer will review it and merge the changes into the main repository. Thank you for helping grow the Marketplace—your contributions make it better for everyone! If you have questions, feel free to comment on an existing issue or discuss in the repo's Discussions section.
