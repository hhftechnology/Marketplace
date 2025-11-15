# How to Contribute

The Marketplace is a community-driven project. We welcome contributions from everyone! To add a new self-hosted service or update an existing one, please open a GitHub [Issue](https://github.com/hhftechnology/Marketplace/issues) using the template below. This helps us review and integrate your submission efficiently.

## Submission Template

Use this structure in your issue description:

### Service Name
[Enter the name of the service, e.g., `nginx` or `redis`. Keep it concise and descriptive.]

### Example docker-compose.yml
```yaml
[Paste a complete, working `docker-compose.yml` configuration here. Use code block formatting for readability.]
```

### Documentation or References
[Provide links to official documentation, Docker Hub pages, GitHub repositories, or other relevant resources.]

### Notes
[Any additional context, setup instructions, or caveats. If this is an update to an existing service, prefix with "Update: " and describe the changes.]

## Submission Guidelines

Before opening your issue, please verify that your `docker-compose.yml` meets these standards to streamline the review process:

- **Remove comments**: Strip out all inline comments from the file for cleanliness.
- **Minimize extras**: Eliminate unnecessary ports, environment variables, volumes, or other configurations.
- **Public images only**: Ensure the Docker image(s) are publicly accessible (no private registries).
- **Inline environment variables**: Include all required environment variables directly in the file—do not reference external `.env` files.
- **Prefer latest tags**: Use the `latest` image tag where possible, unless a specific version is required for stability.
- **Multi-service support**: It's okay to include multiple related services in one compose file (e.g., a main app + dependencies), as long as they function together.
- **Standardize volumes**: Replace absolute host paths with descriptive, uppercase placeholders (e.g., change `/data/adguard-home/work:/opt/adguardhome/work` to `/WORK_DIR:/opt/adguardhome/work`).
- **Set timezone**: Default to `Etc/UTC` for consistency across environments.

Once your issue is submitted, a maintainer will review it and merge the changes into the main repository. Thank you for helping grow the Marketplace—your contributions make it better for everyone! If you have questions, feel free to comment on an existing issue or discuss in the repo's Discussions section.