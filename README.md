# Commerce Extensibility

This repository contains a reference implementation of the Commerce Extensibility Framework. It includes sample code for extending the following services:

- Pricing
- Shipping Calculator
- Tax Calculator

Each set of sample code includes: an Apex class, a test class, and any necessary resource files.

Live Heroku services are used to simulate a connection to a third-party system. You can bypass the Heroku service and use mocked data instead.

**Warning**: The sample code and Heroku services are provided "as is" for demonstration purposes only. Do not use the source code in a production system without modifying and testing it first. And do not use the Heroku services in a production system under any circumstances.

## Pricing Service

The sample code for Pricing Service includes an Apex class (in `PricingServiceSample.apxc`) that calls an external service to retrieve product prices and then saves that price in the `PricingResponseItems` list.

## Shipping Calculator

The sample code for Shipping Calculator includes an Apex class (in `ShippingCalculatorSample.apxc`) that calls an external service to retrieve shipping rates and then save that rate as an additional charge in the `CartItems` list.

## Tax Calculator

The sample code for Tax Calculator includes an Apex class (in `TaxCalculatorSample.apxc`) that calls an external service to retrieve tax information and then save those taxes in `CartTaxes` in `CartItems` and `CartItemAdjustments`.

## Error Handling

There are two types of errors that can surface from the reference implementations: user errors (which the shopper can see and correct) and admin errors (which the shopper can’t fix).

All reference implementations include examples of how to propagate an error to the user.

To propagate an error to the admin, throw an exception from the reference implementation. The user is presented with a generic error message telling them to contact their admin. At the same time, a Platform Status Alert Event platform event is published. A notification is created for the admin to see the error message.

To learn how to create a Platform Status Alert Event trigger for the notification, see [PlatformStatusAlertEvent](https://developer.salesforce.com/docs/atlas.en-us.platform_events.meta/platform_events/sforce_api_objects_platformstatusalertevent.htm) and [Flow Core Action: Send Custom Notification](https://help.salesforce.com/s/articleView?id=sf.flow_ref_elements_actions_sendcustomnotification.htm&type=5).

## Deployment

To deploy this reference implementation, use Workbench:

1. Clone this repository.
2. From this folder, create a .zip file:
   ```bash
   zip -r -X <your-zip-file>.zip *
   ```
3. Open Workbench and go to **Migration** > **Deploy**.
4. Select the file you created (`<your-zip-file>.zip`).
5. Check the **Single Package** checkbox.
6. Click **Next**.
7. Click **Deploy**.
