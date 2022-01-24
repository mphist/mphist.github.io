---
title: Setting up SSL on Server
cover: './cover.png'
date: 2022-01-24
description: We'll set up a SSL Certificate on the server with Let's Encrypt
tags: ['Nginx', 'DigitalOCean', 'SSL', "Let's Encrypt", 'Ubuntu']
---

Let's Encrypt is a Certificate Authority which allows you obtain and install free TLS/SSL certificates. Certbot from Let's Encrypt automates the whole process of obtaining and installing a certficate on your server running Nginx or Apache.

This article assumes that you have a domain name for your server. If you do not have a domain name, you need to create a self-signed SSL certificate. Visit [here](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-16-04) to see how to add a self-signed SSL certificate on your server.

Let's get started.

### Install Certbot

Use the following command to install Certbot:

```
$ sudo apt install certbot python3-certbot-nginx
```

### Obtain and Install an SSL Certificate

Once Cerbot is installed, we can run the following command to obtain a SSL certificate for our server:

**NOTE: Replace example.com with your domain name**

```
sudo certbot --nginx -d example.com -d www.example.com
```

Follow the steps in the prompt and agree to their terms of service. At the end of this, the certificate will be downloaded, installed, and loaded on your server. Your website should now be secured.

### Verify Certbot Auto-Renewal

Let's Encrypt's certificates are valid for 90 days. We can use Certbot to automaically renew our certificates which are within 30 days of expiration.

Certbot has a command for testing its certificate renewal process. By running this command, it will test its renewal process and it will also renew your certificates and reload Nginx to use the renewed certificates.

```
$ sudo certbot renew --dry-run
```

### Conclusion

We set up a SSL Certificate on our server using Let's Encrypt. With Certbot, most of the processes were automated, which makes it very easy to install SSL certificates on your server.
