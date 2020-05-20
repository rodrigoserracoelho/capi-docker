# CAPI Gateway (Docker)
> Light API Gateway implemented with Apache Camel
### To install CAPI Gateway for Docker, follow the instructions bellow:
_To run CAPI Gateway on localhost, a certificate, trust store and private keys are already generated_
1.  Clone this project.
``
$ git clone https://github.com/rodrigoserracoelho/capi-docker.git
``
2.  Run it
``
$ cd capi-docker
``
``
$ sudo docker-compose up -d
``

3. Because of a Keycloak limitation (only running on localhost), you will need to add the **keycloak** to your hosts file.
``
$ vi /etc/hosts
``
``
127.0.0.1 keycloak
``
4. There is already a client created on Keycloak, so you can request your first token:
``
curl --location --request POST 'https://keycloak:8443/auth/realms/capi/protocol/openid-connect/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Basic bWFuYWdlcjo5ODg0MDRkMy0zOGJkLTQyNDYtYTkyMy04Yjc3MmMyMTNiODg=' \
--data-urlencode 'grant_type=client_credentials'
``
5. Copy the provided _access_token_ and visit CAPI API Manager Swagger page
``
https://localhost:8080/swagger-ui.html
``
6. You also call directly the CAPI API Manager to list for example all deployed API's:
``
curl -X GET "https://localhost:8080/route" -H "accept: application/json" -H "Authorization: Bearer <provided access token>"
``
