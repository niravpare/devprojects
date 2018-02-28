# DevOps Project

This is a DevOps project where we are deploying one small HTML code on web server using few DevOps tools.

Tools used in this project.
1. Git
2. Docker
3. Wrecker
4. AWS ( EC2 linux, ElasticIP, ELB, SecurityGroup, ACM, Route53 )
5. Domain: mydevopsproject.com ( GoDaddy )

--> First place your code in index.hml file.
--> Create Docker repo for pushing and pulling Docker image.
--> Configure wrecker.yml file which includes automation configuration script. ( you can include if you want to deploy on specific port )
--> Add your files to Git repo.
--> Create CICD pipeline in Wrecker.
--> Create EC2 instance in AWS console.
--> Configure Security Group.
--> Add require environment in Wrecker. (Authentication and host detail )
--> Commit any changes and it will trigger pipeline in Wrecker and deploy your code on specific port of your web server.

Some Additional Add-ons:

--> You can expose only specific port from AWS security group as you require.
--> If you want to redirect your EC2 Public DNS to specific domain, Buy one Domain or if you want to use existing domain just change NS ( Nameserver ) of you domain to AWS NS with Route53 hosted zone.
--> Add ElasticIp to your Instance for Static Ip. 
--> And Configure Route53 A record for redirection.
--> You can add SSL with different method here I used Amazon signed certificate from Amazon Certificate Manager.
--> And I used ELB ( Elastic Load Balancer) which will allow you to add Amazon SSL to place in middle as well it will
provide you Health check of Instance.
--> You can add Alias in Route53 to add ELB in middle of redirection.
--> You can also add SSL in your root conf directory.
--> You Can redirect your HTTP traffic to HTTPS by adding some few config content.
--> Here I redirected by adding following Content:

<VirtualHost *:80>
        RewriteEngine On
        RewriteCond %{HTTP:X-Forwarded-Proto} =http
        RewriteRule . https://mydevopsproject.com [L,R=permanent]
</VirtualHost>


* My Domain Url: mydevopsproject.com
* My EC2 where I deployed on specific port like 82: ec2-34-205-219-168.compute-1.amazonaws.com:82 

As AWS sevices are chargeable, Stop when you no longer require.
