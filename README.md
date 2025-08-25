# Tutorial: Deploy a Self-Hosted Ghost Blog and Newsletter on PikaPods

### Ghost versus WordPress and Substack

The Ghost blogging and newsletter platform has continued to mature since its initial release in 2013. It is far less bloated than WordPress for a small website, and it is more customizable than Substack or Beehiiv for an email newsletter.

When I was looking to migrate a small Substack newsletter to Ghost, I initially considered their official managed Ghost(Pro) hosting. But at $15 USD per month, the price felt too high for my free side project. 

Investigating options for self-hosting, I first considered Digital Ocean and AWS Lightsail, both of which offer handy pre-configured Ghost server images. But the cost for a deployment meeting the minimum requirements on either platform still sat at around $12 USD per month. That's not much cheaper than Ghost(Pro), and a heck of a lot more work to maintain over time with the inevitable upgrades that will be required to keep the software stack up-to-date.

### PikaPods to the rescue?
Another intriguing option presented itself: PikaPods. This cloud hosting service offers fully-managed open source containerized apps, at very affordable prices. The cost for hosting a Ghost app on PikaPods is currently around $2.50 USD per month. It only takes a few minutes to get a "Pod" instance up and running on a public subdomain, and a Pod can be easily resized at any time to adjust the server memory, storage and CPUs (with the monthly price increasing proportionately, of course).

Conveniently, Pods are fully managed, meaning that internal software stack updates are automatically tested and installed as they become available, with no intervention required from the Pod owner. Thankfully, this doesn't mean a Pod is a total black box: Pod owners can still directly access the MySQL database through a browser interface, for example, and are able to view internal logs and set numerous configuration values through env variables exposed in their configuration tools. 

All in all, a PikaPods deployment felt like an ideal balance of cost, convenience and flexibility for my side project, so I decided to give it a go. The results were very positive.

# Step-by-step Tutorial
The process of deploying a fully-functional Ghost website and newsletter on PikaPods was quite straightforward. It involved no coding, though there were numerous configuration steps spread across multiple tools and platforms. Individual parts of the process are well documented in various places online, but I thought it would be worth documenting everything in a single tutorial.

### Step 1: Deploy an instance of Ghost on PikaPods
Account deployment and account creation on PikaPods is very simple. New users are given a $5 balance, which is enough to test a Ghost deployment for about two months. Only after that time passes is credit card payment information required.

1. Visit https://www.pikapods.com/register and enter your first name, email address, and a secure password. Submit the form and click the confirmation link in the email that arrives.
   
<img alt="Register a user on PikaPods" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t1.png" width="75%" />



3. Log in to PikaPods with the email and password you just registered.

<img alt="Log in to PikaPods" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t2.png" width="75% "/>



5. Click the Add Pod button. Under Choose App type Ghost and press enter. Under Pod Name type a short description of your Pod. Then choose a Pod region of EU or US depending on the physical location of your blog visitors, or your personal preference.

   <img alt="Add a Pod" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t3.png" width="75%" />



7. Click on Resources in the left menu, and review the default values for CPU Cores, Memory, and Storage, and also review the Monthly Cost value. You can always adjust these settings in the future if your Pod requires more resources.

   <img alt="Check Pod resources" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t4.png" width="75%" />



9. Click the Add Pod button to create your Ghost Pod. After a few moments, the control panel for your Pod will appear. This box summarizes information about your Pod, and provides access to numerous configurable options under the gear icon and the More button. We will update some of those configurations later.

   <img alt="Pod control panel" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t5.png" width="75%" />



10. Click on the green link to the right of Domain to open your new Ghost blog in a separate browser tab. It's alive! Not bad for a few minutes of clicking. (You will notice that, for now, the blog lives on a nonsensical subdomain of pikapod.net, in my case, hypnotic-kestrel.pikapod.net. Later in this tutorial, we will switch this to a personalized domain instead.)

   <img alt="Viewing the Ghost blog" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t6.png" width="75%" />



11. Return to your PikaPods dashboard tab. Click on the link inside the orange box visible inside your Pod's control panel.

   <img alt="Link to finalize Ghost setup" src="https://github.com/garyesmith/tutorial-deploy-self-hosted-ghost-on-pikapods/blob/main/images/t7.png" width="75%" />



12. This URL, which you can reach any time by simply adding /ghost to the end of your blog's domain, is where the Ghost Admin tools for your blog will live, and where you will routinely configure your site and create content. But before you can do that, you'll need to create your Ghost account.


15. Test 

### Step 2: Configure a custom domain


### Step 3: Activate and style a theme


### Step 4: Configure Mailgun to send emails


### Step 5: Migrate posts from Substack or WordPress (Optional)


### Step 6: Migrate newsletter subscribers from Substack (Optional)



