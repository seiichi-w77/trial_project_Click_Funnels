# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/setting-up-tax-collection-sales-tax-vat-or-gst-in-clickfunnels-products-1

---

Sales tax is a government-imposed fee on the sale of goods and services, calculated as a percentage of the selling price. In different regions, this tax may be referred to as VAT (Value Added Tax) or GST (Goods and Services Tax). ClickFunnels integrates with payment processors like Stripe and Payments AI, which can handle tax calculations based on your customer's billing address and product type. In this article, you'll learn what sales tax is, why it's important to collect it, and how to enable tax collection in your ClickFunnels checkout.



Requirements

An active ClickFunnels account

A product created in the products menu

A payment processor (e.g., Payments AI, Stripe) connected to the workspace

Important:

ClickFunnels does not offer advice or guidance on whether you should collect sales tax for your business or product. It is recommended to seek assistance from a qualified tax expert or advisor to ensure compliance with your tax obligations.

What is Sales Tax

Sales Tax is a consumption-based tax applied to the sale of goods and services and is usually collected at the point of sale. In the United States, sales tax is determined at the state and local levels, which means rates and tax rules vary significantly depending on the buyer’s location. For example, a product sold in California may have a combined state and local sales tax rate of around 7.25%, while in Delaware, no sales tax is collected at all.

In other countries, similar taxes go by different names. The European Union and the UK use a Value Added Tax (VAT) system, which is typically included in the price of a product and applied at each stage of production and distribution. In Canada, Australia, and parts of Asia-Pacific, the tax is called Goods and Services Tax (GST), which functions similarly to VAT but may vary in rate and scope. For example, Canada's federal GST is 5%, but provinces may apply additional taxes on top.

When collecting these taxes, businesses need to consider the customer’s location, the product or service type, and whether the business is registered to collect taxes in specific regions (commonly referred to as having a tax nexus). Since tax laws can be complex and vary widely by jurisdiction, it is highly recommended to consult a qualified accountant or tax advisor to ensure full compliance with applicable regulations.

How to Collect Sales Tax in ClickFunnels Checkout

There are two main ways to collect tax in ClickFunnels:

Option 1: Manual (Include Tax in Product Price)

If you know your applicable tax rate, you can include it directly in your product price.

Example:
If your product is priced at $100 and your country's tax rate is 12%, you can set the product price to $112. You will then be responsible for calculating and reporting the tax portion of your earnings.

This method is straightforward but requires manual tracking, reporting, and tax filing. Your payment processor won’t provide automated reports or breakdowns.

Option 2: Automatic Tax Calculation

ClickFunnels supports automatic tax calculation through Payments AI and Stripe Tax. These systems detect the customer’s billing location and apply the correct tax rate in real time based on your product's assigned tax category.

Example:
Suppose you sell a $100 digital product to a customer in California. Stripe Tax recognizes the customer's billing address and automatically applies a 7.25% sales tax. The customer sees a checkout total of $107.25; the $7.25 is clearly listed as tax in the order summary.

Why Use Automatic Tax Calculation?

Automatic tax calculation offers several advantages over manual tax handling:

Accurate and region-specific rates: Stripe Tax and Payments AI dynamically calculates the correct rate based on the customer's billing address and local tax laws. This includes U.S. state and city taxes, EU VAT, Canadian GST, and more, ensuring full compliance across different regions.

Real-time updates: Tax regulations frequently change. With automatic tools, you're always using the most current tax rates without needing to monitor laws or manually update pricing.

Integrated tax reporting: Tools like Stripe Tax offer built-in dashboards for generating tax reports, simplifying bookkeeping, reconciliation, and tax filing. These summaries include what you collected, where, and for which tax type.

Global tax tool integrations: Stripe Tax supports integrations with tools like TaxJar, Taxually, Marosa, and HOST to simplify international tax compliance. Payments AI currently integrates with TaxJar, which provides automated sales tax calculations, reporting, and filing primarily for U.S.-based businesses. These integrations help reduce manual tax tracking, ensure regulatory compliance, and generate detailed tax reports across different jurisdictions.

Streamlined user experience: Customers see taxes calculated and added automatically during checkout, reducing confusion and improving transparency.

By using automatic tax calculation, you gain accuracy, peace of mind, and operational efficiency, allowing you to focus more on growth and less on compliance details.

Please follow the steps outlined below to enable the automatic collection of sales tax during the checkout process.

Step 1: Prepare Your Payment Gateway for Tax Calculation

Before taxes can be calculated and applied at checkout, your payment gateway must be properly configured. The steps required can vary depending on whether you're using Payments AI or Stripe. These configurations help ensure the correct tax rate is applied based on the customer's billing address, product type, and regional tax rules.

Payments AI
Stripe
Step 2: Enable Sales Tax in the ClickFunnels Product

Navigate to the Products menu in the left-side navigation.

Select All Products.

On the Products page, select a product and click on it to access the product settings.


Scroll down to the Pricing section.

Check the box Product is taxable.

Choose the appropriate tax category ID from the Tax Category ID field. You can find detailed information on tax codes, categories, and descriptions in the TaxJar documentation.

If your selected category requires a sub-category, choose the appropriate sub-category ID from the Tax Sub Category ID field.

Click Update Product to save your changes.

Displaying Sales Tax on the Checkout Page

When you designate a product as taxable in ClickFunnels, the platform automatically calculates and presents the sales tax during checkout. To ensure this, you must add a Checkout element to your page, which manages the order summary, including the calculation and display of sales tax. Once the customer enters their billing address during checkout, ClickFunnels uses this information to determine the applicable sales tax rate based on configured settings and then displays it in the order summary section. Here’s how it works:

Customer Adds Product to Cart: The customer selects a product to purchase, which has been set as taxable in your product settings.

Customer Enters Billing Address: The customer fills out their billing address in the checkout form.

Sales Tax Calculation: After the billing address is entered, ClickFunnels calculates the sales tax based on the tax settings in Payment AI.

Order Summary Update: The order summary section on the checkout page updates to reflect the calculated taxes. The “Taxes” field in the order summary will display the applicable sales tax amount.


Troubleshooting:

If taxes are not showing or calculating as expected during checkout, here are some things to check:

1. Product Settings

Ensure the product is taxable and the checkbox is selected in your ClickFunnels product pricing settings.

Confirm a valid Tax Category ID is selected (and Sub Category, if applicable).

2. Payment Gateway Configuration

Ensure that either Stripe or Payments AI is properly connected and active in your workspace.

For Stripe, verify that Stripe Tax is enabled and configured with the correct tax registrations and tax behavior settings.

For Payments AI, check that your business is located in a supported region (U.S., Canada, Australia, EU, and UK).

3. Customer Location

Taxes will only be calculated if the customer’s billing address is within a region supported by the payment processor.

4. Currency and Tax Behavior

In Stripe, check if tax is set to be inclusive or exclusive, and confirm this aligns with how your product pricing is displayed.

5. Missing or Incomplete Tax Registration

In Stripe, ensure you've added all applicable tax registrations under your tax settings for the regions from which you plan to collect tax.

Sales Tax FAQs
Does ClickFunnels calculate sales tax automatically?

Yes. When you connect Stripe or Payments AI to your ClickFunnels account, tax can be automatically calculated and displayed at checkout. These processors determine the correct tax based on the customer's billing address and the product's tax category.

What’s the difference between inclusive and exclusive tax in Stripe?
Can I integrate TaxJar with ClickFunnels?
Why is the tax not showing during checkout?