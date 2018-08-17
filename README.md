# Apache
# yum install httpd
# systemctl start httpd.service

# yum install openssl
# yum install mod_ssl
# systemctl restart httpd.service

# cd /etc/pki/tls

- What site is the certificate for ?
# openssl x509 -in certs/localhost.crt -subject -noout

- Does it appear to be self-signed ?
# openssl x509 -in certs/localhost.crt -issuer -noout

- Does the certificate correspond to the key ?
# openssl x509 -in certs/localhost.crt -pubkey -noout
# openssl pkey -in private/localhost.key -pubout

- Key generation
# openssl genpkey -algorithm rsa -out private/keys.key -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:0x100000001

- Generate a self-signed certificate
# openssl req -new -x509 -subj "/CN=learn.tls.now/" -days 365 -extensions v3_req -key private/keys.key -out certs/selfsigned.crt
