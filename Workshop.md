<h1 id="kinvey-and-openedge">Kinvey and OpenEdge</h1>
<p>A short workshop script to create a small NativeScript app, followed by Kinvey Studio web &amp; mobile app that integrates an OpenEdge based data source.</p>
<p><strong>Sports Shop App – MVP Requirements</strong><br>
As a Sports Shop 2000 customer I want to</p>
<ul>
<li>Login to the app</li>
<li>Display an editable list of sports equipment available in the shop (using an OE backend)</li>
<li>Arrange a consultation with a shop assistant on new skis in a shop location of my choice</li>
</ul>
<h2 id="workshop-requirements">Workshop requirements:</h2>
<ul>
<li>
<p>Windows or Mac required + Android Device or IPhone</p>
</li>
<li>
<p>Create Kinvey account (completely free):  <a href="https://console.kinvey.com/sign-up">https://console.kinvey.com/sign-up</a></p>
</li>
<li>
<p>Download and install Kinvey Studio:  <a href="https://studio.kinvey.com/">https://studio.kinvey.com/</a></p>
</li>
<li>
<p>Download and install NativeScript Playground &amp; Preview apps from Google Play  <a href="https://play.google.com/store/apps/details?id=org.nativescript.play">https://play.google.com/store/apps/details?id=org.nativescript.play</a><a href="https://play.google.com/store/apps/details?id=org.nativescript.preview">https://play.google.com/store/apps/details?id=org.nativescript.preview</a>  or Apple AppStore</p>
</li>
<li>
<p>Download and install Kinvey Scanner &amp; Preview apps from Google Play  <a href="https://play.google.com/store/apps/details?id=com.kinvey.scanner">https://play.google.com/store/apps/details?id=com.kinvey.scanner</a><a href="https://play.google.com/store/apps/details?id=com.kinvey.preview">https://play.google.com/store/apps/details?id=com.kinvey.preview</a>  or Apple AppStore</p>
</li>
<li>
<p>Install <a href="https://nodejs.org/dist/v10.16.0/node-v10.16.0-x64.msi">nodejs 10</a> and “npm install -g nativescript”</p>
</li>
</ul>
<h2 id="hands-on-1---create-a-nativescript-app">Hands-on 1 - Create a NativeScript App</h2>
<p><em><strong>Creating a NativeScript app that displays a list of items from a SmartComponent Library PASOE backend</strong></em></p>
<ol>
<li>Navigate to the  <a href="https://play.nativescript.org/?template=play-ng&amp;id=prFgzv&amp;v=7">NativeScript Playground Project</a></li>
<li><strong>Fork it</strong>  by selecting “Fork” from the toolbar above the code editor</li>
<li>Select “Preview” from the top right corner of the page</li>
<li>Open Playground on your mobile device and scan the barcode that is displayed</li>
<li>You should now see a login page, that is unusable (yet)</li>
<li>In app/shared/config.ts, update the API_BASE_URL to the one displayed.</li>
<li>You should now be able to sign in and see an empty “Home” screen.</li>
<li>In app/home/home.component.html, add the ListView where indicated and bind it to the “items” property found in the corresponding TS file. More information on how to use the ListView can be found  <a href="https://docs.nativescript.org/angular/ui/ng-components/listview">here</a></li>
<li>In app/home/home.component.ts, uncomment the block of code making the HTTP call.</li>
<li>Congratulations! You should now be able to see a list of sports items after you sign in.</li>
</ol>
<h2 id="hands-on-2---create-a-kinvey-app">Hands-on 2 - Create a Kinvey App</h2>
<p><em><strong>Creating an app backend using the Kinvey Console</strong></em></p>
<ol>
<li>Login to <a href="https://console.kinvey.com">https://console.kinvey.com</a></li>
<li>Create an app - Choose any name you like</li>
<li>Open the dashboard of the <em>Development</em> environment of that app</li>
<li>Create a user in that app (user: demo pw: demo)</li>
<li>Create a collection “items” in that app</li>
<li>Add a column “ItemName” in that collection<br>
<em>(add as a many additional columns as you like)</em></li>
<li>Add some data to that collection (e.g. sports equipment)</li>
<li>Retrieve/edit some data in the collection using the <em>API Console</em></li>
</ol>
<p>Learn more here: <a href="https://www.progress.com/blogs/how-to-get-started-with-kinvey-and-nativescript-fast">https://www.progress.com/blogs/how-to-get-started-with-kinvey-and-nativescript-fast</a></p>
<h2 id="hands-on-3---use-the-kinvey-sdk-in-a-nativescript-app">Hands-on 3 - Use the Kinvey SDK in a NativeScript App</h2>
<p><em><strong>Use the Kinvey SDK abstractions to access the Kinvey backend</strong></em></p>
<p><a href="https://devcenter.kinvey.com/nativescript/guides/datastore">https://devcenter.kinvey.com/nativescript/guides/datastore</a></p>
<ol>
<li>Navigate to the  <a href="https://play.nativescript.org/?template=play-ng&amp;id=AcHtxD&amp;v=2">NativeScript Playground Project</a></li>
<li><strong>Fork it</strong>  by selecting “Fork” from the toolbar above the code editor</li>
<li>Select “Preview” from the top right corner of the page</li>
<li>Open Playground on your mobile device and scan the barcode that is displayed</li>
<li>You should now see a login page, and after logging in a blank “Home” view</li>
<li>Add an OnInit method to the home.component.ts class to have an event handler for loading data when the view loads</li>
<li>Add a Kinvey DataStore private member to the class pointing at the “items” collection</li>
<li>Perform a fetch all by calling find() on the DataStore and subscribe to the results.</li>
<li>Assign the results the items class member</li>
<li>You should now see data from your Kinvey backend in the list</li>
</ol>
<h2 id="hands-on-4---use-an-external-data-source">Hands-on 4 - Use an External Data Source</h2>
<p><em><strong>Connect to an OpenEdge data source</strong></em></p>
<p>There are three options to integrate OpenEdge in Kinvey:</p>
<ul>
<li>
<p>Connect to OE using RapidData for Progress:<br>
<a href="https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforProgressData">https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforProgressData</a></p>
</li>
<li>
<p>Connect to OE using a FlexData connector for JSDO:<br>
<a href="https://devcenter.kinvey.com/rest/guides/flex-services#flex-data">https://devcenter.kinvey.com/rest/guides/flex-services#flex-data</a><br>
The JSDO FlexData connector is available here:<br>
<a href="https://github.com/steinerj/jsdo-kinvey-flex">https://github.com/steinerj/jsdo-kinvey-flex</a></p>
</li>
<li>
<p>Connect to OE using  RapidData - DataDirect Odata via SQL (not part of this workshop)<br>
<a href="https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforDataDirect">https://devcenter.kinvey.com/rest/guides/rapid-data#ConnectorforDataDirect</a></p>
</li>
</ul>
<h3 id="rapid-data-for-progress">Rapid Data for Progress</h3>
<ol>
<li>Under <em>Services</em> - create a new RapidData for Progress Connector in the scope of your app</li>
<li>Connection Details (anonymous auth)<br>
Endpoint: <a href="https://oemobiledemo.progress.com/OEMobileDemoServices/">https://oemobiledemo.progress.com/OEMobileDemoServices/</a><br>
Catalog:<br>
<a href="https://oemobiledemo.progress.com/OEMobileDemoServices/static/SportsService.json">https://oemobiledemo.progress.com/OEMobileDemoServices/static/SportsService.json</a></li>
<li>Create a new Service Object - Discover - <em>Item</em></li>
<li>Name as you like, choose <em>Itemnum</em> as primary key, Activate all operations, save and discover all fields, map <em>Itemnum</em> to <em>_id</em></li>
<li>In your app, swap the “items” store from internal to the newly created OE store</li>
<li>Test in API Console and/or web/mobile app</li>
</ol>
<h3 id="flexdata-connector-for-jsdo">FlexData connector for JSDO</h3>
<ol>
<li>Clone or download this repository: <a href="https://github.com/steinerj/jsdo-kinvey-flex">https://github.com/steinerj/jsdo-kinvey-flex</a></li>
<li>In the directory of the cloned repo, run the following commands to verify your environment is working correctly. This will run the flex data service locally.
<ul>
<li>npm install</li>
<li>node .</li>
</ul>
</li>
<li>You can now open <a href="http://localhost:10001/items">http://localhost:10001/items</a> to verify that the service is correctly retrieving items from the OE service.</li>
<li>In the Kinvey web console, create a Flex Service Runtime container under the “Services” tab in context of your Kinvey App</li>
<li>Run the following commands to create your Kinvey profile and deploy the flex service to the previously created container:
<ul>
<li>kinvey init</li>
<li>kinvey profile login NAME</li>
<li>kinvey flex init</li>
<li>kinvey flex deploy</li>
</ul>
</li>
<li>In your app, swap the “items” store from internal to the newly created FlexData service</li>
<li>Test in API Console and/or web/mobile app</li>
</ol>
<p>Learn more about Flex Services here:<br>
<a href="https://www.progress.com/blogs/getting-started-with-kinvey-flexservices">https://www.progress.com/blogs/getting-started-with-kinvey-flexservices</a></p>
<p>For learning how to set up JSDO capable OpenEdge Data Object Services, please follow these tutorials:<br>
<a href="https://www.youtube.com/watch?v=Nk9wrmYUFPA">https://www.youtube.com/watch?v=Nk9wrmYUFPA</a></p>
<p><a href="https://www.progress.com/services/education/openedge/creating-openedge-data-object-services">https://www.progress.com/services/education/openedge/creating-openedge-data-object-services</a></p>
<h2 id="optional-hands-on---create-a-kinvey-studio-app">Optional: Hands-on - Create a Kinvey Studio app</h2>
<p><em><strong>Build a web &amp; mobile app based on Angular, NativeScript and Kinvey using the low code Kinvey Studio</strong></em></p>
<p><strong>Steps:</strong></p>
<ol>
<li>Create a new app in Studio and point it to your Kinvey Backend app</li>
<li>Choose an app theme (bonus: fine tune the styling on css level - see: <a href="https://devcenter.kinvey.com/nativescript/guides/studio-themes">https://devcenter.kinvey.com/nativescript/guides/studio-themes</a>)</li>
<li>Modify the login page in the systems module to use a different logo</li>
<li>Create a new module, e.g. “Sports”</li>
<li>Create a web view grid and point it to the “items” collection</li>
<li>Create a mobile list view (single or double line) and also point it to items - add it only to the tab navigation</li>
<li>Activate search for both</li>
<li>Test in browser and phone</li>
</ol>
<p>For reference: <a href="https://devcenter.kinvey.com/nativescript/guides/studio-getting-started">https://devcenter.kinvey.com/nativescript/guides/studio-getting-started</a></p>
<h2 id="optional-hands-on---chatbot">Optional Hands-on - Chatbot</h2>
<p><em><strong>Offer a modern, conversational UI as part of your web &amp; mobile app</strong></em></p>
<ol>
<li>Create a blank mobile view and a layout manager</li>
<li>Add a “Chat” component</li>
<li>Under advanced - paste the following chatbot JSON:</li>
</ol>
<p>Mobile:</p>
<pre><code>{
"botId": "5b3a83534eeb2f4ee5d99da4",
"channelId": "9e48b0dc-8cdb-4e79-9ce0-6595e8ab2da3",
"channelToken": "1b45111f-d2f1-49ff-8531-4980ad1fcceb"
} 
</code></pre>
<ol start="4">
<li>Add a chatbot widget to the AppLayout view in the System model to enable it for web as well</li>
</ol>
<p>Web:</p>
<pre><code>{"bot": {"id": "5b3a83534eeb2f4ee5d99da4"},"channel": {"id": "3a8c6cec-a978-4f4b-8b6b-090e741bc4d9","token": "234eac54-bd4b-4aba-9771-dd5d07c5062f"}}
</code></pre>
<p>Create your own bots using KinveyChat - There is an excellent tutorial available:<br>
<a href="https://www.progress.com/kinvey/chat/chatbot-tutorial-intro">https://www.progress.com/kinvey/chat/chatbot-tutorial-intro</a></p>

