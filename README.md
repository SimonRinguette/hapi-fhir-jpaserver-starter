# Container version of HAPI Fhir

This was adapted from [This project](https://github.com/hapifhir/hapi-fhir-jpaserver-starter).

We changed back some of the icons and also added the build pipeline for GitHub.

We added a volume under `/db` that can either be mounted for persistence or not to restart from a blank database every time.


## Running using docker

### Run the server on port 8080 locally

```
docker pull ghcr.io/trisotech/hapi-fhir:v7.0.0
docker run -p 8080:8080 ghcr.io/trisotech/hapi-fhir:v7.0.0
```
Server is accessible at: `http://localhost:8080/`

### To change the port:
docker run -p 8081:8080 ghcr.io/trisotech/hapi-fhir:vX.X.X

If you change the port, update the FHIR base URL used by external tools.

### To overwrite the data volume locally:

```
docker run -p 8080:8080 -v c:\a\data:/db ghcr.io/trisotech/hapi-fhir:vX.X.X
```

You may take the database located at https://github.com/Trisotech/HAPI-FHIR/blob/master/fhir-db/fhir.mv.db as a starting point.


### Configuration via environment variables

You can customize HAPI directly from the `run` command using environment variables. For example:

```
docker run -p 8080:8080 -e hapi.fhir.default_encoding=xml ghcr.io/trisotech/hapi-fhir:v7.0.0
```

HAPI looks in the environment variables for properties in the [application.yaml](https://github.com/Trisotech/HAPI-FHIR/blob/master/src/main/resources/application.yaml) file for defaults.