# Tutorial: Deploy a Self-Hosted Ghost Blog and Newsletter on PikaPods

### Ghost as an alternative to WordPress and Substack

The [Ghost](https://ghost.org/) blogging and newsletter platform has continued to mature since its initial release in 2013. It is less bloated than WordPress for a small website, and more customizable than Substack or Beehiiv for an email newsletter.

When I decided to migrate a small Substack newsletter to Ghost, I initially considered their official managed [Ghost(Pro)](https://ghost.org/pricing/) hosting solution. But at $15 USD per month, the price felt too high for my small side project. 

Investigating options for self-hosting, I first considered [Digital Ocean](https://marketplace.digitalocean.com/apps/ghost) and [AWS Lightsail](https://docs.aws.amazon.com/lightsail/latest/userguide/amazon-lightsail-quick-start-guide-ghost.html), both of which offer handy pre-configured Ghost server images. But the cost for a deployment meeting the minimum requirements on either platform still sat at around $12 USD per month. That's not much cheaper than Ghost(Pro), especially considering the extra work that would be required to keep the software stack up-to-date over time.

### PikaPods to the rescue?
Another intriguing option presented itself: [PikaPods](https://www.pikapods.com/). This cloud hosting service offers fully-managed open source containerized apps, at very affordable prices. The cost for hosting a basic Ghost app on PikaPods is currently around $2.50 USD per month. It only takes a few minutes to get a "Pod" instance up and running on a public subdomain, and a Pod can be easily resized at any time to increase the memory, storage space, and the number of CPUs as required.

Conveniently, Pods are fully managed, meaning that internal software stack updates are automatically tested and installed as they become available, with no action required from the Pod administrator. Thankfully, this doesn't mean a Pod is a total black box: Pod administrators can still directly access the Ghost MySQL database through a browser interface, for example, and are able to view internal logs and set numerous configuration values through environment variables exposed in the interface. 

All considered, a PikaPods deployment seemed like an ideal balance of cost, convenience and flexibility for my side project, so I decided to give it a go. The results were very positive.

&nbsp;

# Step-by-step Tutorial

The process I used to deploy a fully-functional Ghost website and newsletter on PikaPods was quite straightforward. It did not involve any coding, though there were numerous configuration steps spread across PikaPods, Cloudflare, Mailgun and my domain registrar. Individual parts of this process are well-documented in various places online, but I thought it would be valuable to collect all the steps into a single detailed tutorial.


&nbsp;

### Part 1: Deploy an instance of Ghost on PikaPods
   
New PikaPods users are given a $5 balance, which is enough test out a minimal Ghost deployment for about two months. Only after that time passes is credit card payment information required if you wish to keep the Pod running.

**1.1** Visit https://www.pikapods.com/register and enter your first name, email address, and a secure password. Keep a personal record of this information somewhere safe, such as your password manager. Submit the form, then click the confirmation link in the email that arrives. 

<img alt="Register a user on PikaPods" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t1.png" width="75%" />

**1.2** Visit https://www.pikapods.com/login and log in using the email address and password you just registered.

<img alt="Log in to PikaPods" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t2.png" width="75% " />

**1.3** Click the *Add Pod* button. Under *Choose App* choose *Ghost*. Under *Pod Name* type a short description of your Pod. Then choose a Pod region of *EU* or *US* depending on the expected geographic location of your blog visitors (or your personal preferences). 

<img alt="Add a Pod" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t3.png" width="75%" />

**1.4** Click on *Resources* in the left menu, and review the default values for *CPU Cores*, *Memory*, and *Storage*, and also confirm the *Monthly Cost*. You can always change these settings in the future if your Pod requires more resources. 

<img alt="Check Pod resources" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t4.png" width="75%" />

**1.5** Click the *Add Pod* button at the lower right to create your Ghost Pod. After a few moments, the control panel for your Pod will appear. This box summarizes information about your Pod, and provides access to numerous configuration options under the gear icon and the More button. We will make use of some of those configurations later in this tutorial.

<img alt="Pod control panel" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t5.png" width="75%" />

**1.6** Click on the green link to the right of *Domain* to open your new Ghost blog in a separate browser tab. It's alive! Not bad for a few minutes of effort. (You will notice that, for now, the blog lives on a nonsensical subdomain of *pikapod.net*, in my case, *hypnotic-kestrel.pikapod.net*. Later in this tutorial, we will switch this to a personalized domain.)

<img alt="Viewing the Ghost blog" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t6.png" width="60%" border="1" />

**1.7** Return to your PikaPods dashboard tab in your browser. Click on the link inside the orange box visible inside your Pod's control panel.

<img alt="Link to finalize Ghost setup" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t7.png" width="70%" />
     
**1.8** This URL, which you can reach any time by simply adding */ghost* to the end of your blog's domain, is where the *Ghost Admin* tools for your blog will live. But first you'll need to create your Ghost account. To do that, enter your *Site title*, your *Full name*, your *Email address*, along with a secure password. Your site's title and the admin user details can be changed later, so there's no need to agonize too much here. But make sure once again to keep a personal record of this information somewhere safe, such as your password manager. Then click the *Create account & start publishing* button.

<img alt="Link to finalize Ghost setup" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t8.png" width="75%" />

**1.9** Once you are logged in, you might want to poke around to familiarize yourself with the Ghost Admin interface. Later in the tutorial I will describe steps to activate and style a theme, and to optionally import posts from another site. But extensive documentation about the Ghost editor is available in the [Ghost Manual](https://ghost.org/help/using-the-editor/) and I won't try to replicate it here. 

<img alt="Ghost Admin default view" src="https://raw.githubusercontent.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/refs/heads/main/images/t9.png" width="50%" />


&nbsp;

### Part 2: Configure a custom domain

**2.1**

&nbsp;

### Part 3: Activate and style a theme

**3.1**

&nbsp;

### Part 4: Configure Mailgun to send emails

**4.1**

&nbsp;

### Part 5: Migrate posts from Substack or WordPress (Optional)

**5.1**

&nbsp;

### Part 6: Migrate newsletter subscribers from Substack (Optional)

**6.1**

