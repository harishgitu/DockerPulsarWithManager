# DockerPulsarWithManager
Docker compose file for running Pulsar Standalone and Pulsar Manager 

### Setup
1. Create a folder Pulsar
2. Copy the docker-compose file into the Pulsar folder
3. Run the following command (If you want to see the logs, don't include "-d" flag)
   ```bash
   docker-compose up -d
   ```

### Logging into Pulsar Manager
Run the following commands
```bash
CSRF_TOKEN=$(curl http://localhost:7750/pulsar-manager/csrf-token)
```
```bash
curl -H 'X-XSRF-TOKEN: $CSRF_TOKEN' -H 'Cookie: XSRF-TOKEN=$CSRF_TOKEN;' -H "Content-Type: application/json" -X PUT http://localhost:7750/pulsar-manager/users/superuser -d '{"name": "admin", "password": "adminpass", "description": "admin", "email": "admin@testemail.org"}'
```

Open the following URL
<ttp://localhost:9527>
Use the above username (`admin`) and password (`adminpass`) to login


### Setting up new environment
use the following value in "service URL" when setting up new environment (service name from docker-compose file)
```html
http://pulsarcore:8080
```

#### More reading and additiona options
- [Apache Pulsar](https://github.com/apache/pulsar-manager)
- [Wordpress Page](https://jpinjpblog.wordpress.com/2020/12/10/pulsar-with-manager-and-dashboard-on-docker-compose/)
