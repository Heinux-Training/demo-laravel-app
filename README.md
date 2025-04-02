# demo-laravel-app
Sample application using Laravel framework.

## Deployment

This application can be deployed to staging and production environments using the provided GitHub Actions workflows.

### Prerequisites

- SSH deploy keys for the target server(s).
- The following environment variables must be set as secrets in the repository:
  - `SSH_PRIVATE_KEY`: The private key for SSH authentication.
  - `SSH_HOST`: The hostname or IP address of the server.
  - `SSH_USERNAME`: The username for SSH authentication.
  - `DEPLOY_PATH`: The absolute path to the application directory on the server.

### Deployment Steps

1. **Configure SSH Deploy Keys:**
   - Generate an SSH key pair on your local machine if you don't have one.
   - Add the public key to the authorized keys on your server.
   - Add the private key as a secret named `SSH_PRIVATE_KEY` in your GitHub repository.

2. **Set Environment Variables:**
   - Set the required environment variables (`SSH_HOST`, `SSH_USERNAME`, `DEPLOY_PATH`) as secrets in your GitHub repository.

3. **Create Deployment Workflows:**
   - The repository already includes deployment workflows in `.github/workflows/deploy-staging.yml` and `.github/workflows/deploy-production.yml`.

4. **Trigger Deployment:**
   - To deploy to the staging environment, push changes to the `dev` branch.
   - To deploy to the production environment, create a release or tag on the `main` branch.

The workflows will automatically handle the deployment process, including:
- Checking out the code.
- Setting up SSH.
- Deploying the code to the server.
- Installing dependencies using `composer`.
- Running database migrations.
- Optimizing the application.