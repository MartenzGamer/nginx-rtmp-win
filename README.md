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
