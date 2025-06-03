/etc/nginx/nginx.conf must have this inside it's http block:

```
   http {
        server {
            listen 80;
            server_name 172.26.0.1 host.docker.internal;

            location /nginx_status {
                stub_status;
                allow 127.0.0.1;
                allow 172.26.0.0/16;
                allow ::1;
                deny all;
            }
        }
   }
```