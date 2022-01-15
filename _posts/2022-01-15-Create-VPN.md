---
layout: post
title: "Create VPN"
date: 2022-01-15 11:50:00 +0800
---

### Table of Content
* [Step by Step](#step-by-step)
    * [Setup VPN Server](#setup-vpn-server)
    * [Connect to VPN Server](#connect-to-vpn-server)
    * [Configure VPN](#configure-vpn) 
* [Conclusion](#conclusion) 
* [Useful Links](#useful-links)

[VPN(Virtual  Private Network)](https://en.wikipedia.org/wiki/Virtual_private_network) establishes a secure internet connection while you’re using public networks. It encrypts your internet traffic and hides your online identity, which improve the security of your connection. In this tutorial, we’re going to set up VPN using AWS EC2.

## [Step by Step](#step-by-step)

# [Setup VPN Server](#setup-vpn-server)
1. Login to your AWS Management Console and find EC2. In EC2 service, Click **Launch Instance**.
2. In Step 1: Choose an Amazon Machine Image (AMI), click **AWS Marketplace** and search **openvpn**. Find the OpenVPN Access Server and click **Submit**.
![Step1:Choose an Amazon Machine Image(AMI)](/AWS-diary/Image/create-vpn/chooseAMI.png)
3. OpenVPN is a paid commercial server, but this **OpenVPN Access Server** allows 2 devices to connect to VPN for free. If you need more than 2 devices to connect, use other server when you search for **openvpn** in the marketplace. 
Click **Continue**
![Continue](/AWS-diary/Image/create-vpn/OpenVPN-continue.png)
4. Choose your instance. You can choose free tier to prevent costing extra money. Then click **Review and Launch**->**Launch**.
![Choose instance](/AWS-diary/Image/create-vpn/choose-instance.png)
5. Before you launch instance, you have to select an existing key pair or create a new key pair. Key pair allows you to connect to your instance securely. 
Click **Create a new key pair** and type in your Key pair name. Then **Download Key Pair**. Remember where you store the key pair because this is your ONLY chance to download the key pair. Normally it will be safe to store in Disk C. I faced a problem when I stored the key pair in Disk D/Desktop, when I tried to ssh to my instance, it showed access denied because the key pair is too easy to access. However, when I stored in Disk C, the problem resolved.
![Create new key pair](/AWS-diary/Image/create-vpn/create-a-new-key-pair.png)
6. You will have to wait a couple of seconds for the instance to be launched. Once it's done, it will show you Launch Status as below. Click the link below. It will take you to your EC2 instance console.
![Launch Status](/AWS-diary/Image/create-vpn/launch-status.png)

---

# [Connect to VPN Server](#connect-to-vpn-server)
1. Select your OpenVPN instance and Click **Connect**. Or Hover to Instance ID and right click, then choose **Connect**.
![connect instance](/AWS-diary/Image/create-vpn/connect-instance.png)
2. There are several ways you can connect to your instance. In this tutorial, I'm going to show you 'SSH client' method. Copy the command under **Example** section.
![SSH](/AWS-diary/Image/create-vpn/ssh.png)
3. Open your terminal/powershell in your computer, navigate to the folder where you store your key pair(in my case, C:/Users/User).
4. Input the command you've just copied. (ssh -i "key pair name" root@your instance Public DNS)
5. You'll be asked some configuration questions. Just insert 'yes' or Enter until the process end.
![terminal ssh](/AWS-diary/Image/create-vpn/terminal-ssh.png)
6. Re-type the ssh command and change 'root' to 'openvpnas'. I.e. ssh -i "key pair name" openvpnas@your instance Public DNS.
7. Once you've connected successfully, run command ```sudo passwd openvpn``` to change the password. REMEMBER the password as you'll use it later to login to server. You may close your terminal/powershell now.

![reset password](/AWS-diary/Image/create-vpn/reset-password.png)
8. Go back to EC2 console page and click the OpenVPN server instance. Find it's public IPv4 address and click **open address**.
![Open address](/AWS-diary/Image/create-vpn/open-address.png)

---

# [Configure VPN](#configure-vpn) 

1. You'll reach OpenVPN User Page using Public IPv4 address in the instance summary. Scroll down to find Admin button and login as an Admin. 
Username: openvpn
Password: the password you just set up in terminal.
Click **Sign in**->**Agree**.
![Admin login](/AWS-diary/Image/create-vpn/admin-login.png)
2. Once you logged in, click **VPN setting** in the left navigation bar. Scroll down to the 'Routing' section. Enable 'Should client internet traffic be routed through the VPN?'. It allows clients' traffic route through VPN to the internet, which hide your local identity. 
Click **Save settings**.
![routing](/AWS-diary/Image/create-vpn/routing.png)
3. On top of your homepage, click **Update Running Server**.
![update running server](/AWS-diary/Image/create-vpn/update-running-server.png)
4. Login again as a user, you can either:
- Open the public IPv4 address again
- remove /admin/vpn_settings of the url 
5. Download your OpenVPN application. In this case, it's Windows. Click Windows icon and **Save File**. The file is approximately 60mb.
![Download app](/AWS-diary/Image/create-vpn/download-app.png)  
![Save file](/AWS-diary/Image/create-vpn/savefile.png)
6. Once downloaded, execute the file. You'll need to setup your OpenVPN. Click **Next** until you finish.
![setup openvpn](/AWS-diary/Image/create-vpn/setup-openvpn.png)
7. Open the OpenVPN appplication and turn on VPN. For the first time, you'll need to login again, username: openvpn, password: _yourpassword_.
![openvpn](/AWS-diary/Image/create-vpn/openvpn.png)
8. Congratulation! You've successfully connect to the VPN. 
![connect-successful](/AWS-diary/Image/create-vpn/connect-successful.png)

## [Conclusion](#conclusion) 
In this tutorial, setting up OpenVPN server using EC2 instance is demonstrated. It is totally free within free tier and available to 2 clients. You can easily turn on and off the VPN server in **OpenVPN Connect** application in your device and login using username(openvpn) and password.

## [Useful Links](#useful-links)
1. [setup a FREE VPN server in the cloud (AWS)](https://www.youtube.com/watch?v=m-i2JBtG4FE)
2. [How to create a free VPN server on AWS](https://towardsdatascience.com/how-to-create-a-free-vpn-server-on-aws-655ca3b3ff32)
3. [OpenVPN](https://openvpn.net/)