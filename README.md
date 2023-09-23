INSTRUCTIONS: How to run using Docker and docker-compose
Now to run a new Fineract instance you can simply:

1.  git clone https://github.com/apache/fineract.git ; cd fineract

2.  docker-compose build

3.  docker-compose up -d

fineract (back-end) is running at https://localhost:8443/fineract-provider/

wait for https://localhost:8443/fineract-provider/actuator/health to return {"status":"UP"}
you must go to https://localhost:8443 and remember to accept the self-signed SSL certificate of the API once in your browser, otherwise you get a message that is rather misleading from the UI.

community-app (UI) is running at http://localhost:9090/?baseApiUrl=https://localhost:8443/fineract-provider&tenantIdentifier=default
login using default username mifos and password password

The docker-compose.yml will build the fineract container from the source based on the Dockerfile. You could change that to use the pre-built container image instead of having to re-build it.

https://hub.docker.com/r/apache/fineract has a pre-built container image of this project, built continuously.

You must specify the MySQL tenants database JDBC URL by passing it to the fineract container via environment variables; please consult the docker-compose.yml for exact details how to specify those. (Note that in previous versions, the mysqlserver environment variable used at docker build time instead of at docker run time did something similar; this has changed in FINERACT-773), and the mysqlserver environment variable is now no longer supported.)
