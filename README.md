# feedback-plugin
A plugin to display feedback in the starter repo


If your app is based on the [node-starter-app](https://github.com/cds-snc/node-starter-app) this should be an easy process. Otherwise you will need to MacGyver it. See [feedback-plugin-example](https://github.com/cds-snc/feedback-plugin-example) for an example of how to install it on a fresh copy of the starter app. 

To install our plugin, if your app is based on the node-starter-app:
Run `$npm install git+https://git@github.com/cds-snc/feedback-plugin.git#v1.0.2`
 Add the following to your app.js file:
`const { registerPlugins } = require('./node_modules/feedback-plugin/register')`
 
`app.plugins = registerPlugins(app)`

Copy and paste our translations into your `locales/en.json` and `locales/fr.json` files
To set up the mid-service feedback component, you will need to import the styling and modify the base template. All the necessary changes are in this commit. 
To set up the post-service feedback component, create new routes in your app for a feedback page and feedback-confirmation page. The full set of changes you need is here. 
To customize the questions and other content displayed in these components, you can extend the templates and define your own nunjucks blocks.

##Where to send the responses
There are 2 options for this:
Use the feedback-collector we have built, or
Set up your own endpoint within your app, or

How you set up your own endpoint within your app will depend on the tech stack you are using. Here are some reasons you might want to use the feedback-collector:
Very little code to write
Gives you the option of emailing out user responses as they are submitted
Saves the responses in a database for later analysis
Lets you download a CSV file with your feedback responses.

To hook up your form to the feedback-collector, follow these steps:
Log in with your CDS Google account here: http://cds-feedback-collector.herokuapp.com/
Add a new form.
a) If you are setting up a post-service feedback form, or any form where the respondent will be submitting from a dedicated questions page, select that you want the respondent to be redirected, and enter the confirmation URL (such as: https://cds-feedback-prototype.herokuapp.com/en/feedback-confirmation). 
b) If you are setting up the mid-service feedback bar, select “No” redirect.
Add your form and confirm your email address.
a) If you are going to redirect the respondent, add the following action to your form html: `<form action=”https://cds-feedback-collector.herokuapp.com/en/send?id=YOUR_FORM_ID">`
b) If you are not redirecting the user, …
You’re done! The feedback-collector is now collecting your responses. You can download them at any time by clicking “Download responses” from the my-forms page.
