# Dagster Cloud Branch Deploments Quickstart

Template to get started with Dagster Cloud Branch Deployments.

## Create a new repository from this template

Click the `Use this Template` button and provide details for your new repo.

![Creating a copy of the Template repo](https://user-images.githubusercontent.com/10215173/138138429-7a81e4d7-8fdf-4988-9758-2babcc90af5f.png)

## Set up secrets

Set up the secrets listed in the Docker registry access step (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`), as well as `DAGSTER_CLOUD_URL`, `REGISTRY_URI`, and `DAGSTER_CLOUD_API_TOKEN`,
in your GitHub repository's Settings page.

`DAGSTER_CLOUD_API_TOKEN` should contain an [agent token](https://docs.dagster.cloud/auth#managing-user-and-agent-tokens), e.g. `agent:hooli:1193cb69aaa34cfz83d44adcfe89b057`.

![GitHub settings page](https://user-images.githubusercontent.com/10215173/164542909-78f7b580-96e4-44a2-990e-d85cb1ec9319.png)

## Verify Builds are Successful

At this point, the Workflow should complete successfully. If builds are failing, ensure that your
secrets are properly set up the Workflow properly sets up Docker regsitry access.

![Screen Shot 2021-10-20 at 10 02 55 AM](https://user-images.githubusercontent.com/10215173/138138556-d147000f-c42d-4ab1-8187-3d6be3786142.png)
