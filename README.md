# keycloak-custom-authenticaor
- mvn clean install
- Add the jar @ /opt/keycloak/providers/ in keycloak
- Now modify direct grant flow to add only username and sa-otp authenticator. (Direct flow would look like below )
![image](https://github.com/prasanna4742/keycloak-custom-authenticaor/assets/17253064/1ab58703-393f-40ea-84f2-1a846de33ac1)
- Create a user and fetch the token with below command, example below:
curl   -d "client_id=directtestsa1"   -d "username=pras"   -d "password=password"   -d "otp=1234"   -d "grant_type=password"   "http://localhost:8180/realms/SA/protocol/openid-connect/token"
- Authenticator has hard coded check for value 1234, if there's any other value you get 401, example below:
curl -d "client_id=directtestsa1"   -d "username=pras"   -d "password=password"   -d "otp=12345"   -d "grant_type=password"   "http://localhost:8180/realms/SA/protocol/openid-connect/token"
