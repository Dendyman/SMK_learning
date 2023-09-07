# Step 0 «Enter SAP Build Lobby»

Open <https://samruktest-gdpazdel.eu10.build.cloud.sap/lobby>\
Authentificate using <https://a8nbw3y7x.accounts.ondemand.com/>
(only if the authentification is requested)

![](./media/image1.png)

Enter your user and password

![](./media/image2.png)

# Step 1 «Creating an Application Project in SAP Build apps Lobby»: 

Create your application project by clicking on **Create**.\
![Create the project](./media/image3.png)

Choose **Build an Application**.\
\
![Build App](./media/image4.png)

Next, select **Web & Mobile Application**\
![Name the project](./media/image5.png)

For the *Project Name*, specify a name based on your user, such as **mobile_app_ws_user(?),** add a comment in the description, and then click **Create** to start working on your application.\
\
![](./media/image6.png)

# Step 2 «Opening the Project, Home Page»: 

Upon completing Step 1, you will be redirected to the Build Apps Composer editor, which is a kind of IDE (Integrated Development Environment) for SAP Build Apps. On the canvas, you can already see the initial **Home page** of your application with fields for the title and text:\
![](./media/image7.png)

On the left, you will find elements that can be added to the canvas. On the right, there is a properties panel for the selected element, and at the bottom right, you will find the tree of elements on the canvas. Below, there is a panel for adding logic to the elements.

In summary, building your application involves:

\- Defining connections to data sources and application variables.

\- Designing UI elements.

\- Implementing logic for the selected elements.


# Step 3 "Building the app: connecting to Data":

In this step, we will focus on connecting our application to data sources. Follow the instructions below:

1. Navigate to the **DATA** tab:
   ![](./media/image8.png)

2. In the SAP Build Apps classic data entities section, create definitions for two API calls of type OData Integration:

   - One API call is for retrieving data about a request by its UUID, which is read from a QR code.
   
   - The other API call is for uploading an image to the Blob table using the UUID from a QR code.

   To create these API calls, select the **OData Integration** type:
   ![](./media/image9.png)

3. Insert the link to the description of our API services (\$metadata) from the API server:

   https://afanasevdm-cfruntime-371tohiy-dev-dbapi-fiori-srv.cfapps.us10.hana.ondemand.com/service/catalog/$metadata

   Then click **Verify URL**:
   ![](./media/image10.png)

4. The configurator, using the metadata information, has identified 2 entities: **Request** and **Blobstorage**. Activate both of them:
   ![](./media/image11.png)

5. For these entities, settings for standard access methods (GET, POST, UPDATE, etc.) will appear. Save the default settigs by clicking **SAVE DATA RESOURCES**:
   ![](./media/image12.png)

6. As a result, the project will now have defined access methods for the 2 API services: **Request** (a table of requests) and **Blobstorage** (a table of blob objects with UUIDs from requests).

   The outcome should look like this:
   ![](./media/image13.png)

# Step 4 «Building the app: creating app pages»:

In accordance with the application architecture, we need to create two application pages: "**Home Page**" and "**Photo Page**." Follow the steps below to create these pages:

1. Click on the link labeled "**Home Page**":
   ![Home Page Link](./media/image14.png)

2. The configurator will open, and you need to add the second page. Click on **ADD NEW PAGE**:
   ![Add New Page](./media/image15.png)

3. In the window that appears, enter the page name as "**Photo Page**" and then click **OK**:
   ![Enter Page Name](./media/image16.png)

4. The newly created page will open. Click **SAVE** to save your changes:
   ![Save Page](./media/image17.png)


# Step 5 «Building the app: adding UI elements to the first page»:

Navigate to the first page of the application by clicking on **Home page** in the navigation link, and then on the actual "**Home page**" itself (you may need to click **SAVE** if the previous changes were not saved):

![Navigation to Home Page](./media/image18.png)

![Home Page](./media/image19.png)

Select the *Headerline* and change the text to the following: "***Point the camera at QR-code***":

![Headerline](./media/image20.png)

In the **LAYOUT** tab, under the **LAYOUT** section, choose center alignment:

![Center Alignment](./media/image21.png)

Remove the second **Text 1** element:

![Remove Text Element](./media/image22.png)

Add a **Button** element to the canvas of the first page from the left-side element library under the **CORE** tab. Change the button's label to ***"Scan QR"***:

![Add Button Element](./media/image23.png)

# Step 6 «Building the app: adding processing logic of the first page»:

Let's define the variable **uuid_var** as an *App Variable* with the type *"**any text**"*, where the UUID of the request will be stored. To do this, switch to **VIEW -- VARIABLES**:

![Define Variable](./media/image24.png)

Save your changes using **SAVE**.

Navigate back to the first page of the application, "**Home page**," by switching to **VIEW -- VARIABLES**.

Select the **Scan QR** button and open the **Show logic for "BUTTON 1"** panel at the bottom of the screen:

![Button Logic](./media/image25.png)

In the opened panel, add the following elements from the **Logic CORE** panel on the left:

#### Device: Scan QR/barcode

#### Variables: Set app variable

#### Data: Get Record

#### Navigation: Open page

#### Dialog: Alert

#### Dialog: Alert

Connect these elements as shown in the diagram:

![Logic Diagram](./media/image26.png)

In the **"Variables: Set app variable"** logic block, assign the value from the **"Scan QR/barcode"** logic block to the **uuid_var** App Variable by selecting the variable in the **Variable name** field:

![Set Variable Value](./media/image27.png)

Assign the output value of the previous block by clicking on the icon under **Assigned value** and selecting **Output value of another node**:

![Assign Output Value](./media/image28.png)

Next, choose **Scan QR/barcode** under **Select logic node**, **Scan QR/barcode / QR barcode content** under **Select node output**, and then click **SAVE**:

![Assign QR Output](./media/image29.png)

To read data using the **"Data: Get record"** logic block, using the decoded UUID value stored in the **uuid_var** variable, fill in the parameters of the block as follows:

Maintain **Resource Name** as follows to make an API call to **Request** resource:

![Get Record API](./media/image30.png)

The **Id** parameter is filled with the variable:

![Id Parameter](./media/image31.png)

Next, under **App Variables**, choose the **uuid_var** variable and click **SAVE**:

![Variable Selection](./media/image32.png)

For the first **Alert** element, set the text as "**cannot read QR**" for unsuccessful QR code reading:

![First Alert](./media/image33.png)

Similarly, for the second **Alert**, set the message for unsuccessful reading from the API as "**request not found**":

![Second Alert](./media/image34.png)

Save all changes in the project using the **SAVE** button:

![Save Project](./media/image35.png)


# Step 7 «Building the app: adding data variables and UI elements of the second page»:

Navigate to the "**Photo page**":

![Photo Page](./media/image36.png)

Switch to the **VARIABLES** mode and add 2 variables, **name** and **surname**, as page parameters on the **PAGE PARAMETERS** tab:

![Page Parameters](./media/image37.png)

Go to the **PAGE VARIABLES** tab and create 2 more variables to store the captured photo with their respective data types (*mimetype -- text; photo_path -- local file system path*):

![Page Variables](./media/image38.png)

Switch to the VIEW mode and remove the **Headline** element.
![Text Element](./media/image38_2.png)

For the text element, set the Content property as a formula with the value **JOIN(\["Take a photo for ", params.name, params.surname\], ' ')**:

![Text Element](./media/image39.png)

Save the result:

![Save Result](./media/image40.png)

Align the text to the center by changing the properties of the text field as shown: **LAYOUT -> Text Align -> center**:

![Text Alignment](./media/image41.png)

Next, add new elements to the canvas of the "**Photo page**":

- Image

- Button 1

- Button 2

Change the *label* property for the buttons as shown in the image:

![Button Labels](./media/image42.png)

For the *Image* element, bind the **Source** property of the image to the **PAGE VARIABLE: photo_path**:

![Image Source](./media/image43.png)

Then, set fixed dimensions for the image:

![Image Dimensions](./media/image44.png)

And center-align the image:

![Image Alignment](./media/image45.png)


# Step 8 «Building the app: adding processing logic of the second page -- "take photo" button»:

Select the "**Take a photo**" button and open the logic panel by clicking on **Marketplace**:

![Take a Photo Button](./media/image46.png)

In the search field, type "convert file to base64" and select the found element:

![Search and Select Element](./media/image47.png)

Next, install the component by clicking **INSTALL**:

![Install Component](./media/image48.png)

Afterward, the element will appear in the **INSTALLED** tab:

![Installed Component](./media/image49.png)

Now, let's drag and drop the following elements to the logic canvas for the button's functionality:

**DEVICE: take photo**

**VARIABLES: set page variable**

**VARIABLES: set page variable**

**DIALOG: Alert**

Connect them as shown in the image:

![Connect Elements](./media/image50.png)

For one variable, link it to the **mimeType** output of the **Take photo** element and the page variable **mimetype**:

![Assign MimeType](./media/image51.png)

Then, save your changes.

For the second variable, configure it to assign the page variable **photo_path** with the output of the **Take photo -- path** block:

![Assign Photo Path](./media/image52.png)

Save your changes.

For the **DIALOG: Alert** element, set the text to "**failed to take photo**":

![Alert Text](./media/image53.png)

Finally, save your project:

![Save Project](./media/image54.png)

# Step 9 «Building the app: processing logic of the second page -- "upload to system" button»: 

Select the "**Upload to system**" button and open the button's logic panel. Next, add the following elements to the panel:

- **MEDIA: Convert file to base64** (to serialize the photo into a text sequence and save it as a BLOB in the database field)
- **VIEW: Show spinner** (to freeze the screen while the converter and database upload process is running)
- **VIEW: Show spinner** (to unfreeze the screen in the case of success or error)
- **DATA: Create record** (to pass image parameters to the API and save them in the database)
- **DIALOG: Alert** (to display messages about the success or failure of the process)

Connect them as shown in the image:

![Connect Elements](./media/image55.png)

Next, for the **Convert file to base64** element, set the following parameters:
Specify the file URL for conversion from **PAGE VARIABLE photo_path**:

![Convert File URL](./media/image56.png)

For the Create Record element, choose the resource name: **Blobstorage**:

![Resource Name](./media/image57.png)

For the **Record** field, choose "**Object with properties**" and set the following values:

- Bind the **mimetype** field to the **mimetype** variable of type **PAGE VARIABLE**
- Bind the **req_uuid** field to the **uuid_var** variable of type **APP VARIABLE**
- Bind the **Imagedata** field to the output of the previous converter element, **Convert file to Base64 / Base64 text**

![Record Field](./media/image58.png)

For the **Alert** element for successful record creation in the database, display a success message - ***Uploaded***:

![Success Alert](./media/image59.png)

In case of unsuccessful database entry, display a message -- ***Failed to Upload***:

![Failure Alert](./media/image60.png)

For unsuccessful image conversion, display a message -- ***failed to convert***:

![Conversion Alert](./media/image61.png)

Save your entire project:

![Save Project](./media/image62.png)

# Step 10 «Building the app: linking parameters' transition between the pages»: 

Open the **Home page** and select the **Scan QR** button. Open the button's logic panel and choose the **NAVIGATION: Open page** block. In the **page** property (the next opened page), specify the **Photo page**:

![Open Page](./media/image63.png)

Then, link the required parameters of the opened page (**PAGE PARAMETERS** defined for **Photo page** earlier) to the returned result of the **API Get record** for the **Request** entity:

![Link Parameters](./media/image64.png)

Save your changes.

Save your entire project:

![Save Project](./media/image62.png)

# Step 11 «Testing the app on your device»:

1. Install the **SAP Build Apps** application from the App Store or Google Play Store.

2. Go to the Launch tab in your application project, then click **OPEN PREVIEW PORTAL**:

![Open Preview Portal](./media/image65.png)

3. On your mobile phone, open the **SAP Build Apps** application, and choose to sign in via SAP Build Apps:

![Sign In](./media/image66.png)

4. Enter the 6-digit code on the portal in your browser and click **Confirm**:

![Confirm Code](./media/image67.png)

5. In the mobile application, find your project in the list of Apps and click **Open**:

![Open Project](./media/image68.png)

The application will launch:

![App Launch](./media/image69.png)

6. Access the portal and open the **Reception** tab:

[Reception Portal](https://samruktest-gdpazdel.workzone.cfapps.eu10.hana.ondemand.com/site#workzone-home&/workpages/rYR9XbhxTRa1KE6OapUqCe)

In the list, find your request, enter it, scan the QR code on your mobile device, and take a photo.

As a result, the photo will appear in the receptionist's application on the portal.

