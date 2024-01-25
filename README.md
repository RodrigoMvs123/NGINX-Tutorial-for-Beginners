# NGINX-Tutorial-for-Beginners

https://www.youtube.com/watch?v=9t9Mp0BGnyI 

https://www.airbnb.com/ 
Inspect 
Network
Headers
Request URL
Request Method
Status Code
Remote Address 
Reffer Policy
Response Headers
Server: nginx ( Web Server ) 

Computer -> Request -> ( AWS Server ) -> Response 

Reverse Proxy / Load Balancer 
Computer -> Request -> ( Nginx ) -> Request ( Airbnb ) -> Response to Nginx -> Response to Browser

NGINX Installation 
On Windows
https://nginx.org/en/docs/windows.html 

Download
cd c:\
unzip nginx-1.25.3.zip
cd nginx-1.25.3
start nginx
localhost

code .

Visual Studio Code
Explorer
Open Editors
nginx.conf

nginx.conf

#user  nobody;
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;

    server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   html;
            index  index.html index.htm;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

}

Nginx Terminology 

Key-value pairs 
Directive 
Block of code
Context 


Nginx Serving Static Content 

Visual Studio Code
Explorer
Open Editors
nginx.conf
index.html

index.html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

Visual Studio Code
Terminal 
nginx -s reload

Visual Studio Code
Explorer
Open Editors
index.html
nginx.conf

nginx.conf
http {
    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;
    }
}

events {}

Visual Studio Code
Explorer
Open Editors
index.html

index.html
    <html>
        <body>
            <h1>Hello my friends. I am served from NGINX</h1>
        </body>
    </html>

Nginx Mime Types

Visual Studio Code
Explorer
Open Editors
nginx.conf
index.html
styles.css

styles.css
h1 {
    background-color: pink;
    color: aqua;
}

Visual Studio Code
Explorer
Open Editors
nginx.conf
styles.css
index.html

index.html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>My NGINX Project</title>
        <link rel="stylesheet" href="./styles.css">
    </head>
        <body>
            <h1>Hello my friends. I am served from NGINX</h1>
        </body>
    </html>


Visual Studio Code
Explorer
Open Editors
styles.css
index.html
nginx.conf

nginx.conf
http {

    types {
        text/css        css;
        text/html       html;
    }

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;
    }
}

events {}

localhost:8080
Inspect
Network
Content-Type: text/css

Visual Studio Code
Explorer
Open Editors
nginx.conf
styles.css
index.html
mime.types

mime.types

types {
    text/html                                        html htm shtml;
    text/css                                         css;
    text/xml                                         xml;
    image/gif                                        gif;
    image/jpeg                                       jpeg jpg;
    application/javascript                           js;
    application/atom+xml                             atom;
    application/rss+xml                              rss;

    text/mathml                                      mml;
    text/plain                                       txt;
    text/vnd.sun.j2me.app-descriptor                 jad;
    text/vnd.wap.wml                                 wml;
    text/x-component                                 htc;

    image/avif                                       avif;
    image/png                                        png;
    image/svg+xml                                    svg svgz;
    image/tiff                                       tif tiff;
    image/vnd.wap.wbmp                               wbmp;
    image/webp                                       webp;
    image/x-icon                                     ico;
    image/x-jng                                      jng;
    image/x-ms-bmp                                   bmp;

    font/woff                                        woff;
    font/woff2                                       woff2;

    application/java-archive                         jar war ear;
    application/json                                 json;
    application/mac-binhex40                         hqx;
    application/msword                               doc;
    application/pdf                                  pdf;
    application/postscript                           ps eps ai;
    application/rtf                                  rtf;
    application/vnd.apple.mpegurl                    m3u8;
    application/vnd.google-earth.kml+xml             kml;
    application/vnd.google-earth.kmz                 kmz;
    application/vnd.ms-excel                         xls;
    application/vnd.ms-fontobject                    eot;
    application/vnd.ms-powerpoint                    ppt;
    application/vnd.oasis.opendocument.graphics      odg;
    application/vnd.oasis.opendocument.presentation  odp;
    application/vnd.oasis.opendocument.spreadsheet   ods;
    application/vnd.oasis.opendocument.text          odt;
    application/vnd.openxmlformats-officedocument.presentationml.presentation
                                                     pptx;
    application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
                                                     xlsx;
    application/vnd.openxmlformats-officedocument.wordprocessingml.document
                                                     docx;
    application/vnd.wap.wmlc                         wmlc;
    application/wasm                                 wasm;
    application/x-7z-compressed                      7z;
    application/x-cocoa                              cco;
    application/x-java-archive-diff                  jardiff;
    application/x-java-jnlp-file                     jnlp;
    application/x-makeself                           run;
    application/x-perl                               pl pm;
    application/x-pilot                              prc pdb;
    application/x-rar-compressed                     rar;
    application/x-redhat-package-manager             rpm;
    application/x-sea                                sea;
    application/x-shockwave-flash                    swf;
    application/x-stuffit                            sit;
    application/x-tcl                                tcl tk;
    application/x-x509-ca-cert                       der pem crt;
    application/x-xpinstall                          xpi;
    application/xhtml+xml                            xhtml;
    application/xspf+xml                             xspf;
    application/zip                                  zip;

    application/octet-stream                         bin exe dll;
    application/octet-stream                         deb;
    application/octet-stream                         dmg;
    application/octet-stream                         iso img;
    application/octet-stream                         msi msp msm;

    audio/midi                                       mid midi kar;
    audio/mpeg                                       mp3;
    audio/ogg                                        ogg;
    audio/x-m4a                                      m4a;
    audio/x-realaudio                                ra;

    video/3gpp                                       3gpp 3gp;
    video/mp2t                                       ts;
    video/mp4                                        mp4;
    video/mpeg                                       mpeg mpg;
    video/quicktime                                  mov;
    video/webm                                       webm;
    video/x-flv                                      flv;
    video/x-m4v                                      m4v;
    video/x-mng                                      mng;
    video/x-ms-asf                                   asx asf;
    video/x-ms-wmv                                   wmv;
    video/x-msvideo                                  avi;
}

Visual Studio Code
Explorer
Open Editors
styles.css
index.html
mime.types
nginx.conf

nginx.conf
http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;
    }
}

events {}

Nginx Location Block 

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
index.html
mime.types

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
index.html
mime.types


index.html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>My NGINX Project</title>
    </head>
        <body>
            <ul>
                <li>Mango</li>
                <li>Strawberry</li>
                <li>Watermelon</li>
            </ul>>
        </body>
    </html>

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
index.html
mime.types

nginx.conf
http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }
    }
    
}

events {}


Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
vegetables
veggies.html
index.html
mime.types

veggies.html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>My NGINX Project</title>
    </head>
        <body>
            <ul>
                <li>Lettuce</li>
                <li>Eggplant</li>
                <li>Onion</li>
            </ul>>
        </body>
    </html>

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
vegetables
veggies.html
index.html
mime.types

nginx.conf
http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }

        location /vegetables {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /vegetables/veggies.html /index.html =404;
        }
    }
    
}

events {}

Visual Studio Code
Terminal
nginx -s reload 

Nginx Redirects and Rewrites

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
vegetables
veggies.html
index.html
mime.types

nginx.conf
http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }

        location /vegetables {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /vegetables/veggies.html /index.html =404;
        }

        location /crops {
            return 307 /fruits
        }

    }
    
}

events {}http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }

        location /vegetables {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /vegetables/veggies.html /index.html =404;
        }

        location /crops {
            return 307 /fruits;
        }

    }
    
}

events {}

Visual Studio Code
Terminal
nginx -s reload 

localhost:8080/crops/ ( Redirect to http://localhost:8080/fruits/ )

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
vegetables
veggies.html
index.html
mime.types

nginx.conf
http {

    include mime.types;

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        rewrite ^/number/(\w+) /count/$1;

        location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }

        location /vegetables {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /vegetables/veggies.html /index.html =404;
        }

        location /crops {
            return 307 /fruits;
        }

    }
    
}

events {}

Visual Studio Code
Terminal
nginx -s reload 

localhost:8080/number/3 ( Redirect to  
location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }
)

Nginx Load Balancer 

Reverse Proxy / Load Balancer 
Computer -> Request -> ( Nginx ) -> Request ( Airbnb ) -> Response to Nginx -> Response to Browser

Computer -> Request -> ( Nginx ) -> Request ( AWS ) -> Response to Nginx -> Response to Browser

…

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
server
index.js
vegetables
veggies.html
index.html
mime.types

index.js


Visual Studio Code
Terminal
cd server
npm init
npm init -y
npm install express

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
server
index.js
package.json
vegetables
veggies.html
index.html
mime.types

package.json
//…
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index"
},
//…

Visual Studio Code
Terminal
npm run start

Docker Compose 
Make a Docker Container 
https://docs.docker.com/language/nodejs/containerize/ 

// Dockerfile:

FROM node:10

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# Bundle app source
COPY . .

EXPOSE 8080
CMD [ "node", "server.js" ]

Visual Studio Code
Explorer 
Open Editors 
nginx.conf
styles.css
fruits
server
Dockerfile
index.js
package.json
vegetables
veggies.html
index.html
mime.types

Dockerfile
// Dockerfile:

FROM node:10

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# Bundle app source
COPY . .

EXPOSE 7777
CMD [ "npm", "run", "start" ]

Visual Studio Code
Terminal
cd server
docker build . -t myserver // Image ( myserver ) 
docker run -p 1111:7777 -d myserver

localhost:1111
I am a endpoint

Visual Studio Code
Terminal
docker run -p 2222:7777 -d myserver
docker run -p 3333:7777 -d myserver
docker run -p 4444:7777 -d myserver

Visual Studio Code
Explorer 
Open Editors
nginx.conf
styles.css
fruits
server
index.js
package.json
vegetables
veggies.html
index.html
mime.types

nginx.conf
http {

    include mime.types;

    upstream backendserver {
        server 127.0.0.1:1111;
        server 127.0.0.1:2222;
        server 127.0.0.1:3333;
        server 127.0.0.1:4444;
    }

    server {
        listen 8080;
        root C:/Users/Matheus/Desktop/Rodrigo/nginx;

        rewrite ^/number/(\w+) /count/$1;

        location / {
            proxy_pass http://backendserver/;
        }

        location ~* /count/[0-9] {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /index.html =404;
        }

        location /fruits {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
        }

        location /carbs {
            alias C:/Users/Matheus/Desktop/Rodrigo/nginx/fruits;
        }

        location /vegetables {
            root C:/Users/Matheus/Desktop/Rodrigo/nginx;
            try_files /vegetables/veggies.html /index.html =404;
        }

        location /crops {
            return 307 /fruits;
        }

    }
    
}

events {}

Visual Studio Code
Terminal
nginx -s reload

localhost:8080
I am a endpoint

localhost:8080
I am a endpoint

localhost:8080
I am a endpoint

localhost:8080
I am a endpoint





















