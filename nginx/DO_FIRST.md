Expose Nginx’s internal stats endpoint.

Add this to your Nginx config (nginx.conf or a site conf like /etc/nginx/conf.d/default.conf):

```
server {
    listen 127.0.0.1:8080;
    location /nginx_status {
        stub_status;
        allow 127.0.0.1;
        deny all;
    }
}
```
Then test, reload, test

```
sudo nginx -t
sudo systemctl reload nginx
curl http://127.0.0.1:8080/nginx_status
```

Should see something like this if working properly
```
Active connections: 2 
server accepts handled requests
 100 100 200
Reading: 0 Writing: 1 Waiting: 1
```