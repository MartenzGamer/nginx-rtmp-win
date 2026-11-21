# nginx-rtmp-win
A pre-compiled, ready-to-use version of Nginx for Windows.

# Components Included
This build includes the following components:

- Nginx 1.30.7
- OpenSSL 4.1.0
- PCRE2 10.49
- zlib 1.4

## Configuration 

```
 --with-cc=gcc \
 --prefix= \
 --add-module=../nginx-rtmp-module \
 --with-pcre=../pcre2-10.49 \
 --with-zlib=../zlib-1.4 \
 --with-http_ssl_module \
 --with-openssl=../openssl-4.1.0 \
 --with-cc-opt="-Wno-error"
```   

# Some tutorial

Edit nginx\conf\nginx.conf. Add the rtmp block at the very bottom, outside the http {} block:
```
rtmp {
 server {
 listen 1935;
 chunk_size 4096;
 application mystream {
 live on;
 record off;
 push rtmp://live.twitch.tv/app/YOUR_TWITCH_KEY;
 push rtmp://x.rtmp.youtube.com/live2/YOUR_YOUTUBE_KEY;
  }
 }
}
```
Optional status page. Add a server inside the http {} block:
```
server {
 listen 8080;
 location /stat {
 rtmp_stat all;
 rtmp_stat_stylesheet stat.xsl;
 }
 location /stat.xsl {
 root C:/nginx/conf;
 }
}
```
