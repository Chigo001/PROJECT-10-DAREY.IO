  PROJECT 10
* LOAD BALANCER SOLUTION WITH NGINX AND SSL/TLS.
* CONFIGURE NGINX AS A LOAD BALANCER
* The first step i took was create an EC2 VM based on Ubuntu Server 20.04 LTS and named it Nginx LB. I also opened all the necessary security group to secure HTTP and HTTPS Connections.
<img width="1440" alt="Screenshot 2023-02-28 at 11 46 30 AM" src="https://user-images.githubusercontent.com/115854902/224564016-ee789075-fda7-4940-9823-5e7d167a76e6.png">
* I updated my /etc/hosts file with Web Servers names and their local IP addresses.
* The next step was to update and install nginx as a load balancer to point traffic to the resolvable DNS names of the webservers
<img width="1440" alt="Screenshot 2023-03-10 at 11 13 51 AM" src="https://user-images.githubusercontent.com/115854902/224564319-a8599e33-0907-45d8-9071-d7cdfe3687df.png">
<img width="1440" alt="Screenshot 2023-03-10 at 11 19 15 AM" src="https://user-images.githubusercontent.com/115854902/224564350-4b3c963e-7d97-4b90-8160-1620bddf7b89.png">
<img width="1440" alt="Screenshot 2023-03-10 at 11 20 42 AM" src="https://user-images.githubusercontent.com/115854902/224564574-06924b76-9074-473b-a2c7-b778d0129623.png">
I opened the default nginx configuration file to insert the given configuration into the http section. I also edited my server name with my domain name and also commented out this line.
# include /etc/nginx/sites-enabled/*;

<img width="1440" alt="Screenshot 2023-03-02 at 4 14 17 PM" src="https://user-images.githubusercontent.com/115854902/224564764-0486c79a-2d46-4ed0-8c7b-3b893e0aef99.png">

STEP 2
* REGISTER A NEW DOMAIN NAME AND CONFIGURE SECURED CONNECTION USING SSL/TLS CERTIFICATE.

* I registered a new domain name (toolingysf.website) using Bluehost.com
<img width="1440" alt="Screenshot 2023-03-02 at 3 25 32 PM" src="https://user-images.githubusercontent.com/115854902/224566334-ee9652f1-8e65-4da4-9003-8f24b97e0a91.png">
* I searched for Route 53 on my AWS Console and created a hosted zone .
<img width="1440" alt="Screenshot 2023-03-02 at 3 32 59 PM" src="https://user-images.githubusercontent.com/115854902/224566469-fb65338b-7b2b-46c2-91e4-6061b180edee.png">

* I updated a record in my registrar to point to my Nginx LB IP address.
* I attached the values of my record to my domain name servers and saved it.
<img width="1440" alt="Screenshot 2023-03-10 at 2 47 39 PM" src="https://user-images.githubusercontent.com/115854902/224566747-65fc404d-e555-41c7-b05b-bb75635ab6e5.png">
<img width="1440" alt="Screenshot 2023-03-02 at 3 53 02 PM" src="https://user-images.githubusercontent.com/115854902/224566786-12f92d0e-b69f-4a33-8486-46db7b725da0.png">

Then I went ahead to access my web servers using my new domain name with HTTP protocol.
<img width="1440" alt="Screenshot 2023-03-12 at 3 29 11 PM" src="https://user-images.githubusercontent.com/115854902/224566910-8ccbb9a8-360f-4dc0-9cf1-ae1e66532aad.png">

* I installed certbot and requested an SSL/TLS Certificate.
<img width="1440" alt="Screenshot 2023-03-12 at 3 59 00 PM" src="https://user-images.githubusercontent.com/115854902/224566999-0f14f9ac-de83-4e3a-805f-376233181966.png">
<img width="1440" alt="Screenshot 2023-03-12 at 4 07 54 PM" src="https://user-images.githubusercontent.com/115854902/224567175-c9fee2f5-dc91-4690-944f-a03546c1fe1f.png">
<img width="1440" alt="Screenshot 2023-03-12 at 4 08 03 PM" src="https://user-images.githubusercontent.com/115854902/224567290-e65c2f76-66e8-4731-8ad7-8b1a4bdd004f.png">

I secured access to my web solution by trying to reach it using HTTPS protocol.
<img width="1440" alt="Screenshot 2023-03-12 at 4 08 28 PM" src="https://user-images.githubusercontent.com/115854902/224567321-fbf7e645-8341-44ae-b1f6-7f7a33bc0542.png">

I was also able to view the details of the certificate for my website.
<img width="1440" alt="Screenshot 2023-03-12 at 4 09 36 PM" src="https://user-images.githubusercontent.com/115854902/224567522-d847e0aa-d051-4514-b87d-6e126e857a67.png">
<img width="1440" alt="Screenshot 2023-03-12 at 4 36 48 PM" src="https://user-images.githubusercontent.com/115854902/224567569-feeef738-ca41-4b45-b8c0-b77bb8af81d9.png">

* Next step was to set up periodical renewal for my SSL/TLS certificate.
<img width="1440" alt="Screenshot 2023-03-12 at 4 32 16 PM" src="https://user-images.githubusercontent.com/115854902/224567642-fc971f9c-c476-427d-bd00-3c2f8cad4429.png">

* I configured a cron job to run the command twice a day by editing the crontab file and adding the given line to it.
* <img width="1440" alt="Screenshot 2023-03-12 at 4 29 27 PM" src="https://user-images.githubusercontent.com/115854902/224567910-2e1e96a5-b4a0-4146-b34c-436454655bb7.png">





