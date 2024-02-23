# demo-baldev
server {
  listen   80;
  root /var/www/html;
  index index.php index.htm;
  server_name _;
  location / {
    try_files $uri $uri/ /index.html;
  }

  location ~ \.php$ {
    try_files $uri =404;
    fastcgi_pass 127.0.0.1:9000;
#    astcgi_pass /run/php7.4-fpm.sock
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME                     $document_root$fastcgi_script_name;
    include fastcgi_params;
  }
}
