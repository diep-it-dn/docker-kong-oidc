# Build docker image and start all on the localhost
1. From the root dir, run `./build.sh` to build the docker image with tag: local/docker-kong-oidc:2.8.1
2. cd to `run-local` folder:
    
    Run: `make kong-postgres`
    
    Run: `make keycloak` if you don't have a running keycloak server
    
    Run: `ipconfig` and  get your current IP address then update for configure_oidc_plugin, patch_oidc_plugin in the Makefile.
    Run: `make init` to create some services, routes and configure oidc plugin

3. Test the kong-oidc:
   1. Open browser and go to: http://localhost:8000/mock, it should show the login page first if you haven't logged yet
   2. Login sucessfully by an user then you should view the data in http://localhost:8000/mock

4. Run `make clean` to clean the kong server

# Configure Keycloak
1.  Go to http://localhost:8085/auth/admin/master/console/#/master/clients then create a client with id kong then enable "Client authentication", "Authorization" 
2. Go to Credentials tab to copy Client Secret and replace it in the kong_secret var in the Makefile
3. In Settings tab, set "Root URL" to `http://localhost:8000`, "Valid redirect URIs" to `/*`
4. Create users, for example: client-user1
# Configure konga
1.  go to http://localhost:1337/register#!/connections and create an admin account
2.  in the Dashboard: http://localhost:1337/#!/dashboard, enter: example: kong-local as name, http://kong:8001 as Kong Admin URL

   Read more in the Makefile for more information!
