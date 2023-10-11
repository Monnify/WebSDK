# WebSDK

### An Integration Guide for the Monnify Web SDK


With the Monnify Web SDK, you are able to receive payments in your web application via:

* Card
* Bank Transfer
* USSD
* Phone Number

Implementation steps

1. ##### Adding the javascript plugin link to your website
  This can be done by adding the checkout Javascript snippet to your website using the code sample shown below:
  ```javascript
  <html>
<head>
    <script type="text/javascript" src="https://sdk.monnify.com/plugin/monnify.js"></script>
    <script>
        function payWithMonnify() {
            MonnifySDK.initialize({
                amount: 100,
                currency: "NGN",
                reference: new String((new Date()).getTime()),
                customerFullName: "Damilare Ogunnaike",
                customerEmail: "ogunnaike.damilare@gmail.com",
                apiKey: "MK_TEST_*****",
                contractCode: "6266*****",
                paymentDescription: "Lahray World",
                metadata: {
                    "name": "Damilare",
                    "age": 45
                },
                incomeSplitConfig: [{
                    "subAccountCode": "MFY_SUB_342113621921",
                    "feePercentage": 50,
                    "splitAmount": 1900,
                    "feeBearer": true
                }, {
                    "subAccountCode": "MFY_SUB_342113621922",
                    "feePercentage": 50,
                    "splitAmount": 2100,
                    "feeBearer": true
                }],

                onLoadStart: () => {
                    console.log("loading has started");
                },
                onLoadComplete: () => {
                    console.log("SDK is UP");
                },

                onComplete: function(response) {
                    //Implement what happens when the transaction is completed.
                    console.log(response);
                },
                onClose: function(data) {
                    //Implement what should happen when the modal is closed here
                    console.log(data);
                }
            });
        }
    </script>
</head>

<body>
    <div>
        <button type="button" onclick="payWithMonnify()">Pay With Monnify</button>
    </div>
</body>
</html>

  ```

  You will need to set your API key and Contract code which can be gotten from the developer section of your Monnify dashboard.
  Furthermore, you won't be needing to set the application environment as this will be determine by your API credentials.

   
  

2. ##### Handle callback functions
   There are optional callbacks that you can handle before and after the transactions:

   * OnLoadStart:
   This callback is called when the sdk is about to start

   ```javascript
   onLoadStart: () => {
                    console.log("loading has started");
                }
   ``` 

   * OnLoadComplete:
   This callback is called immediately the web sdk is up.
   ```javascript
   onLoadComplete: () => {
                    console.log("SDK is UP");
                }
   ```

   * OnComplete:
   This callback is called when the transaction is completed. Transaction completion data like transactionReference, paymentReference, paymentStatus and paymentMethod are sent to this callback.
   ```javascript
   onComplete: function(response) {
    console.log(response);
    }
   ```

   * OnClose
   This callback is called as soon as the checkout modal is closed and the status of the payment is also sent as part of the callback payload
   ```javascript
   onClose: function(data) {
                    console.log(data);
                }
   ```
     

___
For further information, you can check out our [developer documentation](https://developers.monnify.com) and you can also join our [slack community](https://slack.monnify.com).



