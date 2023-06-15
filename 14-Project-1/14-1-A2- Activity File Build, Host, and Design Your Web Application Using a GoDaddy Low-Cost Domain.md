# ACTIVITY 14-1: Build, Host, and Design Your Web Application Using an Azure Free Domain

## Overview 
(1) Create an Azure web app.
(2a) Choose a domain with GoDaddy.
(2b) Map your custom domain to Azure's App Service.
(3) Deploy a container on the web app.
(4) Design your custom web application.
(5) Answer review questions.

### Part 1: Create an Azure Web App
- Same as Part 1 of [Azure free domain](14-1A-Build%2C%20Host%2C%20and%20Design%20Your%20Web%20Application%20Using%20an%20Azure%20Free%20Domain.md)

### Part 3: Deploy a Container on the Web App
- Same as Part 2 of [Azure free domain](14-1A-Build%2C%20Host%2C%20and%20Design%20Your%20Web%20Application%20Using%20an%20Azure%20Free%20Domain.md)

### Part 4: Design Your Custom Web Application
- Same as Part 3 of [Azure free domain](14-1A-Build%2C%20Host%2C%20and%20Design%20Your%20Web%20Application%20Using%20an%20Azure%20Free%20Domain.md)

### Part 5: Answer Review Questions
- Same as Part 4 of [Azure free domain](14-1A-Build%2C%20Host%2C%20and%20Design%20Your%20Web%20Application%20Using%20an%20Azure%20Free%20Domain.md)

### Part 2a: Choose a Domain with GoDaddy
In this part, you will select your own unique domain name using GoDaddy. To do so, complete the following steps:

1. Navigate to GoDaddy.com.
2. Pick a website for your cyber-blog, but note the following:
- The 99 cent domains are usually ".club" or ".xyz," and ".info" is $1.99 a year.
- After you pick the domain, the cost may increase after your first year—check carefully for this.
- We recommend choosing a domain such as "bobscyberblog.club," but you can pick any domain that you prefer:
- Refer to the following webpage for tips on picking a domain: How to come up with a good domain name.
- GoDaddy will provide you other domain options if your chosen domain is not available.

3. Once you have chosen an available domain, click "Get It," as the following image shows:
4. Select a duration of one year to get the 99 cent price, then select "Looks Good, Keep Going," as the following image shows:

5. The next page offers add-ons, such as domain protection. These are not required. Select "Continue to cart."

6. The next page should show your cart. Make sure that your total shows correctly (99 cents if you didn't select any add-ons).
- Then click "Ready to Pay," as the following image shows:

7. Create a GoDaddy account, or log in if you already have an account.

8. Follow the steps to complete your payment.


### Part 2b: Map Your Custom Domain to Azure's App Service
In this part, you will point the DNS to Azure's app service. To do so, complete the following steps:
1. Return to the app that you created within Azure App Service.

2. Select "Custom domains" from the left-hand menu, then click "Add custom domain." In the "Custom domain" text box, enter the new domain that you created on GoDaddy, and then click "Validate." The following image shows these steps:


3. After selecting "Validate," the page will confirm whether the hostname is available.
- Select the hostname record type "A Record," and notice the TXT and A data under "Domain ownership," as shown in the following image:
- You will update this data in the GoDaddy DNS record to prove that you own the domain.

4. Return to your GoDaddy.com products page: https://account.godaddy.com/products.
5. On this page, find the domain that you just added (you may have to scroll down), and select "DNS," as the following image shows:
6. Below your existing DNS records, select "ADD," as the following image shows:

7. One at a time, add in the two "Domain ownership" records (TXT and A), that you saw in Step 3, and click "Save" after each one.
- The TTL can stay at 1 hour.
- The following image shows this step:

8. Once you've added both records, they should appear at the bottom of your DNS page, as the following image shows:

9. Delete the A record that is labeled as "Parked"

10. Return to Azure, and repeat Step 2. After clicking "Validate," green check marks should appear next to "Hostname availability" and "Domain ownership."

11. Select "Add custom domain," as the following image shows:

12. After a minute, your new domain will appear under "Assigned Custom Domains," as the following image shows:

- If the domain doesn't appear, refresh your page and clear your cache.

Congratulations! You now own your own unique domain, accessible on the internet!

#### Checkpoint 
Before continuing, make sure that you have completed the following critical tasks:
- Your Azure web app has been created.
- A unique IP has been assigned to your web app.
- You have selected and created your own unique domain with GoDaddy.
- You have mapped your domain to Azure's app service.# 14-1:Building and Hosting the Web App_ed