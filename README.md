# Postman Demo
This is a small demo repository to showcase how to implement automated tests in Postman and execute in CI pipeline.

## Postman collection
The collection within this repository contains a set of requests to test the CRUD operations of the GitHub's Project API.
The collection can be executed as it is or with data-driven approach using the [PostmanDemoData.csv](./PostmanDemoData.csv) as input data file.

## Execution
As a precondition you have to create a [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). Set this token as a global variable named `gitHubApiToken` in Postman/Newman. 

Execute the collection via Postman or Newman.
 - Postman: import [Github Project CRUD II.postman_collection.json](./Github%20Project%20CRUD%20II.postman_collection.json) and [GitHubAPI.postman_environment.json](./GitHubAPI.postman_environment.json)
 - Newman: `newman run "Github Project CRUD II.postman_collection.json" -e GitHubAPI.postman_environment.json -d PostmanDemoData.csv --global-var gitHubApiToken=<GITHUB_PAT> -r cli,emojitrain`

## Pipeline
The [ado_pipeline.yml](./ado_pipeline.yml) is an example for a simple Azure DevOps pipeline to execute the postman collection. The pipeline expects that the GitHub PAT is stored as a secret environment variable named `GITHUB_API_TOKEN`. 

