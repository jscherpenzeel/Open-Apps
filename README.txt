Quick Requisition Entry App

This all-in-one app is designed for quick entry of free text requisition line(s) to the users current basket. The idea is to make the creation of key feilds quickly while using the standard bulk edit features within the Coupa basket to apply the remianing required feilds before sending the requisition for approval.

Input feilds used by the App:
	1. Line Description
	2. Line Supplier
	3. Line Price
	4. Line Quantity
	5. Line UOM *applicable when quanitity is used. *Defaults to your instances default UOM code. 
	6. Line Commodity *Optional when using URL params below.

Input feilds NOT used by the App: *Must be editied within your basket before submiting for approval.
	1. All header feilds including custom feilds
	2. Line need-by-date
	3. Line shipping methods
	4. Line savings
	5. Line attachments
	6. Line account segments
	7. Line commodity
	8. Line custom feilds
	9. Supplier sites
	10. Manufacturer part number
	11. Manufacturer name
	12. Form responses

A valid API key is required for the app to function. Use of key permissons is highly recommended.
Required permissons are:
	1. Api/Requisitions > Update Requisition Without Validation
	2. Api/Currencies > Index
	Note. The app will query suppliers based on the user content resitrictions. No supplier API is needed.
	
This is a web based all in one .html file, using vue.js as the framwork *Note, does not support older browsers like IE. The App uses the web address URL parameters to save the API key and optionial extras. This makes customizing easy while maintaining security by not hard coding the API key. Security is achived by saving the API key in the url, and adding the address link as part of a Coupa homepage link with content groups, or by using the Coupa menu config with panels apps. 

Required URL paramenters are:
	1. API Key

Optional URL paramenters are:
	1. Table band background color *default is Coupa blue
	2. Currency *default is AUD
	3. Input Row limits *default is 100 *Standard Coupa requisition line limits is 100, check with Coupa support if you need that extended, but it can effect perfomance, and not a direct relation to the purchase orde line limit
	
Instructions to install the app:
	1. Save the .html file to a custom PO template of your choice. Setup > PO Customisation > Edit (*note, this will allow the web app to be available within the Coupa instance and is requirement to function)
	2. Open the saved .html file by editing the custom PO template agian, and clicking on the file
	3. Copy the URL from the browser web address bar
	4. Remove everything after and including the "etag=xxxxxxxxxxxxxxx" so your left with: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?
	5. Add the API key URL parameter behind the question mark: example: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?key=xxxxxxxxxxxxxx
	6. Add any optional extras to the URL if required.
		Currency Default: &cur=USD	example: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?key=xxxxxxxxxxxxxx&cur=USD
		Line limit: &lines=50		example: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?key=xxxxxxxxxxxxxx&cur=USD&lines=50
		Commodity Option: &com=true	example: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?key=xxxxxxxxxxxxxx&cur=USD&lines=50&com=true
		Band Color: &color=5cb85c	example: https://yourinstance.coupahost.com/public_attachments/Nm8dTy1m?key=xxxxxxxxxxxxxx&cur=USD&lines=50&color=5cb85c
		*note the band color uses the hash code, the same as your Coupa	band Colour under Company Infomation if your using one.
	7. Reload the browser page with the new address URL with all the parameters
	8. You can now test the app
	9. Create a Coupa panel app by going to: Setup > Installed Apps > Create > Create New iFrame App
	10. Use the app URL from above in the Application URL feild and save.
	11. Create a Coupa menu link by going to: Setup > Menu Configuration > Create > Secondary menu, and select the Installed App you created previously and save.
	12. Open the newly created menu app and copy the browser web address URL. Menu additions use a roll permisson, which you can add to users role based access if required.
	13. If you want to use the app from a Coupa homepage, create a homepage content with content groups applied if required, and use the URL link you saved above on your Coupa homepage. Users can then access the app via their content controled homepage links.

****ALLWAYS TEST BEFORE USING IN YOUR PRODUCTION INSTANCE****

VERSION UPDATES
1.01	Added file CSV input		
1.02	Added currencies as an option
1.03	Change starting table row count to 15 or to max limit if < 15
1.04 	Added feature to paste from any table cell, populating cells right and down of origin
	Updated Popup CSS
	Removed Supplier as a mandatory feild
	removed UOM "EA" to now use Coupa defult for Qty lines.
1.05	Fix issue with last line of paste array being removed
1.06	Added url parm for commodities/auto_complete
	Added optional commodities/auto_complete functionality
1.07	Use enforce leave node when applicable on commdoties


