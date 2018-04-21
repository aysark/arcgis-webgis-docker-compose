# Docker Compose of WebGIS
This composer will spin up 3 containers (Server, Datastore, Portal & WA) on the same bridge network so they will be able to link to each other to compose a WebGIS stack.

Successfully tested on hosts: ubuntu, rhel using 10.5-10.6.1 images

# Requirements
- you're own docker images of: Server, Datastore, Portal & WA
- atleast 20gb of space
- if running on linux, you may need to install docker-compose
- all WebGIS ports must be free (stop any existing portal/server/datastore services)

# Setup your stack

To get started all you have to do is: `docker-compose up`

Once all containers are deployed and healthy, its time to configure your stack:

1. To setup, first go to Server and create a site: `https://localhost:6443/arcgis/manager/`  

2. Next setup datastore:
`https://localhost:2443/arcgis/datastore/`  And enter the server URL as: `https://SERVER:6443/arcgis`  

3. Next setup portal via: `https://your_machine_ip:7443/arcgis/home/`  

4. Next setup portal with webadaptor via: `https://localhost/arcgis/webadaptor`  Enter your Portal URL as: `https://your_machine_ip:7443` 

5. Finally, federate your portal, by going to portal settings.  Enter your server services URL as: `https://your_machine_ip/arcgis`  And your server admin url as: `https://SERVER:6443/arcgis`

Note: the urls are case sensitive due to how docker does networks.

To clean up, simply run: `docker-compose down`
