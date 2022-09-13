1. From the root dir, run `./build.sh` to build the docker image with tag: local/docker-kong-oidc:2.8.1
2. cd to `run-local` folder
    Run: `make kong-postgres`
    Run: `make keycloak` if you don't have running keycloak server
3. Run `make clean` to clean the kong server
   
# Configure konga
1.  go to http://localhost:1337/register#!/connections and create an admin account
2.  in the Dashboard: http://localhost:1337/#!/dashboard, enter: example: kong-local as name, http://kong:8001 as Kong Admin URL

   Read more in the Makefile for more information!