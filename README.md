For Docker follow the instructions bellow:
* Clone this project.
* Execute
    $ sudo docker-compose up -d
* If you are starting a fresh Mongo instance, a default CAPI Client will be created for you.
* Request your first access token: curl -X POST https://localhost:8080/oauth/token -H 'Authorization: Basic d2ViLXB1Ymxpc2hlcjp3ZWItY2xpZW50LXNlY3JldA==' -H 'Content-Type: multipart/form-data;' -F grant_type=client_credentials -F 'response_type=access_token'
* Go to: https://localhost:8080/swagger-ui.html
* Authenticate with the token you obtained from the previous step. (Don't forget to specify: Bearer <the token>)
* Publish your first API: 
    curl -X POST "https://localhost:8080/route/swagger-rest" -H "accept: application/json" -H "Content-Type: application/json" -d "<your-api>" (see Example of an API definition)
* Imagine that your context was: test and one of your GET path was /user you can then test: http://localhost:8380/gateway/test/user

Docker compose will create instances of Grafana, Prometheus and Zipkin, but if you wish to use already existing instances you just need to change this environment variables:

* api.gateway.prometheus.endpoint=http://prometheus:9090
* api.gateway.zipkin.endpoint=http://zipkin:9411/api/v2/spans
* api.gateway.grafana.endpoint=http://localhost:8080/grafana
