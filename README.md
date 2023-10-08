# Create a JavaScript Action Using TypeScript

<!-- Recommend change owner/repo -->
![CI](https://github.com/korosuke613/typescript-action-template/actions/workflows/ci.yaml/badge.svg)

## Usage

> [!WARNING]  
> Fill in after repository creation.

## Development

### Rule

Adhere to the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). Because using [google-github-actions/release-please-action](https://github.com/google-github-actions/release-please-action) for the release.

### Release

A release pull request is automatically created when a change that requires a release is made.

- [release-please.yaml](https://github.com/korosuke613/typescript-action-template/blob/main/.github/workflows/release-please.yaml)
- [post-release-please.yaml](https://github.com/korosuke613/typescript-action-template/blob/main/.github/workflows/post-release-please.yaml)

After the pull request merge, a release is created and tags for major, minor, and patch are created.

## Initial Setup

> [!WARNING]  
> It describes the steps that are required when a repository is created from a template.

### Create Repository

1. Click **Use this template** button

### Create GitHub App

GitHub App is required for release.

1. Create a GitHub App with the following settings. The rest of the values are optional.
   - Uncheck `Webhook` -> `Active`.
   - Set the following permissions in `Permissions` -> `Repository permissions`
     - `Contents` -> `Read & write`
     - `Pull requests` -> `Read & write`
2. Download `Private key`
3. Install App against the created repository
4. The following values will be used later.
   - App ID
   - Downloaded `Private key` path
   - App name (`https://github.com/settings/apps/<App name>`)

### Setting Repository

You will need to do some configuration of your repository to make a release.

- Set GitHub App information to Secrets, Variables
- Configure GitHub Actions to create pull requests

1. Preparing `.env`
    ```console
    cp .env.example .env
    ```
2. Fill in the contents of `.env`
3. Configure the necessary settings in the repository
    ```console
    GH_TOKEN=$(gh auth token) ./tools/repository-setup.sh
    ```

