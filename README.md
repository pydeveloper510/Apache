# Apache
Forward proxy Reverse proxy

https://www.lesstif.com/system-admin/forward-proxy-reverse-proxy-21430345.html

https://roundfigure.tistory.com/34


#LoadModule proxy_module modules/mod_proxy.so

#LoadModule proxy_http_module modules/mod_proxy_http.so

<VirtualHost *:80>

  ServerName test.com
  
  ProxyRequests Off
  
  ProxyPreserveHost On
  
  ProxyPass / http://localhost:8080/
  
  ProxyPassReverse / http://localhost:8080/
  
</VirtualHost>

