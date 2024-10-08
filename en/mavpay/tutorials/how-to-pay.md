---
title: "How to Pay Delegators"
weight: 1
type: docs
summary: How to Pay Delegators Using MavPay
---

## Using MavPay

### Summary of Using Mavpay

Using the MavPay application is through CLI for now and will be
carried out through a few commands. 

This section will review:

1.  Generating a payout table for all delegates
2.  Generating a test notification (*Testing the
    **Twitter**/**Discord**/**E-mail** notifications from the advanced
    configuration file*)
3.  Generating an actual payout
4.  Running a continual payout
5.  Keeping MavPay up-to-date

Before using a command in MavPay, you will need to run
***two additional commands</span>*** that will
allow you to call the application via commands and set permissions
While in the MavPay directory in the terminal, run the following
commands (*see code and examples below*):

   `mv mavpay-linux-amd64 mavpay`

| ![<Command to move MavPay application in order to run.>](/mavpay/tutorial/mavpayImage16.png) |
|-|

   `chmod +x mavpay`
    
| ![<Command to change permissions for MavPay application in order to run.>](/mavpay/tutorial/mavpayImage17.png) |
|-|
    
---    

### Using MavPay: Step 1 - Generating a payout Table

Generating a payout table is a tool that is useful for Public
Bakers because it allows the baker to see the incoming rewards from
baking (both block rewards & fees from delegates), review payout per
delegator from their stake, and other data (see below).

The command to generate a payout table is as follows (always remember to be in the
*mavpay* directory: 

   `./mavpay generate-payouts`

This will generate a payout table, as exampled below: 

| ![<Description of output for ./mavpay generate-payout command.>](/mavpay/tutorial/mavpayImage18.png) |
|-|

***Note: the Delegator & Recipient columns have been hidden***

1.  Represents the table of *invalid* delegators that will **not** be
    paid out due to not meeting specific thresholds (ie minimum payout
    threshold/minimum balance)
2.  Represents the table of *valid* delegators that will be paid out
3.  The list of Delegators first 4 and last 4 characters of their
    wallet
4.  The list of Recipients of payment first 4 and last 4 characters of
    their wallet (often the same as Delegator)
5.  The delegated balance for each Delegator for that particular cycle
6.  Represents the kind of reward given (ie delegator reward, baker
    reward, and fee income)
7.  The amount of the specific reward to be paid out
8.  The fee rate for each delegator, will reflect those delegators who
    have custom fees per the configuration file
9.  The fee collected by the baker from each delegator for hosting their
    delegation
10. The transaction fee to pay out each reward



### Using MavPay: Step 2 - Testing Notifications

This step will be used to test the notification system for your
MavPay application. This step will NOT need to be completed every
payout, but only when you changes messages to test that it was
successful. 

while in the *mavpay* directory, use the command: 


   `./mavpay test-notify`



### Using MavPay: Step 3 - Initiating a Payout

To use the MavPay application to send a payment will require 1
line of code and one additional confirmation while it runs.  

To run MavPay, run the code: 

`./mavpay pay`


The system will initiate the MavPay application at this point and present a payout
table, similar to the table(s) from step 1.

Once the table is displayed, the prompt will ask you to confirm the payout, and you need to confirm *y* or *n* (see below):

| ![<Output and subseqant request for confirmation while running MavPay.>](/mavpay/tutorial/mavpayImage19.png) |
|-|

1.  You will be asked to confirm, type '***y***' for yes or '***n***'
    for no

If you confirm the transaction, the payouts will proceed and your
delegates will be paid out, as well as your Baker wallet. Remember, if
you are using a separate wallet to payout from your Baker wallet you
will need to add funds to cover the payments. 

At this point you have successfully ran the MavPay application and paid out your
delegates. Be sure to check the confirmations and any errors that may
have been broadcasted in the terminal (ie, the example above did not
send notifications because that was not set up).
    
### Using MavPay: Step 4 - Running a Continual Payout

To use the MavPay application to send a payment will require 1
line of code and one additional confirmation while it runs.  

To run MavPay in continual mode, run the command: 

   `./mavpay continual`
   | ![<Run MavPay in continuous mode>](/mavpay/tutorial/mavpayImage20Continual.png) |
   |-|
    
Running in continual mode will start its first payment a little bit after the current cycle (one during which you launched it) finishes and the next one begins (usually around 30-60 minutes after the beginning of the new cycle).
    
If you would like to start in continual mode but still need to pay your delegators for last cycle, run the command from Step 3. first and then launch MavPay in continual mode.
 


---
    
## Summary: MavPay

MavPay is an application that allows for easy payouts for public
bakers on the Mavryk Blockchain. This allows for significant
customizations and flexibility with respect to the payout system and
empowers bakers to further take control of their Bakery and aid in
decentralizing the Mavryk Blockchain. 

---

Any questions/comments/concerns? Please contact the Mavryk Dynamics team on
[Telegram](https://t.me/MavrykNetwork) 