# TeamsPresenceAPI
Use the Teams Presence API to automate events based on user status. This demonstration shows how you can connect Teams Presence to your Smart Home

As seen in my LinkedIn [Post](https://www.linkedin.com/posts/denzilfernandes_microsoft365-powerautomate-apifirst-activity-6755244173097623553-GCTN) 
> "💡 Did you know that you can connect your smart home to Microsoft Teams? Take a peek here to learn how you can use the Teams Presence API and Power Automate to change the lights in your home.
>
> 🏠 How this helps? Well I have 3 kids schooling online at home. As I begin my journey at Microsoft, I am in many training sessions some of which I would like to have a little less interruption. Now I can change the light in their room so they know "Daddy's on a call"

## M365 Tenant & 3rd Party Requirements 
1. Azure AD App Registration
2. IFTTT Subscription
2. Power Automate with Premium Connectors ( HTTPS Request / When a HTTP Request is received)
3. Microsoft Teams 

## Azure AD App Registration
1. Register Azure AD Application and Grant Permission to the Teams Presence API

## IFTTT
Use a Webhook as a Trigger and set an action to control the lights or devices you want to connect and control.
1. If you have already use IFTTT then proceed to create a trigger using Webhook. (https://ifttt.com/create/if-maker-webhooks)
2. IFTT Webhook FAQ Check out (https://help.ifttt.com/hc/en-us/articles/115010230347-Webhooks-service-FAQ)

## Power Automate
1. Get the ObjectID from Azure AD for the User Account that we need to subscribe for Teams Presence Changes.
2. Import 2 Power Automate Flows
  - Create Subscription for Teams Presence 
  - Get Teams Presence Subscription

## Microsoft Teams
1. Test Changing the Presence Status of the User Account (i.e. Account that is setup for teams subscription)
