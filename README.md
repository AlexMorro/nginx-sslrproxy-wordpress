# nginx-sslrproxy-wordpress
# Docker compose
Default wordpress config for docker-compose from docker hub.

Added nginx:
  - port forwarding 80 and 443
  - add volumes for configuration file, ssl certificate and ssl key.

# NGINX configuration file (default.conf)
One server block for redirecting http to https.

The other server block listens for port 443 with ssl, specifies the certificate, and the location block for redirecting to the wordpress server and set the headers to forward to the wordpress server.

It doesn’t need any IP because the internal docker DNS does the job.


I created my own certificate using openssl

# Start the app stack
You just need the docker-compose.yml and the nginx folder with the config file and the certificate and key inside the folder ssl. Then with docker compose up it’s up and running.

```
./project Folder/
|   docker-compose.yml
|
\---./nginx
    |   default.conf
    |   
    \---./ssl
            nginx-selfsigned.crt
            nginx-selfsigned.key
```

Note: this will create a new and default wordpress installation, if you want to maintain the wordpress config you’ll also need the wordpress and database folders at the same level as the nginx one.
