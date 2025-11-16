# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/how-to-set-up-upgrade-and-downgrade-options-for-subscription-products-1

---

The upgrade and downgrade feature allows customers to easily switch between subscription plans whenever they need to. It’s a simple way to offer flexibility and ensure your products meet their changing needs. In this article, you’ll learn how to set up this feature for your subscription products, step by step, so your customers can move between plans effortlessly. 

Requirements

An active ClickFunnels account

A subscription product created in the Products section

A funnel created in your workspace

Payments AI Configured Account

Understanding the Upgrade and Downgrade Feature

The upgrade and downgrade feature is designed to give customers the flexibility to move between subscription plans as their needs change. This functionality is especially useful for businesses offering tiered plans, such as basic, standard, and premium subscriptions.

For example, imagine you run an online fitness platform with three subscription tiers:

Basic Plan ($29/month): Access to on-demand videos.

Standard Plan ($79/month): Includes everything in the Basic Plan plus live classes.

Premium Plan ($129/month): Adds personalized coaching to the Standard Plan features.

If a customer starts with the Basic Plan and later decides they want live classes, they can upgrade to the Standard Plan. Similarly, a Premium Plan customer who no longer needs coaching can downgrade to the Standard Plan.

This feature simplifies the process for customers by allowing them to adjust their plans directly through the checkout process, without needing to contact support or cancel their subscription.

Important

The feature only applies to subscription products. It doesn’t work for one-time purchases.

Plan changes can only occur between predefined options (e.g., a customer can’t upgrade to a completely different product).

By offering this level of flexibility, you create a better experience for customers and make it easier to retain them over the long term.

Setting Up Products for Upgrade/ Downgrade

Navigate to Products in the side navigation menu, then select All Products.

Click the Create Product button.

In the popup, select Digital or Physical as the product type, then enter the Product Name and Description.

Click Create Product to confirm.

Select Subscription as the Price Type and set the price details. Click Set Price to save.

Scroll to the Variants section, check the box for “This product has multiple options.

In the Option field, select an existing option or click Add new option to create a new option, such as Tier.

In the Values fields, enter each option value, such as Essential Plan, Growth Plan, and Elite Plan.

Click Done once the tiers are set up.

Scroll to the bottom of the page and click Update Product to save your changes. The page will reload to show the updated product settings.

Scroll back to the Variants section, where the newly created tiers will appear. Click Edit Variants to customize each plan.

Configuring Each Variant

After setting up your variants, follow these steps for each one to enable pricing overrides and plan changes:

In the Pricing section, click Add Override Price.

Select Subscription as the price type.

Set the Amount per payment to reflect the price for this variant (e.g., $29 for a subscription).

Choose how often the customer will be charged in the Charge customer every dropdown (e.g., monthly).

Check the boxes for Customer can upgrade and Customer can downgrade to enable plan changes.

Click Save to confirm the pricing details.

For more detailed guidance on configuring pricing, refer to the How to Add and Manage Pricing article.

Scroll to the Upgrades/Downgrades section and click Add Upgrade/Downgrade.

In the popup, select either Upgrade or Downgrade, depending on the configuration.

For example, let’s configure an Upgrade for the Essential Plan:   

Select Upgrade at the top of the popup.

Under Upgrade from, confirm the current plan’s pricing (e.g., $29/month).

Under Upgrade to, select the Growth Plan from the dropdown.

Click Save to apply the changes.

Repeat these steps for all variants:

For the Growth Plan, configure both an upgrade to the Elite Plan and a downgrade to the Essential Plan.

For the Elite Plan, configure a downgrade to the Growth Plan.

Save your changes after configuring each plan option.

Repeat these steps for all remaining variants.

Double-check that all pricing and plan changes are accurate to avoid any confusion for your customers.

Adding Products to a Funnel

After configuring your subscription products with upgrade and downgrade options, the next step is to attach them to a funnel. Follow these steps to integrate your product into a funnel and enable the upgrade/downgrade functionality:

Navigate to Funnels in the side navigation menu.

Select the funnel you want to attach the product to and open it in the funnel workflow editor.

Locate the page where you want to add the product (e.g., the checkout page), and click the three dots next to the page name.

Ensure this page includes a Checkout element to support product purchases. To learn more about the Checkout element, refer to the Checkout: Enable Users to Complete their Purchase article.

Click Add Products from the dropdown menu. 

Click the Add Product button to open a window displaying a list of all existing products.

Hover over the desired product and click Select Product.

Once the product is added, click the gear ⚙️ icon next to your product.

Check the boxes for Allow contacts to upgrade existing orders? and Allow contacts to downgrade existing orders?. This step ensures that customers can modify their subscriptions directly through the funnel.

Click on Availability and Prices and ensure all your configured prices are selected and visible.

Finally, click Update Included Product to save your changes and apply the settings.

Testing the Setup

After integrating your subscription product into a funnel, it’s important to test the setup to ensure everything is functioning as expected.

Enable Test Mode in Funnel Settings and Ensure the Credit Card payment method type is selected. If the funnel is in Live Mode, switch it to Test Mode to prevent real purchases during testing. 

Copy the funnel URL from the top center of the funnel workflow editor and open it in a new browser tab. Navigate through the funnel until you reach the checkout page.

Use a test email address to simulate a purchase. Select one of your configured subscription plans and proceed through the checkout process using the following test credit card details:

Card Number: 4111-1111-1111-1111

CVV: Any 3-digit number

Expiry Date: Any future date

Complete the purchase and confirm that you’re redirected to the appropriate confirmation page. Verify that the receipt or order summary accurately reflects the selected subscription plan.

Return to the funnel URL and enter the same test email address used during the initial purchase. The Checkout element should recognize you as an existing customer and offer options to upgrade or downgrade your subscription.

Select a new plan to test the upgrade or downgrade functionality. In the Manage Subscriptions section, use the dropdown under your active order to choose a new plan (e.g., upgrade to Premium Plan or downgrade to Essential Plan). Click Update My Order! to complete the process. 

FAQ
Why aren’t upgrades or downgrades showing on the checkout page?

Upgrades and downgrades may not appear if the necessary options haven’t been enabled in your funnel product settings. To fix this, go to your funnel, open the product settings, and make sure the options for Allow contacts to upgrade existing orders? and Allow contacts to downgrade existing orders? are both checked. Save the changes and test again.

Why are the prices for my variants missing or incorrect?
Why doesn’t Test Mode recognize an existing customer?
Why aren’t plan upgrades or downgrades applying correctly?