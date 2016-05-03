### Setup docker registry

0. Clone project and enter into folder. 
1. Generate self-signed certificate `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./certs/domain.key -out ./certs/domain.crt` (Be sure to use the name of your domain as a CN.)
2. Create user `docker run --entrypoint htpasswd registry:2 -Bbn testuser testpassword > auth/htpasswd`
3. Start your registry `docker-compose up -d`.

### Login into registry from local computer

0. Copy&Paste file `./certs/domain.crt` to `/etc/docker/certs.d/myregistrydomain.com:5000/ca.crt` and restart docker.
1. Login `docker login -u testuser -p "testpassword" myregistrydomain.com:5000`.
