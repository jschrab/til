# Magento / UPS API Integration setup

(Abbreviated from source)

### Request your Development Access Key
This step is normally the step that I get lost on, lol. I’ve got the logging in part down to a science.
1.	On the UPS website you will hover over the Support menu item and click on the Technology Support menu item.
2.	Under the Tools and Resources box you will need to click the link for the UPS Developer Resource Center.
3.	Step three on this page is title Download APIs, you will want to click the first link there called Access the UPS Developer Kit.
4.	On this page you will see a box that is titled How to Get Started, and Step 5 within this box is a linked called Request an Access Key, click this link.
5.	Enter your personal contact information into step 2, seeing as your the person that is doing the integration for this account, then click the blue button at the bottom of this form labeled Request an Access Key.
6.	Save this access key, because it is everything that your production Magento store will need to pull rates.

### Configure Magento
You will need to open the Magento payment methods screen that we accessed earlier. Find the UPS option and click on it if the options are not visible. Here’s an explanation of each of the options for you to decide how your store needs to be configured.
1.	Enabled for Checkout
You will need to set this option to Enabled once you have everything configured correctly.
2.	UPS Type
The default selection is United Parcel Service, but this API integration will not return your negotiated rates. Toggle this option to United Parcel Service XML, so that you can receive your negotiated rates.
3.	Gateway XML URL
You shouldn’t have to change these, but in case your were lost somehow, here they are again:
https://onlinetools.ups.com/ups.app/xml/Rate
4.	Tracking XML URL
https://onlinetools.ups.com/ups.app/xml/Track
5.	Shipping Confirm XML URL
https://onlinetools.ups.com/ups.app/xml/ShipConfirm
6.	Shipping Accept XML URL
https://onlinetools.ups.com/ups.app/xml/ShipAccept
7.	Mode
If set to Live, then UPS will attempt to verify your website while using the https, secure connection. The alternative is to set the option to Development, but in my personal experiences this option has never made any difference.
8.	Password
This is the password from your UPS online login credentials, of which you have properly connected to your shipper number.
9.	User ID
This is the username from your UPS online login credentials, of which you have properly connected to your shipper number.
10.	Access License Number
You just received this as your Access Key from the last step. A copy should have also been emailed to the account owner. If you’ve trained them well, they should have already forwarded it to your inbox.
11.	Origin of the Shipment
This information will be sent to UPS for each XML request. UPS will use this data along with your zip code and state to calculate your rates.
12.	Title
This is what your users will see headlining the section of your checkout process where all of the UPS rates are listed. The default value serves just fine IMO.
13.	Enable Negotiated Rates
Don’t forget to Enable Negotiated Rates like we have been trying to do this whole time.
14.	Packages Request Type
  1.	Divide to Equal Weight
  2.	Use Origin Weight
15.	Container
UPS will adjust their provided weights based on the type of packaging that you select.
16.	Shipper Number
This is the number that is associated with your negotiated rates and the ups.com login information from earlier.
17.	Destination Type
This is important, UPS has two completely different rates that it provides for addresses, Residential and Commercial. If you select Residential, then UPS will add a Residential surcharge of around $3.00 to every delivery.
UPS does not determine whether or not the Address is a residential or not when it provides you with the rates. You are responsible for telling UPS what the address is, if you want accurate rates.
Most of the time customers prefer that the rates are exactly accurate, so you will need to install an extension that will validate the shipping address using the UPS address validation xml. Once validated, then the extension will update the UPS Rates xml to receive more accurate rates.
18.	Maximum Package Weight
UPS has a maximum weight of 150 pounds. If you exceed this weight, then UPS will return a rate for only 150 pounds. Sometimes when you have multiple items in a shopping cart, they will override this shipping rate if combined for pricing.

Crazy helpful UPS API integration setup source: https://merchantprotocol.com/602/magento-ups-integration-and-negotiated-rates/
