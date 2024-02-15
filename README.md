## Overview
This project aims to host a highly available static website using HTML, CSS, Javascript, Simple Storage Service (S3), Route 53, CloudFront Distribution and Certificates Manager. The primary goal is to achieve a secure, highly available website. I followed a tutorial from Tiny Technical Tutorials. 

### Part 1: Setting up S3 for static website hosting
I followed a tutorial (by GreatStack on youtube) to help jump start the process of building the website using HTML, CSS, and Javascript code. I then took that code and uploaded it to an S3 bucket and configured S3 bucket for public access. When creating an S3 bucket an important stipulation is that the bucket name has to be the same as the domain name that you register. 

### Part 2: Getting a custom domain
I purchased a domain name for use with AWS Route 53 from a third party website. Because of this, I had to create a hosted zone and use the name servers that AWS provided to link to the domain name provided by the website. We then have to create a record in Route53 to route requests to our s3 website when someone goes to our domain. 

### Diagram 1: Progress So Far
![diagram1](https://github.com/sauravnakarmi/AWS-Static-Website/assets/70821330/193d8cb5-a3f7-44b9-8dbd-44473550533e)

### Part 3: Setting Up SSL/HTTPS and Creating a CloudFront Distribution
In order to have a proper certificate for our cloud front distribution we need to be in us-east-1 for our region. To validate our certificate we need to add a CNAME record into our Route 53. The certificate itself cannot be used on the S3 bucket we have created, instead, we need to create a cloud front distribution to attach the certificate to. The origin of our cloud front distribution will be our s3 bucket. We also need to make sure we redirect HTTP to HTTPS, choose a WAF option, add a cname, use our custom SSL certificate that we created, and make sure our root object is set to our index.html page. To properly use our domain name for access to our website we need to update our route 53 record. Instead of pointing to our S3 bucket, our A record needs to point to our cloud front distribution. 

### Diagram 2: Final Infrastructure
![finaldiagram](https://github.com/sauravnakarmi/AWS-Static-Website/assets/70821330/72949cfe-c1d2-450a-b014-361526114fb0)

### Conclusion 
