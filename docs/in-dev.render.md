[base](../README.md) > [docs](./README.md) > in-dev > Render Deployment

# Deploying to Render.com

> [!WARNING]
> This feature is in development and is not yet ready for use.

This repository is configured for continuous deployment to [Render.com](https://render.com/)
on their free tier.

## How It Works

The deployment is defined using infrastructure-as-code in the `render.yaml`
file at the root of the repository.
This file tells Render to:

1.  **Create a Web Service:** Define a service of type `web`.
2.  **Use Docker:** Use the `docker` environment to build and deploy the
    service.
3.  **Use the Free Plan:** Deploy the service on the free instance type.
4.  **Configure Health Checks:** Use the `/` path to perform health checks,
    ensuring the service is running correctly.

## Getting Started

To deploy this repository to your own Render account:

1.  Create a new "Blueprint" service in the Render dashboard.
2.  Connect the GitHub repository you created from this template.
3.  Render will automatically detect and use the `render.yaml` file.
4.  Approve the plan, and Render will build and deploy the service.

Any subsequent pushes to your `main` branch will automatically trigger a new
deployment on Render.

## `render.yaml`

```yaml
services:
  - type: web
    name: base-template-app
    env: docker
    plan: free
    healthCheckPath: /
```
