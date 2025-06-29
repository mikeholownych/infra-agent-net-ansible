# Role: docs_site

## Purpose
Generates a versioned documentation website from Markdown sources (`README.md`) using MkDocs with the Material theme, and deploys it as a static site.

## Variables
- `site_dir`: Path to publish the built site (default: `/srv/docs/site`).
- `mkdocs_config`: Path to `mkdocs.yml` template (default in `templates/mkdocs.yml.j2`).

## Tasks
1. **Install Documentation Tools**: Installs MkDocs and Material theme via pip.
2. **Generate Configuration**: Renders `mkdocs.yml` from Jinja2 template with project metadata.
3. **Collect Sources**: Synchronizes `README.md` files into the MkDocs docs folder.
4. **Build Site**: Runs `mkdocs build` to generate the static site.
5. **Deploy Site**: Uses Docker Compose to serve the site (e.g., via an nginx container).

## Templates
- `templates/mkdocs.yml.j2`: Jinja2 config specifying site name, navigation, and theme settings.

## Usage
Invoke this role to publish up-to-date project documentation automatically after any changes to Markdown files, supporting versioned docs and search functionality.
