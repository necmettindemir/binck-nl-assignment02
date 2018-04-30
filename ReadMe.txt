

----------------------------------------------

Assignment

2) Please design a service, which would send out «smart alerts» 
(notifications via push/email/text messages) 
to clients based on events in their investment portfolios. 

----------------------------------------------

Assumptions

1. It is supposed that clients can determine their preferences about notification channels.
   It means a client checks all or some of the followings. 

   Notification channels

	- web notification		
	- mobile app notification 	

	- sms notification 		
	- email notification 		


2. It is supposed that clients can determine their preferences about events and 
   notification rules.

   It means a client can prefer time/condition/type/etc of any predefined event for notification.

   To be able to design such system we should collect all possible situations in a pool and 
   we should let client to make preference from the view of amount, limits, time, condition, etc.


   Some notifications are bidirectional and interactive.

   For example, a client could prefer one or some the followings to get notification using any channel mentioned above.

   - Send push notification to mobile application about short-time opportunity to make an investment.
     The client is provided with to buttons. "I Accept" or "I don't Accept"

   - Send push notification to mobile application as a warning to direct customer to sell the investment.
     The client is provided with to buttons. "I Accept" or "I don't Accept"



	
   Some notifications are one-directional.
   
   For example, a client could prefer some of the followings.

   - send sms notification to my mobile app when my any investment increased 5% in last 5 hours
   - send email at each Friday 17:00 pm as summary of my investments
   - send sms notification when any transaction occurs about my any investment
   - etc.

      
3. From the view of efficiency of sending notification,
   many parameters should be considered.

   - messages must bu short as much as possible
   - timing must be considered according to geographic location
     (client must be awake for push notifications)
  

----------------------------------------------


Solution for Smart Alerts



1. Flow of Data

   From the view of flow of notifications, there two directions.


   1.1. GUI pulls notification from server

	- web notification		
	- mobile app notification 

	- Timer or timer-like mechanism can be used at GUI side.
        - At each tick or at each event of timer-like mechanism a request is sent to server (possibly a web service) 
          and a algorithm of check list about events is performed. 
          If there is a result at the end of this request a response is returned and 
          shown in/on GUI.
        


   1.2 Server sends notifications to the client accounts in another server 
       using SMTP, SMS gateway, etc

   	- sms notification 		
	- email notification 		

	1.2.1 Timer, timer-like mechanism can be used at application level of server side
	      For such operation a notification sender executable can run using timer.

        1.2.2 Scheduled database job can be used at the database level of server side


   1.3 Event itself can be used to send notification
		
	This is the simplest one. If user perform any action using web or mobile app
	a notification message can be sent using email, sms, etc.



2. Logging

   All notifacation messages should be logged.
   There should be a log list that can be accessed by an admin
   
   With high-quality log mechanism we will have the following advanteges

   - The log list will help us make decision about the points where we should develop more
   - We have information against any judicial situtation 
	


3. Statistics

   From the view of type/time/etc statistics of preferences should be evaluated.

   This statistics of preferences will help us to classify our customers according to many parameters
   such us age group, geographic location, device usage, etc.

   The result of the statistics will help us determine our policy about customer behaviours.



4. Templates

	There should be template for each type of messages that can be filled according to client preference and event condition.

	For example 1 : 

	
	Investment change  template in English could be as below.
	
	"Dear <<FirstName>> <<LastName>> Your investment with the code of <<INVESTMENT_CODE>> has <<CHANGE_TYPE>> <<PERCENT>>% in last <<AMOUNT_OF_TIME>> <<TYPE_OF_TIME>>"

	The derived message could be as below.

	"Dear Bilbo Baggins Your investment with the code of <<784787>> has increased 7% in last 2 days"	

	

5. Multilanguage support

	- With template Multilanguage support can be performed.

	- According to the preffered language client will get any notification message.

	- This means, a dynamic data design should be used at database level for multilanguage support of message templates.


----------------------------------------------


Technical Design for Smart Alerts

image...

