```
server {
  server_name api.infostash.students.nomoreparties.sbs;

  location / {
    proxy_pass http://localhost:3001;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }

  listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/api.infostash.students.nomoreparties.sbs/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/api.infostash.students.nomoreparties.sbs/privkey.pem; # managed by Certbot  include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
  ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}


server {
  server_name infostash.students.nomoreparties.sbs www.infostash.students.nomoreparties.sbs;

  root /home/d.dzmitryeu/news-explorer-frontend;

  location / {
    try_files $uri $uri/ /index.html =404;
  }

  listen 443 ssl; # managed by Certbot
  ssl_certificate /etc/letsencrypt/live/infostash.students.nomoreparties.sbs/fullchain.pem; # managed by Certbot
  ssl_certificate_key /etc/letsencrypt/live/infostash.students.nomoreparties.sbs/privkey.pem; # managed by Certbot
  include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
  ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}


server {
  if ($host = www.infostash.students.nomoreparties.sbs) {
    return 301 https://$host$request_uri;
  } # managed by Certbot

  if ($host = infostash.students.nomoreparties.sbs) {
    return 301 https://$host$request_uri;
  } # managed by Certbot

  listen 80;

  server_name infostash.students.nomoreparties.sbs www.infostash.students.nomoreparties.sbs;
  return 404; # managed by Certbot
}
```