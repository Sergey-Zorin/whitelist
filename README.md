# whitelist
Bash script preparing a set of rules to restrict access to nginx.

## How it works
Script `whitelist` allows you to create and maintain files like this
```
##### whitelist 'admin'
# allow <ip>; # <expire> <type> <name>

allow 11.11.11.11 ;   # 1647950342 login alice
allow 22.22.22.33 ;   # 1647950457 dns bob.home.org
allow 33.33.33.33 ;   # FOREVER dns charlie.ddns.net
```
Such files are stored by default in the `/etc/nginx/whitelists` directory.
You can use these files in nginx config
```
location /admin/ {
    include whitelists/admin[.]list;
    deny all;
    ...
}
```


