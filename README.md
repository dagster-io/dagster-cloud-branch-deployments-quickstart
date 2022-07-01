# Dagster Cloud Branch Deploments Quickstart

Template to get started with Dagster Cloud Branch Deployments.

## Create a new repository from this template

Click the `Use this Template` button and provide details for your new repo.

<img width="953" alt="Screen Shot 2022-07-06 at 7 24 02 AM" src="https://user-images.githubusercontent.com/10215173/177577141-b6a91585-a276-49d3-b66b-e47bd26665a0.png">


## Modify GitHub Workflow

Edit the [GitHub Workflows](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions#create-an-example-workflow) at
[`.github/workflows/deploy.yml`](./.github/workflows/deploy.yml) and 
[`.github/workflows/branch_deployments.yml`](./.github/workflows/branch_deployments.yml) to set up Docker registry access. Uncomment the step associated with your
registry (ECR, DockerHub, GCR etc.), and take note of which secrets will need to be defined for your particular platform.
## Set up secrets

Set up secrets on your newly created repository by navigating to the `Settings` panel in your repo, clicking `Secrets` on the sidebar, and selecting `Actions`. Then, click `New repository secret`.


| Name           | Description |
|----------------|-------------|
| `DAGSTER_CLOUD_API_TOKEN` | An agent token, for more details see [the Dagster Cloud docs](https://docs.dagster.cloud/auth#managing-user-and-agent-tokens). |
| `REGISTRY_URL` | The URL of the Docker image registry you would like to deploy from. This must be accessible to your agent. |
| `ORGANIZATION_ID` | The organization ID of your Dagster Cloud organization, found in the URL. For example, `pied-piper` if your organization is found at `https://dagster.cloud/pied-piper` or `https://pied-piper.dagster.cloud/`. |
| Docker access secrets  | Depending on which Docker registry you are using, you must define the credentials listed in the workflow file. |

<img width="1143" alt="GitHub settings page" src="https://user-images.githubusercontent.com/10215173/177576864-cbf88e90-9c92-41f6-b513-7bbae50b7ed7.png">


## Verify Builds are Successful

At this point, the Workflow should complete successfully. If builds are failing, ensure that your
secrets are properly set up the Workflow properly sets up Docker regsitry access.

<img width="1029" alt="Successful build" src="https://user-images.githubusercontent.com/10215173/177576774-86198b14-0241-4542-95ef-dd9b2cb7dcae.png">

## Adding or Modfiying Code Locations

To add new code locations to be built or to modify the existing location definition, change the [input matrix](https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs) at the top of each action file.

For example:

```yaml
matrix:
  # Here, define the code locations that should be built and deployed
  location:
    - name: foo_location
      # Dockerfile location
      build_folder: my_package/foo_location
      # Docker registry URL
      registry: https://364536301934.dkr.ecr.us-west-2.amazonaws.com/foo-location
      # Path to file containing location definition
      location_file: cloud_workspace.yaml
    - name: bar_location
      build_folder: my_package/bar_location
      registry: https://364536301934.dkr.ecr.us-west-2.amazonaws.com/bar-location
      location_file: cloud_workspace.yaml
```

The `location_file` specified can either contain a single location's
definition, or a list of multiple locations' definitions.
