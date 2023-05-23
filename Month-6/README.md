# Materials for Month 6

Sprint 3 starts in Month 6 and it is the most hands on part of the Foundations training. For many it will be uncharted territory as there will be lots to learn and execute as quickly as possible. Lots of Linux-based tasks, software installation and configuration. Hopefully these materials will be useful to you and will help you get up to speed very quickly. This is not meant to be a replacement to the materials already provided on the intranet but to augument it and possibly cover areas that need more attention. If there are areas you need me to cover more, you can reach out to me.
Quick Links
1. Node.js
2. SSH
3. Load balancer
4. HTTPS/SSL

## JavaScript
What is Node.js? Unlike other general purpose programming languages, Javascript was first developed as a special purpose language for web browsers. So it only ran in web browsers for a while. Node.js was then developed to be a runtime environment for Javascript which allows you to write and run Javascript outside a browser like other languages, in a termi example. Node.js provided the platform for Javascript to be used as a backend language and even write commandline scripts.
More [here.](https://www.educative.io/blog/what-is-nodejs)

## SSH
What is SSH? SSH is a short form for Secure Shell, just as 'bash' is short for Bourne Again Shell. A shell is terminal-based program that allows you to give direct instructions as well as run precoded instructions written in a script. Simply put, it conveys your instructions to the kernel. More on that [here.](https://www.geeksforgeeks.org/what-is-terminal-console-shell-and-kernel/)

ssh enables you to securly execute commands and programs in a computer that is physically out of your reach. Your webserver is most likely in another country on another continent. SSH helps you connect to its terminal so you can run scripts, deploy programs and so on. Most of what you need to know about ssh is provided in the material of the task. There was however an issue where ssh keys were missing from sandbox terminals. [Follow this guide if you ever run into such an issue.](https://www.baeldung.com/linux/copy-ssh-keys)

## Load Balancer
* How to configure web-02 to be like web-01:
1. Use 4-not_found_page_404 script from task 4 in [this project.](https://intranet.alxswe.com/projects/266)
2. In your terminal, go into the appropriate repo using cd. The filepath should be alx-system_engineering-devops/0x0C-web_server
3. Copy it using scp command as follows:
```
scp 4-not_found_page_404 ubuntu@your_web-02_server_ip:~
```
Note that 'your_web-02_server_ip' is just a placeholder name. Use your correct web-02 server IP.
4. Now ssh into web-02 and run the script. If done correctly, web-02 nginx will now be configured just like web-01.
5. Exit by typing 'exit' or pressing Ctrl + D. Now cd back into the task folder '0x0F-load_balancer'. Don't forget to create a readme file.

After you do this, you write another script to configure a custom header in nginx in both web-01 and web-02
1. Create the 0-custom_http_response_header script in the task folder '0x0F-load_balancer'.
2. Use scp to copy this script to both web-01 and web-02 servers
```
scp 0-custom_http_response_header ubuntu@your_web-01_server_ip:~
```
```
scp 0-custom_http_response_header ubuntu@your_web-02_server_ip:~
```
3. ssh into web-01, run the script. Exit back to your terminal.
4. ssh into web-02, run the script. Exit back to your terminal.
5. Test your configuration using the example shown in the task.

* How to install HAProxy:
1. Write a script to install and configure HAProxy with the specs given in the task. Follow the task material for guidelines.
2. Using what you have learnt above use scp to copy the script '1-install_load_balancer' to your load balancer
```
scp 1-install_load_balancer ubuntu@your_lb-01_server_ip:~
```
3. ssh into your load balancer and run the script.
4. Exit the ssh and test using the example shown in the task.
5. Always take note of the terminal prompt in the examples. Some tests are run on the server itself, others are run from your terminal.

## Configure Your Domain Zone on get.tech
Configuring your domain zone to point your subdomain to your load balancer is easy.
You should have your domain name by now.
1. Got to get.tech
2. Login to your account
![login page](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/2ae345bc-71b6-41bb-83c9-ccdb624a6f96)
3. When logged in, at the top right hand corner, click on account.
![acount](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/5ebfa10d-450b-44a3-95ef-bb88a22e543d)
4. The account management page will appear. In the 'Jump to Domain' window, type your domain name and click on the '>>' button.
![jump to domain](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/ca42ac75-b097-4893-8293-0b8c0d949aa1)
5. A new page will appear. Scroll to the bottom of the page or click on 'DNS Management' on the side menu. Then click on 'Manage DNS'
![manage dns](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/adb78a7a-24af-4829-bd45-8994a56f98a0)
6. A new window will open. This is your domain zone. All you are required to do here is to create A records according to how they are specified in the tasks. Click on 'Add A record'.
![domain zone](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/d131fb25-a566-415d-b852-2973d065d722)
7. An A record page will appear. In 'Host Name', type 'www'. In 'Destination IPv4 address' type your lb-01 IP address. Click 'Add record'.
![a record page](https://github.com/Innocentsax/ALX-RESOURCES_FROM_BEGINNER_TO_ADVANCE/assets/23355078/05251d0f-7760-44d1-b348-22dd43c1fc06)