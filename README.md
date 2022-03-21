# Apache (Reverse Proxy)
Forward proxy Reverse proxy

https://www.lesstif.com/system-admin/forward-proxy-reverse-proxy-21430345.html

https://roundfigure.tistory.com/34

https://playon.tistory.com/87

*https://judo0179.tistory.com/34    change path

# httpd.conf
```
#LoadModule proxy_module modules/mod_proxy.so

#LoadModule proxy_http_module modules/mod_proxy_http.so
```
```
<VirtualHost *:80>

  ServerName test.com
  
  ProxyRequests Off
  
  ProxyPreserveHost On
  
  ProxyPass / http://localhost:8080/
  
  ProxyPassReverse / http://localhost:8080/
  
</VirtualHost>
```

```
<VirtualHost *:2087>
  ServerName madegame.net

  ProxyRequests Off
  SSLProxyEngine on

  ProxyPreserveHost On
  AllowEncodedSlashes On

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>

  SSLEngine on
  SSLProxyVerify none
  SSLProxyCheckPeerCN off
  SSLProxyCheckPeerName off
  SSLProxyCheckPeerExpire off


  ProxyPass / http://localhost:3081/
  ProxyPassReverse / localhost:3081/

  RequestHeader set X-Forwarded-Proto "https"
  RequestHeader set X-Forwarded-Port "443"

  #"D:\Xampp\apache\conf\keys\rootca.crt"
  #SSLCertificateFile "D:\Xampp\apache\conf\keys\certificate.crt"
  #SSLCertificateKeyFile "D:\Xampp\apache\conf\keys\private.key"

  SSLCertificateFile "D:\Xampp\apache\conf\keys\rootca.crt"
  SSLCertificateKeyFile "D:\Xampp\apache\conf\keys\rootca.key"
</VirtualHost>
```
# Create certificate key (https)

https://manage.sslforfree.com/dashboard
