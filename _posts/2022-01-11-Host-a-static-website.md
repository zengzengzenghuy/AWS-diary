---
layout: post
title:  "Host a static website"
date:   2022-01-11 11:50:00 +0800
---
### Table of Content
* [What is AWS Amplify?](#https://zengzengzenghuy.github.io/AWS-diary/2022/01/11/Host-a-static-website.html#What-is-AWS-Amplify?)
* IS AWS Amplify free?(# Is AWS Amplify free?)
* Step by Step(# Step by Step)
* [Conclusion](#https://zengzengzenghuy.github.io/AWS-diary/2022/01/11/Host-a-static-website.html#Conlusion)

Hosting your static website has never been easier using the AWS platform. In this article, you're going to understand how to use **AWS Simplify** to host your static website within minutes.

## [What is AWS Amplify?](#What-is-AWS-Amplify?)
[AWS Amplify](https://aws.amazon.com/amplify/?nc=sn&loc=1) allows you to build, deploy and host your static website and mobile app with just a few click. You can connect your source code from Git repository or upgrade file to Amplify console to host your website or app.

## Is AWS Amplify free?
**If you are under Free Tier condition**, you get the following benefits for **FREE** :
- 1000 build minutes per months
- 5GB stored per month
- 15GB served per month
> The free tier expires at the end of your 12 month AWS Free Tier term.

**If not**, the price follows [Pay-as-you-go](https://aws.amazon.com/amplify/pricing/?nc=sn&loc=4) rule:
- $0.01 per build minute
- $0.023 per GB stored per month
- $0.15 per GB served

## Step by Step
1. Log in to AWS Management Console
2. Search **AWS Amplify**
3. After entering the service, scroll to the bottom and click **Get Started!** under Amplify Hosting 
![AWS Amplify](/AWS-diary/Image/Host-a-static-website/AWS-Amplify.png)
4. You may choose to upload your code through different ways. I'm going to show you the two most popular ways: Github, and Deploy without Git Provider.
    1. Github
        1. Choose **Github** and **Continue**
        ![Connect to Github](/AWS-diary/Image/Host-a-static-website/Choose-source-code.png)
        2. You'll need to authorize AWS to access your Github account if it's your first time using it. Click **Authorize aws-amplify-console**
        ![Authorize AWS Amplify Access](/AWS-diary/Image/Host-a-static-website/Authorize.png)
        3. Choose the repository where your source code is located and the branch. Click **Next**.
        ![Add repository branch](/AWS-diary/Image/Host-a-static-website/Add-repo-branch.png)
        4. Enter your App name and tick **Allow AWS Amplify to automatically deploy all files hosted in your project root directory.** and continue.
        ![Configure build settings](/AWS-diary/Image/Host-a-static-website/Configure-build-settings.png)
        5. You can review all the details before deploying. Once the information is correct, click **Save and deploy**.
        ![Review](/AWS-diary/Image/Host-a-static-website/Review.png)
        6. Once all the four sections turn into green tick, your website is up and ready!
        ![Done page](/AWS-diary/Image/Host-a-static-website/Done1.png)
    2. Deploy without Git Provider
        1. Choose **Deploy without Git Provider** in step 4.1.1.
        2. Enter your App name and Environment name. Upload your source code using either:
            - Drag and drop (Upload from local)
            - Amazon S3 (Choose S3 bucket where your source code is stored)
            - Any URL (Upload URL where your source code is located)
        To simplify the demonstration, I will choose **Drag and drop**
        ![Start a manual deployment](/AWS-diary/Image/Host-a-static-website/Start-a-manual-deployment.png)
        3. Your site is now up and ready!
        ![Done-2 page](/AWS-diary/Image/Host-a-static-website/Done2.png)
 5. (Optional) Add a domain name

    Since the default domain name looks like https://dev.xxxxxxxxxx.amplifyapp.com, you may need to add a domain name to your website so that people can find your website easier.

    **If you already have your own domain name for the website:**
    1. Go to **App settings** and Click **Domain management**, click **Add domain** at the top right corner.
    ![Domain management](/AWS-diary/Image/Host-a-static-website/Domain-management.png)
    2. Enter your domain name and Click **Configure domain**. Add Subdomains if you want people to search for your website using subdomain name. Tick **Setup redirect from (Domain name) to (Subdomain name)** at the bottom of the section. Click **Save**.
    
    ![Add domain](/AWS-diary/Image/Host-a-static-website/Add-domain.png)
    Reference:[Add a custom domain managed by Amazon Route 53](https://docs.aws.amazon.com/amplify/latest/userguide/to-add-a-custom-domain-managed-by-amazon-route-53.html)


    **If you do not have a domain name**

    You can create a domain name using [AWS Route 53](https://aws.amazon.com/getting-started/hands-on/get-a-domain/) (A DNS service)
    > Domains are not part of the free tier so you will be charged for any domain you register.
6. （Optional) Add a SSL certificate

    SSL(Secure Socekt Layer) acts as a protect layer to secure the internet traffic to your website, preventing criminals from reading and modifying any information transferred.  It uses encryption algorithms to scramble data in transit, preventing hackers from reading it as it is sent over the connection.

    You can get a SSL certificate from **AWS Certificate Manager**. The feel is only $0.75 for each certificate issued and it lasts for one year.

    Check out [How do you get an SSL certificate with AWS](https://www.freecodecamp.org/news/a-beginners-guide-on-how-to-host-a-static-site-with-aws/) for step-by-step guidance.
7. Congratulation, your website is now secure and ready to go!

## [Conclusion](#Conclusion)
In this tutorial, an easy way to host a static website using AWS Amplify is demonstrated. It is almost free (may cost a little extra money if you wish to add domain and SSL certificate).

There are other ways to create and host a static website on AWS platform. Check the the links below for more information.

#### Useful Links
1. [Deploy files stored on Amazon S3, Dropbox, or your Desktop to the AWS Amplify Console](https://aws.amazon.com/blogs/mobile/deploy-files-s3-dropbox-amplify-console/)
2. [Host website with DNS, s3 bucket, SSL, and Cloudfront](https://www.freecodecamp.org/news/a-beginners-guide-on-how-to-host-a-static-site-with-aws/)
3. [Configuring a static website using a custom domain registered with Route 53](https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html)
4. [How to Host a Website on S3 Without Getting Lost in the Sea](https://medium.com/@kyle.galbraith/how-to-host-a-website-on-s3-without-getting-lost-in-the-sea-e2b82aa6cd38)
5. [Host a Static Website with AWS Amplify](https://aws.amazon.com/getting-started/hands-on/host-static-website/)
