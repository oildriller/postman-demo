# Postman Demo
This is a small demo repository to showcase how to implement automated tests in Postman and execute in CI pipeline.

## Postman collection
The collection within this repository contains a set of requests to test to create, read and modify a playlist via Spotify REST API.
The collection can be executed as it is or with data-driven approach using the [PostmanDemoData.csv](./PostmanDemoData.csv) as input data file.

## Execution
As a precondition you have to request get an [access token](https://developer.spotify.com/documentation/general/guides/authorization/code-flow) to be able to operate with Spotify API. 

Execute the collection via Postman or Newman.
 - Postman: import [Spotify automated.postman_collection.json](./Spotify%20automated.postman_collection.json) and [GitHubAPI.postman_environment.json](./SpotifyApi.postman_environment.json)
 - Newman: `newman run "potify automated.postman_collection.json" -e SpotifyApi.postman_environment.json -d PostmanDemoData.csv --global-var spotifyClientId=<SPOTIFY_CLIENT_ID> --global-var spotifyClientSecret=<SPOTIFY_CLIENT_ID> -r cli,emojitrain`

## Pipeline
The [ado_pipeline.yml](./ado_pipeline.yml) is an example for a simple Azure DevOps pipeline to execute the postman collection. The pipeline expects that the secrets are stored as secret pipeline variables. 

