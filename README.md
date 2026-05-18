# Hello Word on Amazon Lightsail

This repository contains a simple Dockerized "Hello Word" application and a GitHub Actions CI/CD workflow to deploy it to an Amazon Lightsail instance.

## What this includes

- `app.js` - simple Node.js Express app that returns `Hello Word`
- `Dockerfile` - builds the app into a Docker image
- `.github/workflows/deploy.yml` - GitHub Actions workflow that deploys via SSH to Lightsail

## Setup

1. Create an Amazon Lightsail Linux instance with Docker installed.
2. Open port `80` and `22` in Lightsail networking.
3. Add your instance SSH private key to GitHub Secrets.
4. Create the required GitHub Secrets below.

## Required GitHub Secrets

- `LIGHTSAIL_SSH_HOST` - the Lightsail public IP or hostname
- `LIGHTSAIL_SSH_USER` - SSH username (`ubuntu`, `ec2-user`, `bitnami`, or your instance user)
- `LIGHTSAIL_SSH_PRIVATE_KEY` - private key content with access to the Lightsail instance
- `LIGHTSAIL_REMOTE_PATH` - remote deployment directory, e.g. `/home/ubuntu/hello-word`

## Deploy

Push to the `main` branch and the workflow will:

1. checkout the repository
2. copy app files to the Lightsail instance
3. build the Docker image on Lightsail
4. run the container on port `80`

## Access

Open your Lightsail public IP in a browser. You should see:

```
Hello Word
```
