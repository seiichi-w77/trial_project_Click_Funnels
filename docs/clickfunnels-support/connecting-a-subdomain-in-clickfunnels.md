# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/connecting-a-subdomain-in-clickfunnels

---

You might already have a website on your main domain or use a domain registered outside of ClickFunnels, but still want to run funnels, blogs, or campaigns on a separate web address. ClickFunnels makes it easy to connect a subdomain using a simple automated or manual setup process in just a few simple steps. In this article, you'll learn how to connect a subdomain in ClickFunnels using both the automated setup and manual setup methods.


Requirements

An active ClickFunnels account

A domain purchased from a third-party registrar (e.g., GoDaddy, Cloudflare, Namecheap, etc.)

Warning:

We currently do not support Internationalized Domain Names (IDNs). Special characters are letters that are not in the English alphabet. Some examples of special characters are æ, ø, å, ö, ä, ü and é.

Domain names with trademarked phrases cannot be added or used in ClickFunnels. Click here to view restricted phrase list.

What is a Subdomain

A subdomain is a part of your main domain name that helps you organize or separate content on your website. It acts like a separate area of your site but is still connected to your main domain.

Example:

Main domain: yourdomain.com

Subdomain: blog.yourdomain.com, webinar.yourdomain.com, or shop.yourdomain.com

You may have already come across subdomains in real life, such as:

support.google.com for Google’s help center

news.bbc.co.uk for news content

store.nike.com for Nike’s online shop

These examples show how subdomains help create dedicated spaces for specific content or purposes without interfering with the main website.

When to Consider Using a Subdomain

You may want to use a subdomain in ClickFunnels for various reasons. Here are some scenarios where using a subdomain makes sense:

You already have a website on your root domain and want to keep it separate from your funnel pages.

You want to host a blog on a dedicated space like blog.yourdomain.com.

You’re running a webinar series and want a branded link, such as webinar.yourdomain.com.

You’re promoting a special campaign or limited-time offer and want it to be separate from your main site.

You want to build a membership area or customer portal under a unique URL, such as members.yourdomain.com.

You want to keep your funnel content distinct from your corporate or brand website for better organization and clarity.

Step 1 – Adding the Subdomain in ClickFunnels

To begin, you'll first add your subdomain to ClickFunnels by following the steps outlined above:

Start by logging into your ClickFunnels workspace.

From the left sidebar menu, click Workspace Settings and then select Domains.


Click Add Domain

In the open prompt, click + Add an Existing Domain..

In the open prompt, enter your subdomain name (e.g., blog.yourdomain.com) and click Continue.


Select Subdomain if it’s not already selected.

Important:

Do not use www when connecting a subdomain. The www prefix is itself a subdomain (e.g., www.example.com), and should not be used in this process.

Click “Continue with …” to proceed to the DNS setup.

At this stage, the subdomain has been added to your workspace, but the integration is incomplete. To complete the integration, follow Step 2 below.

Step 2: Setting Up the Subdomain

After adding a subdomain, you need to pick a DNS setup method.

Automated Method (Recommended if your domain provider is supported by automated setup)

Manual Method(If automated setup is not supported)

To complete the integration, you must link your domain registrar or DNS provider account (e.g., GoDaddy, Cloudflare, NameCheap, Bluehost, etc.) with ClickFunnels. Follow either the automated or manual setup instructions below to finish connecting your subdomain to ClickFunnels.

Automated Method
Manual Method
Setting Up the Forwarding Rule

Upon completing the integration of your subdomain with ClickFunnels, creating a forwarding rule within your domain's DNS provider may be necessary. This will ensure that any visitors accessing the subdomain with the "HTTP://" prefix (e.g., http://blog.yourdomain.com) are redirected to https://blog.yourdomain.com.

Below is an example of a forwarding rule that can be added to Cloudflare.

Check out our detailed guide about adding forwarding rules in different domain DNS providers in the article, Adding Domain Forwarding Rules.

Connecting the Subdomain to a Workspace Site

After successfully integrating your subdomain with your workspace, follow these steps to connect it to your site:

From your workspace, click on the Site & Blog app in the left-hand menu.

Select Site Settings.

Scroll to the Site Domain section and choose the subdomain you wish to use for your site in the Domain field.

Click the Update site button to save your changes.

Important:

The domain connected to the Site & Blog app is used for Courses, Store, Blog, Customer Center, Landing Pages, and Community. These features must share the same domain connected to the Site & Blog settings.

Connecting a Subdomain to a Funnel

Click on Funnels from the left navigation menu.

Identify a funnel you wish to associate with your subdomain and click the Gear ⚙️ icon to access the funnel settings.

In the Domain field, select the desired subdomain from the dropdown menu.

Enter the desired path in the Funnel Path URL field, such as /home, /page, or /root. To set this funnel as the subdomain’s default page, enter a single / character.

💡 Learn more about setting a funnel as a domain default page in the article, Setting a Funnel as the Domain Default Page.

Click Update Funnel to save changes.

Congratulations! Your subdomain is now connected to the funnel. When the subdomain is accessed, the first page of your funnel will be displayed.

Subdomain FAQs
How many subdomains can I connect in ClickFunnels?

There is no limit. You can connect as many subdomains as you need to your ClickFunnels workspace.

Can I connect a subdomain if my root domain is already connected to another platform?
Do I need to pay to connect a subdomain?
Where can I use a subdomain in ClickFunnels?
I already connected the root domain. Can I still add a subdomain?
Will my subdomain work with SSL (HTTPS)?