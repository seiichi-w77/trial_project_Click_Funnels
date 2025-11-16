# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/setting-funnel-as-the-domain-default-page

---

One powerful feature of ClickFunnels is the ability to set a specific funnel as the default page for your domain. This ensures that every visitor is directed to your primary sales pathway right from the start, without any redirect or additional path at the end. By doing so, visitors can enter your funnel directly using your custom domain, providing a seamless experience. This article will guide you through setting a funnel as your domain’s default page.

Requirements

An active ClickFunnels account

A domain verified in the workspace

A funnel created in the workspace

Important:

A domain can only have one root page. If a domain is already in use for a site in the Site & Blog app, it cannot be set as the default domain for a funnel. In this case, the domain will automatically redirect visitors to the site's home page instead.

Set Up Funnel as Domain Default Path

Click on the Funnels menu from the navigation on the left side.

Locate the funnel you wish to load on your domain’s root path and click the Gear ⚙️ icon to access the funnel’s settings.

Select the domain in the Domain field. The selected domain must be different from the one used for your Site.

Change the Funnel Path URL field to just a single / character.

Alternatively, you can view these settings directly inside your funnel. Access the funnel and click the Settings button at the top right corner of the funnel page, and then follow steps 3 and 4 above.

Click Update Funnel to save changes.

Congratulations! The funnel will be displayed whenever someone visits your domain.

Important:

When the domain is visited, the system will redirect visitors to the first page of the funnel and display the page with its unique path. For example: if the domain name is ‘www.example.com’ and the first step of the funnel has the path ‘/home’ then www.example.com will be redirect to www.example.com/home.

How to Prevent Displaying the Page Path of the Domain Default Page

To prevent the domain default funnel page from displaying with its page path, add a “split test” at the top of the funnel step and set the split percentage to 100-0. Splits added to the top of a funnel behave differently than other splits. When a split test is added at the top of the funnel, the pages for the first step on either path are served at the funnel’s root URL.

Navigate to a Funnel and locate the first step of the Funnel.

Click the Three Dot ⋮ icon and choose the Split test page option.


In the prompt, you can create a new page or duplicate the existing one.

A Variation Page will then be added alongside the original page.

Use the Split Test Slider to set the percentage to 100% for the original page on the left and click Apply Changes.

Next, wait a moment and test your domain in a browser. The domain will display the top funnel step without any path (e.g., www.yourdomain.com).

You can learn more about creating and managing split tests in funnel steps in the Funnels - Managing A/B Split Testing in Funnel Steps article.