/etc/nginx/nginx.conf must have this inside it's http block:

```
   http {
       server {
           listen 80;
           server_name localhost;

           location /nginx_status {
               stub_status;
               allow 172.17.0.0/16;
               allow 127.0.0.1;
               deny all;
           }
       }
   }
```