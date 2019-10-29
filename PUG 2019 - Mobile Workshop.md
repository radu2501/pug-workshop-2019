
# Kinvey and OpenEdge

A short workshop script to create a small NativeScript app, followed by Kinvey Studio web & mobile app that integrates an OpenEdge based data source.


**Sports Shop App – MVP Requirements**
As a Sports Shop 2000 customer I want to
- Login to the app
- Display an editable list of sports equipment available in the shop (using an OE backend)
- Arrange a consultation with a shop assistant on new skis in a shop location of my choice

## Workshop requirements:

-   Windows or Mac required + Android Device or IPhone
-   Create Kinvey account (completely free):  [https://console.kinvey.com/sign-up](https://console.kinvey.com/sign-up)
-   Download and install Kinvey Studio:  [https://studio.kinvey.com/](https://studio.kinvey.com/)
    
 
-   Download and install NativeScript Playground & Preview apps from Google Play  [https://play.google.com/store/apps/details?id=org.nativescript.play](https://play.google.com/store/apps/details?id=org.nativescript.play)[https://play.google.com/store/apps/details?id=org.nativescript.preview](https://play.google.com/store/apps/details?id=org.nativescript.preview)  or Apple AppStore
    
-   Download and install Kinvey Scanner & Preview apps from Google Play  [https://play.google.com/store/apps/details?id=com.kinvey.scanner](https://play.google.com/store/apps/details?id=com.kinvey.scanner)[https://play.google.com/store/apps/details?id=com.kinvey.preview](https://play.google.com/store/apps/details?id=com.kinvey.preview)  or Apple AppStore
-  Install [nodejs 10](https://nodejs.org/dist/v10.16.0/node-v10.16.0-x64.msi) and "npm install -g nativescript"

## Hands-on 1 - Create a NativeScript App

_**Creating a NativeScript app that displays a list of items from a SmartComponent Library PASOE backend**_

1.  Navigate to the  [NativeScript Playground Project](https://play.nativescript.org/?template=play-ng&id=prFgzv&v=8)
2.  **Fork it**  by selecting "Fork" from the toolbar above the code editor
3.  Select "Preview" from the top right corner of the page
4.  Open Playground on your mobile device and scan the barcode that is displayed
5.  You should now see a login page, that is unusable (yet)
6.  In app/shared/config.ts, update the API_BASE_URL to the one displayed.
7.  You should now be able to sign in and see an empty "Home" screen.
8.  In app/home/home.component.html, add the ListView where indicated and bind it to the "items" property found in the corresponding TS file. More information on how to use the ListView can be found  [here](https://docs.nativescript.org/angular/ui/ng-components/listview)
9.  In app/home/home.component.ts, uncomment the block of code making the HTTP call.
10.  Congratulations! You should now be able to see a list of sports items after you sign in.
## Hands-on 2 - Create a Kinvey App
***Creating an app backend using the Kinvey Console***

1. Login to https://console.kinvey.com
2. Create an app - Choose any name you like
3. Open the dashboard of the *Development* environment of that app
4. Create a user in that app (user: demo pw: demo)
5. Create a collection "items" in that app
6. Add a column "ItemName" in that collection
	*(add as a many additional columns as you like)*
7. Add some data to that collection (e.g. sports equipment)
8. Retrieve/edit some data in the collection using the *API Console*

Learn more here: https://www.progress.com/blogs/how-to-get-started-with-kinvey-and-nativescript-fast

## Hands-on 3 - Use the Kinvey SDK in a NativeScript App
_**Use the Kinvey SDK abstractions to access the Kinvey backend**_

[https://devcenter.kinvey.com/nativescript/guides/datastore](https://devcenter.kinvey.com/nativescript/guides/datastore)

1.  Navigate to the  [NativeScript Playground Project](https://play.nativescript.org/?template=play-ng&id=AcHtxD&v=2)
2.  **Fork it**  by selecting "Fork" from the toolbar above the code editor
3.  Select "Preview" from the top right corner of the page
4.  Open Playground on your mobile device and scan the barcode that is displayed
5.  You should now see a login page, and after logging in a blank "Home" view
6.  Add an OnInit method to the home.component.ts class to have an event handler for loading data when the view loads
7. Add a Kinvey DataStore private member to the class pointing at the "items" collection
8. Perform a fetch all by calling find() on the DataStore and subscribe to the results. 
9. Assign the results the items class member 
10. You should now see data from your Kinvey backend in the list 

## Hands-on 4 - Use an External Data Source
***Connect to an OpenEdge data source***

There are three options to integrate OpenEdge in Kinvey:
* Connect to OE using RapidData for Progress:
[https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforProgressData](https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforProgressData)

* Connect to OE using a FlexData connector for JSDO:
	[https://devcenter.kinvey.com/rest/guides/flex-services#flex-data](https://devcenter.kinvey.com/rest/guides/flex-services#flex-data)
	The JSDO FlexData connector is available here:
	[https://github.com/steinerj/jsdo-kinvey-flex](https://github.com/steinerj/jsdo-kinvey-flex)
* Connect to OE using  RapidData - DataDirect Odata via SQL (not part of this workshop)
 [https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforDataDirect](https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforDataDirect)

 ### Rapid Data for Progress
1. Under *Services* - create a new RapidData for Progress Connector in the scope of your app
2. Connection Details (anonymous auth)
Endpoint: https://oemobiledemo.progress.com/OEMobileDemoServices/
Catalog:
https://oemobiledemo.progress.com/OEMobileDemoServices/static/SportsService.json
3. Create a new Service Object - Discover - *Item*
4. Name as you like, choose *Itemnum* as primary key, Activate all operations, save and discover all fields, map *Itemnum* to *_id*
6. In your app, swap the "items" store from internal to the newly created OE store
7. Test in API Console and/or web/mobile app

### FlexData connector for JSDO
1. Clone or download this repository: https://github.com/steinerj/jsdo-kinvey-flex
2. In the directory of the cloned repo, run the following commands to verify your environment is working correctly. This will run the flex data service locally.
	* npm install
	* node .
3. You can now open [http://localhost:10001/items](http://localhost:10001/items) to verify that the service is correctly retrieving items from the OE service.
4.  In the Kinvey web console, create a Flex Service Runtime container under the "Services" tab in context of your Kinvey App
5.  Run the following commands to create your Kinvey profile and deploy the flex service to the previously created container:
	* kinvey init
	* kinvey profile login NAME
	* kinvey flex init
	* kinvey flex deploy
6. In your app, swap the "items" store from internal to the newly created FlexData service
7. Test in API Console and/or web/mobile app

Learn more about Flex Services here:
[https://www.progress.com/blogs/getting-started-with-kinvey-flexservices](https://www.progress.com/blogs/getting-started-with-kinvey-flexservices)

For learning how to set up JSDO capable OpenEdge Data Object Services, please follow these tutorials:
https://www.youtube.com/watch?v=Nk9wrmYUFPA

https://www.progress.com/services/education/openedge/creating-openedge-data-object-services

## Optional: Hands-on - Create a Kinvey Studio app

***Build a web & mobile app based on Angular, NativeScript and Kinvey using the low code Kinvey Studio***

**Steps:**
1. Create a new app in Studio and point it to your Kinvey Backend app
2. Choose an app theme (bonus: fine tune the styling on css level - see: [https://devcenter.kinvey.com/nativescript/guides/studio-themes](https://devcenter.kinvey.com/nativescript/guides/studio-themes))
3. Modify the login page in the systems module to use a different logo
4. Create a new module, e.g. "Sports"
5. Create a web view grid and point it to the "items" collection
6. Create a mobile list view (single or double line) and also point it to items - add it only to the tab navigation
7. Activate search for both
8. Test in browser and phone

For reference: [https://devcenter.kinvey.com/nativescript/guides/studio-getting-started](https://devcenter.kinvey.com/nativescript/guides/studio-getting-started)

## Optional Hands-on - Chatbot
***Offer a modern, conversational UI as part of your web & mobile app***
1. Create a blank mobile view and a layout manager
2. Add a "Chat" component
3. Under advanced - paste the following chatbot JSON:

Mobile:

    {
    "botId": "5b3a83534eeb2f4ee5d99da4",
    "channelId": "9e48b0dc-8cdb-4e79-9ce0-6595e8ab2da3",
    "channelToken": "1b45111f-d2f1-49ff-8531-4980ad1fcceb"
    } 

4. Add a chatbot widget to the AppLayout view in the System model to enable it for web as well

Web:

    {"bot": {"id": "5b3a83534eeb2f4ee5d99da4"},"channel": {"id": "3a8c6cec-a978-4f4b-8b6b-090e741bc4d9","token": "234eac54-bd4b-4aba-9771-dd5d07c5062f"}}

Create your own bots using KinveyChat - There is an excellent tutorial available:
[https://www.progress.com/kinvey/chat/chatbot-tutorial-intro](https://www.progress.com/kinvey/chat/chatbot-tutorial-intro)


