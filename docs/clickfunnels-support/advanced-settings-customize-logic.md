# EXPLORE ARTICLES

**Source:** https://support.myclickfunnels.com/docs/advanced-settings-customize-logic

---

ClickFunnels offers advanced settings to help you fully personalize the behavior and functionality of your containers (sections, rows, columns, and elements). These settings provide greater control over the container's style, animation, and logic. This article focuses on the Logic section within the Advanced settings, where you can apply rendering conditions and custom attributes to enhance the interactivity and functionality of your pages.


Requirements

An active ClickFunnels account

A page created in your workspace

A section, row, column, or element added in the editor

Render Conditions
Creating a new Render Condition

Render Conditions allow you to add logic around elements to control what gets rendered on the page. Each Render Condition creates a new “if” condition where you can use some variables and logic operators. Certain variables' availability depends on what part of your site or theme the page is being used.

To create a new Render Condition node, click the Add Render Condition button from the Logic section of an Element’s Settings. Doing so creates a new Render Condition node where that element was and automatically places the element inside the “if” condition.


Modifying a Render Condition

After creating a Render Condition for an element, the button in the Logic section of the Element’s Settings will change to Visit Closest Condition Settings. Click on this button to access the Render Condition settings for the Render Condition node directly containing the element.


Otherwise, you can view your Page’s Layout to find all Render Condition nodes. Click on the Render Condition node to access its settings.

Adding Elements to a Render Condition

When you go to add a new element beneath one inside a Render Condition node, you can add a new element inside the Condition node with that element or add it below the Condition node. Adding an element inside the Condition node means it will be subject to the same Logic as any other element inside; Otherwise, it is unaffected.


If you wish to add an existing element to the Condition node, you may do so from the Page’s Layout view. Drag and drop the element from the list to your desired spot inside the Condition node.


Removing a Render Condition

Access a Render Condition settings as outlined in the Modifying a Render Condition section, and you will see a Safely Delete Condition Node button. Click the button to remove only the condition, keeping all the elements inside intact.


Custom Attributes

The Custom Attributes feature in ClickFunnels allows you to add HTML attributes directly to your containers (Sections, Rows, Columns, Flex, and Elements), providing advanced customization, dynamic functionality, and seamless integrations. With custom attributes, you can enhance the interactivity of your pages, apply specific styling, track user behavior, and even enable external tools to interact with your page.

How Custom Attributes Work

Custom attributes consist of a name (e.g., data-custom) and a value (e.g., example-value). Once added, these attributes are included in the HTML of your page, making them accessible for styling with CSS, controlling behavior with JavaScript, or interacting with third-party tools.

Adding a Custom Attribute in Containers

Hover over the container (Section, Row, Column, Flex, or Element) and click the gear ⚙️ icon.

Go to the Advanced option.

Click the Logic menu.

Then, click the Add Custom Attribute button to insert a custom attribute name and value for the container.


Click Save to add the attribute in the container. You can add more than one custom attribute in the containers.

Styling with Custom Attributes

You can style containers dynamically by referencing their custom attributes in your CSS. For example, if you add a custom attribute data-highlight="button", you can target it in your CSS like this:

[data-highlight="button"] {
  background-color: #ff5722;
  color: #fff;
}
CSS
COPY
Enabling JavaScript Interaction

Custom attributes allow you to trigger custom behaviors with JavaScript. For instance, you can track interactions using a custom attribute like data-track="cta-button":

document.querySelector('[data-track="cta-button"]').addEventListener('click', function() {
  console.log('CTA button clicked!');
});

JavaScript
COPY
Use Case Examples of Custom Attributes

Precise Analytics Tracking

Add a custom attribute like data-track="subscribe-now" to buttons or links to enable detailed tracking with analytics tools. This allows you to measure user engagement more effectively.

Dynamic Styling

Use attributes to create conditional styles for containers. For instance, you could add data-theme="dark" to a section and apply specific styles:

[data-theme="dark"] {
  background-color: #222;
  color: #fff;
}

CSS
COPY

Third-Party Tool Integration

Many external tools require specific HTML attributes to function. For example, a chatbot integration may require a data-bot="live-support" attribute on a specific container.