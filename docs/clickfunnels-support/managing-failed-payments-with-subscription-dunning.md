# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/managing-failed-payments-with-subscription-dunning

---

Subscription Dunning is a critical process for effectively managing failed subscription payments. By using dunning, the system can attempt to recover failed payments through automated retry rules, ensuring minimal impact on revenue. This article will guide you through what subscription dunning is and how to enable and manage it using Payments AI.

What is Subscription Dunning

Subscription Dunning is the process of managing failed subscription payments by automatically retrying charges or notifying the customer to update their payment information. It ensures that subscription revenue is maintained while providing customers the opportunity to rectify failed payments.

For instance, imagine a customer subscribing to a monthly fitness coaching service. If their credit card payment fails due to insufficient funds, the dunning process would automatically attempt to retry the payment at a later date or contact the customer for updated payment details.

Successful Payment: If the customer updates their payment details successfully, they can continue enjoying the subscription services without interruption.

Failed Payment: If the retries fail and the customer takes no corrective action, the subscription may be canceled, and their access to the service will be restricted.

Understanding the Dunning Process in Payments AI

The dunning process in Payments AI is designed to automatically manage failed payments through a series of retry attempts based on the configured dunning rules (either default or custom). When a dunning rule is in place, Payments AI will notify the customer of the failed payment and initiate retries according to the specified schedule:

Successful Payment: If the payment is successful during one of the retry attempts, the customer’s subscription will continue without interruption.

Unsuccessful Payment: If all retry attempts fail, the system will take action as defined in your dunning configuration. This may include canceling the subscription, marking invoices as abandoned, or any other actions you have configured.

How to Enable Subscription Dunning

You must configure your Payments AI account settings to enable and manage subscription dunning.

Log in to the Payments AI account and navigate to the Automation Rules menu.

In the Subscriptions menu, you can apply the subscription dunning rules in the Subscription Dunning section.

You can set up several scenarios, such as retry schedules, what will happen after each attempt, what will happen after the last failed attempt, emails, etc.

Understanding the Importance of Subscription Dunning:

Automatic payment retries depend on rules set in Payments AI. If no dunning rules are configured, retries will not occur. To avoid missed payments and maintain your revenue stream, it is recommended to configure at least default subscription dunning rules.

If no rules are set, failed payments will be marked as overdue, but the customer will retain access to the product, leaving it up to you to monitor and collect the overdue payments or manually cancel the subscription.

For details on setting up dunning rules, refer to the Payments AI official documentation: Customized Subscription Dunning.

Default Subscription Dunning Rules

Note:

If this is your first time setting up a subscription dunning rule, Payments AI does not apply any default rules automatically. However, when you initiate the setup of a new dunning rule, Payments AI provides a pre-configured “First Subscription Dunning Rule” that you can use as a starting point. This pre-configured rule can be adjusted to meet your specific business needs, simplifying the process of managing failed payments.

If you have enabled the default subscription dunning rule in Payments AI, it will make 3 retry attempts on failed payments:

The first retry, using the full amount, occurs 3 days after the initial failed attempt.

The second retry is scheduled for 7 days after the first failed attempt.

The final retry happens 15 days later at 06:30:00 using the full amount.

If all retry attempts are unsuccessful, the system will proceed according to the actions defined in your Subscription Dunning Configuration for “what happens after the last failed attempt.” These actions could include canceling the subscription, marking invoices as abandoned, or other options. Ensure these actions are set up appropriately in the dunning rules within Payments AI to align with your business needs.

Handling Exit Dunning Stage Using ClickFunnels Workflows

Exit Dunning refers to the point in the subscription payment process where a failed payment is either successfully recovered or when all retry attempts have been exhausted without success. Properly handling exit dunning helps minimize revenue loss by managing failed payments effectively.

Example of Exit Dunning:

Imagine a customer subscribes to a monthly service and their payment fails due to an expired credit card. Payments AI will automatically attempt retries based on the configured dunning rules. If the payment is successfully collected during one of these retries, the Exit Dunning process will occur, and the customer’s subscription will continue uninterrupted. However, if all retry attempts fail and no payment is made, the process will also move into Exit Dunning, where actions such as canceling the subscription or marking invoices as abandoned may be taken based on your configured settings.

How to Handle Exit Dunning Using Workflows:

ClickFunnels provides a specialized workflow called “Exit Dunning” to manage failed subscription payments. This step monitors failed payment attempts and takes action when the payment is resolved or the retry process has concluded. This allows you to automate the process of managing failed payments.

For detailed guidance on setting up the Exit Dunning step in your workflows, refer to the article: Workflows “Exit Dunning” Step - Manage Failed Subscription Payments.

Recap

When Subscription Dunning Happens: Subscription dunning occurs when a customer’s subscription payment fails. Payments AI will automatically initiate retry attempts to collect the payment, following your configured rules.

What You Should Do: You should configure subscription dunning rules in Payments AI to manage failed payments effectively. This includes specifying how many retry attempts should be made, when they should occur, and what actions to take if all retries fail.

What You Can Do with Exit Dunning: In ClickFunnels, you can use the Exit Dunning step within workflows to automate the handling of subscriptions after completing the dunning process. This step allows you to determine actions such as canceling the subscription, unenrolling customers, or sending notifications depending on whether the payment was successfully collected or ultimately failed.