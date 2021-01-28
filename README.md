# TeamsPresenceAPI
Use the Teams Presence API to flow events based on user status. This demonstration shows how you can connect Teams Presence to your Smart Home

[LinkedIn](https://www.linkedin.com/posts/denzilfernandes_microsoft365-powerautomate-apifirst-activity-6755244173097623553-GCTN) 

## M365 Tenant & 3rd Party Requirements 
1. Azure AD App Registration
2. IFTTT 
2. Power Automate with Premium Connectors ( HTTPS Request / When a HTTP Request is received)
3. Microsoft Teams 

## Azure AD App Registration
1. Register Azure AD Application and Grant Permission to the Teams Presence API
2. Gather the Tenant ID, Application ID And Create a Secret ID which will be used in the flows below.
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/1-AzureADAppRegistration.png" style="max-width:100%;">

## IFTTT
Use a Webhook as a Trigger and set an action to control the lights or devices you want to connect and control. 
1. Use IFTTT to create a Webhook Trigger with an action to control the smart devices. (https://ifttt.com/create/if-maker-webhooks)
2. Copy the Webhook Url from IFTTT (Example: https://maker.ifttt.com/trigger/activate_kidsroom_busy/with/key/k12345678ABCDEx)

IFTT Webhook FAQ Check out (https://help.ifttt.com/hc/en-us/articles/115010230347-Webhooks-service-FAQ)

## Power Automate
1. Get the ObjectID from Azure AD for the User Account that we need to subscribe for Teams Presence Changes.
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/1-AzureADUserObjectID.png">

2. Import [Get Teams Presence Subscription](https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3A0-GetTeamsPresenceSubscription-Exported_20210128160412.zip)

  * Copy the HTTP Post URL to be used later in Step 3
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3A1-PowerAutomate-GetTeamsPresenceSubscription-CopyHTTPRequestReceived.png" style="max-width:100%;">

 * Update the HTTP Post URL to IFTTT Webhooks
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3A2-PowerAutomate-GetTeamsPresenceSubscription-UpdatePostToTriggerIFTTT.png" style="max-width:100%;">

3. Import [Create Subscription for Teams Presence](https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3B0-CreateSubscriptionforTeamsPresence-Exported_20210128160435.zip)

 * Update the Tenant ID, Application ID and Secret. 
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3B1-PowerAutomate-CreateSubscriptionforTeamsPresence-UpdateUserNamePassword.png" style="max-width:100%;">

 Update the username password. Note: If you have MFA on your account, you can use another account in the same tenant without MFA enabled.
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3B2-PowerAutomate-CreateSubscriptionforTeamsPresence-UpdateUserNamePassword.png" style="max-width:100%;">

  * Update the NotificationURL - This URL is the HTTP Request Received from the Get Teams Presence Subscription
<img src="https://github.com/M365-DenzilFernandes/TeamsPresenceAPI/blob/main/3B3-PowerAutomate-CreateSubscriptionforTeamsPresence-UpdateNotificationUrl%2BResourceGUID.png" style="max-width:100%;">

## Microsoft Teams
1. Test Changing the Presence Status of the User Account (i.e. Account that is setup for teams subscription)
