---
title: "How to Setup Notifications"
weight: 1
type: docs
summary: How to setup notifications using MavPay
---
    
### Summary
    
Notifications can be automatically sent out when payouts are generated using MavPay. The text are configured in the config.json file, however there are preliminary steps needed inorder to be able to utilize these features. This section will review the necessary steps and information needed from platforms that allow for auto-notifications sent via MavPay. **This tutorial is meant for individuals that have zero experience with interacting with these systems - feel free to skip sections if you are an advanced user.**
    
---
    
### Twitter
    
A Baker can use MavPay to automatically send notifications that payments have been made. This allows for ease of communications for the public baker to the delegates and we will walk through steps to allow for this here. There will be two sections:
    
    1. Twitter Setup
    2. MavPay config.json file setup
    
#### Twitter Setup
    
    In order to setup twitter, be sure you are signed in on a browser window to your twitter account. 
    
 1. While being signed into Twitter in a seperate browser, navigate to https://developer.twitter.com/ and select 'Developer Portal' in the top menu- the developer portal site where you will set up your development account and get the required information for the config.json file and set up permissions.
    
| ![<Navigate to the Twitter Development Portal website>](/mavpay/tutorial/twitterNotificationimage0.png) |
|-|
    
 2. You will then need to fill in some basic information in order to enable the Development Portal profile to be active. be sure that all of the information is correct (if you use multiple twitter accounts be sure the one you want to enable for notifications is the correct one). 
    
| ![<Fill in Basic information to set up a Developer Account for Twitter>](/mavpay/tutorial/twitterNotificationimage1.png) |
|-|
    
 3. Once you submit the information for your development profile - you will need to accept the Terms and Conditions.
    
| ![<Accept Terms and Conditions to Proceed>](/mavpay/tutorial/twitterNotificationimage2.png) |
|-|
    
 4. After accepting Terms and Conditions - you will need to verify your e-mail address that you provided by clicking the link in the e-mail sent from Twitter. 
    
| ![<Verify the e-mail used for your twitter account - you may need to set this up in Twitter before hand if not done>](/mavpay/tutorial/twitterNotificationimage3.png) |
|-|
    
 5. Once you verify your email - this will automatically link you back to your Developer Portal Site and prompt you for an 'App Name' (see MavPay Notif in screen capture). 
    
| ![<Name your APP on Twitter Development Portal website>](/mavpay/tutorial/twitterNotificationimage4.png) |
|-|
    
 6. Once you name your App - you will be given 3 seperate Keys. These will be used to inorder to call the Twitter profile that you are looking to send Notifcations to - and sign for the permissions. Be sure to have these saved in a secure place - they will be used later. Once you have the keys secured, click 'Dashboard' button in lower right. 
    
| ![<Save the Keys for your Twitter Development Profile and App>](/mavpay/tutorial/twitterNotificationimage5.png) |
|-|
    
 7. You will now be in your Twitter Development Dashboard and see the App you created (for this example MavPayNotifs). Click the 'gear' icon to continue set-up. 
    
| ![<Click the gear icon on the app you created for twitter notifications for MavPay and continue to setup your app.>](/mavpay/tutorial/twitterNotificationimage6.png) |
|-|
    
 8. Navigate to 'User Authentication Settings' section and click 'Set-up' to continue.
               
| ![<Navigate to User authentication setting and click 'Set up'>](/mavpay/tutorial/twitterNotificationimage7.png) |
|-|
    
 9. We will fill out the required items for the form under User Authentication settings as follows: <br>
        i. App Permissions: Select 'Read and write' <br>
        ii. Type of App: Select 'Web App, Automated App or Bot'<br>
        iii. App Info: <br>
            a. Callback URI/Redirect URL: this can be anything but for this example we will use 'https://www.MavPayisthebest.com/'<br>
            b. Website URL: this can be anything but for this example we will use 'https://www.MavPayisthebest.com/'<br>
        iv. Click 'save' when finished. <br>
    
    | ![<Select the outlined toggles under App Permissions & Type of App, then fill in a website for App Info>](/mavpay/tutorial/twitterNotificationimage8.png) |
 |-|
               
  10. You will then get your Client ID and Client Secret - copy and save both of these with your other Keys attained earlier. Click 'Done'
            
 | ![<Copy the Cliend ID and Client Secret>](/mavpay/tutorial/twitterNotificationimage9.png) |
 |-|   
      
  11. This will bring you back to the main screen of the App - navigate to the 'Keys and Tokens' toggle at the top of the page. Now, 'Generate' an Access Token and secret - write these down and then once you have confirmed you will be ready to edit the config.json in MavPay. Note - be sure the Access Token and Secret has 'read and write' permission (see image below). For the Next step - setting up the config.json - you will need four items:<br>
        a. API Key and Secret (also known as Consumer Key/Secret)<br>
        b. Access Token and Secret
    
 | ![<Generate your Acces Token and Access Token Secret - and then verify the information.>](/mavpay/tutorial/twitterNotificationimage10.png) |
 |-|   

---
#### MavPay config.json Setup for Twitter Notifications
    
We will use the API Key and Secret as well as the Access Token and Secret to edit the Config file to allow for permissions and calls to push notifcations upon each successful payout.
               
1. You will add the following code block at the base of the config.json file to enable the notifications for MavPay. Note that the message_template can be anything and you can use the <Cyle>, <Delegators>, <DistributedRewards> terms to automatically fill in these terms for each cycle. <br>
    `notifications: [`<br>
    `{`<br>
     `access_token: Your_Acces_Token`<br>
      `access_token_secret: Your_Access_Token_Secret`<br>
      `consumer_key: Your_Consumer_Key`<br>
      `consumer_secret: Your_Consumer_Key_Secret`<br>
      `message_template: Rewards for <Cycle> have been paid to <Delegators> delegates in amount of <DistributedRewards> using #MavPay.👀 MVRK baked with #MavBake! We donate to wallet mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g to fund future development in Mavryk. #cerberusbakery #mavryk.`<br>
      `type: twitter`<br>
    `}`<br>
    `]`
    
| ![<Fill in the information for the config.json file with you information!>](/mavpay/tutorial/twitterNotificationimage11.png) |
|-|   
                              
2. Once you have filled in the necessary information - you have setup Notifications for Twitter! Test the notification by using command: <br>
      a. `mavpay test-notify`

---

Any questions/comments/concerns? Please contact the Mavryk Dynamics team on
[Telegram](https://t.me/MavrykNetwork) 