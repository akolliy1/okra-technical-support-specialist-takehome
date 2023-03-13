# okra-technical-support-specialist-takehome
Okra Technical Support Specialist Takehome

### Section 1: Non technical

1. Question:


> Peter, a member of the sales team just onboarded a high value merchant - Codak Ventures. Before go-live during the integration review session, you had given Codak Ventures’ integration a green light and the merchant has gone ahead to open the service to its customers. 

> In recent times, the merchant has escalated a number of issues which point to the fact that there are issues with their integration. These errors are primarily responsible for the escalated issues. The dev team for the merchant is becoming impatient and has threatened to churn if their issues are not resolved ASAP. How will you handle such a merchant and manage the expectations of Peter in preventing Churn.

#### Answer:

As a technical support specialist, my primary responsibility is to ensure that the technical issues that Codak Ventures is experiencing are resolved promptly to prevent the merchant from churning. Here are the steps I would take:

1. Assess the situation: I would review the issues reported by Codak Ventures and determine the root cause of the problems. This would require communicating with the development team and identifying any technical issues that are affecting the integration.

2. Prioritize the issues: After identifying the issues, I would prioritize them based on their impact on Codak Ventures' business. Issues with high impact on their business should be addressed first.

3. Communicate with Peter and Codak Ventures: I would provide regular updates to Peter and Codak Ventures on the progress of the resolution of the technical issues. I would be transparent about the challenges faced by our development team and provide realistic timelines for when the issues will be resolved.

4. Escalate the issue: If the issues are complex and require additional support, I would escalate the issue to the appropriate team within the company. I would ensure that Codak Ventures receives regular updates on the status of the issue.

5. Provide additional support: In addition to resolving the technical issues, I would provide Codak Ventures with additional support to help them optimize their integration. This could include providing training on our products and services or offering suggestions for improving their integration.

6. Follow up: After resolving the technical issues, I would follow up with Codak Ventures to ensure that they are satisfied with the resolution and to address any additional concerns they may have.

By taking these steps, I would be able to manage the expectations of Peter and prevent the merchant from churning. I would also demonstrate to Codak Ventures that we are committed to resolving any technical issues they may have and providing them with the necessary support to optimize their integration.

### Section 2: Semi technical

As a Technical Support Engineer, you’ll need to have exceptional people skills and the engineering mindset that will allow you to troubleshoot, diagnose and resolve while communicating the issue effectively to the client. As such, we’d like to evaluate your language and engineering skills. 

Please answer on the below list of questions as if you would answer a customer in real-life, feel free to use the Okra docs ([https://docs.okra.ng/docs](https://docs.okra.ng/docs)).

##### Question & Response:

> 1. Hey Okra team, I’m trying to get the latest transactions and I’m hitting the [https://api.okra.ng/v2/transactions/getById](https://api.okra.ng/v2/transactions/getById) but it’s only giving me a week old transactions for some reason. Please help! Jesse

##### Response:

Hello Jesse,

Thank you for contacting Okra!

The transaction endpoint in your context is meant to retrieve a paginated list of a specific transaction of a customer and it is arranged by date in an ascending order.

For your desired result, I would suggest this transaction [POST:https://api.okra.ng/v2/transactions/getByDate] endpoint to get the latest transactions within a specific date range.

This suggested endpoint required a body parameters such as `from` date as a string type, `to` date as string type when making the api call.

For instance, the below is a typical api reference.

```
const axios = require('axios');

const data = JSON.stringify({
    from: '2020-04-25',
    to: '2020-09-25',
    limit: 1,
    page: 1
});

const options = {
  method: 'POST',
  url: 'https://api.okra.ng/v2/transactions/getByDate',
  headers: {accept: 'application/json; charset=utf-8', 'content-type': 'application/json'},
  data,
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  })
```

And an alternative to the suggested transaction endpoint that allows you to retrieve data for `a customer within a specific date range` is the [POST:https://api.okra.ng/v2/transactions/getByCustomerDate].

This suggested alternative transaction endpoint required `customer_id`, `from` date as a string type, `to` date as string type. It is similar to transaction [POST:https://api.okra.ng/v2/transactions/getByDate] endpoint suggested earlier, Except for an additional `body parameter` required which is `customer_id`.

However, They are other transaction endpoints from our docs you could try and that would give your desired result, read more on https://docs.okra.ng/reference/gettransactionbydate.

Please provide the required parameters for the transactions endpoints.

Happy to help if you need anything else.

Akolade <br>
Okra

> Then a follow up mail to Jesse, to confirm the previous mail was helpful or needed any help.

Hello Jesse,

Just wanted to check back in to see if you had any other questions, or if there was anything else that I could do to help.

Let me know! 😊

Akolade<br>
Okra

> 2. Hi! I’ve setup the Widget and I can connect the account, however I don’t understand how to programmatically indicate that the connection was successful or it thrown an error. Thanks in advance. Mike

##### Response:

Hi Mike,

Thank you for reaching out to our technical support team. I can definitely help you with that.

To programmatically indicate that the connection was successful or thrown an error, you will need to implement error handling in your code. When the connection is established successfully, you can create a simple logger that takes in parameters like success status code, such as HTTP 200, and include any relevant data in the response. If an error occurs, you can add a logger to display an appropriate error code, such as HTTP 400 or 500, and include a message that describes the error in the response.

Here is an example code snippet in JavaScript SDK that demonstrates error handling for a successful connection and an error:

```
// Attempt to connect to the account
const widgetOkra = () => {

    Okra.buildWithOptions({
        name: 'Peter the Builder',
        env: 'production-sandbox',
        app_id: '',// app_id from your app builder
        key: 'YOUR PRODUCTION KEY FROM YOUR DASHBOARD', 
        token: 'YOUR CLIENT TOKEN FROM YOUR DASHBOARD',
        connectMessage: 'SDK connected successfully', // Instruction to connect account
        products: ['auth','identity','balance','transactions', 'income'], //in lowercase
        onSuccess: function(data){
            // If the connection is successful, log a success response with a status code and data
            console.log(`Status code: ${200} | Connection successful: ${JSON.stringify(data)}`);
        },
        onError: function(error){
            // If an error occurs, log an error response with a status code and message
            console.error(`Status code: ${400} | Connection error: ${error.message}`);
        }
        onClose: function(){
            console.log('options close')
        }
    })
}
```

In this example, widgetOkra is a function that attempts to connect to the account with the specified app_id, key, env and token. If an error occurs, the function logs an error object that includes a message describing the error. If the connection is successful, the function logs data relevant to the connection.

I hope this helps! Let me know if you have any other questions or concerns.

Best regards,<br>
Akolade


> 3. Hello, my name is Blessing and I would like to understand how do I test Okra. I wouldn’t like to pay for my testing.

##### Response:

Hi Blessing,

Thank you for reaching out to our technical support team. I can help you with your question.

Okra provides a sandbox environment for testing without incurring any charges. The sandbox environment is a replica of the live environment, but all transactions performed in it are for testing purposes only.

To get started with testing on Okra, you will need to sign up for a free account on our dashboard and obtain your sandbox API key. You can then use this API key to test your integration with our sandbox environment.

Here's an example of how to use Okra in sandbox mode using Node.js:

```
// Set up Okra with your sandbox API key
const okra = require('okra-ng')('sandbox', 'your_sandbox_api_key_here');

// Get a list of institutions
okra.getInstitutions((error, response) => {
  if (error) {
    // Handle error
  } else {
    // Handle success
  }
});
```
In this example, we've set up Okra with the sandbox environment and obtained a list of institutions. You can modify this code to suit your integration.

You can find more information about testing on Okra's documentation page or reach out to our support team if you have any further questions or concerns.

I hope this helps! Let me know if you need further assistance.

Best regards,<br>
Akolade
<br>
### Section 3: Technical

Given the following, can you troubleshoot why the customer is having issues with these routes? Feel free to use Postman or any tool of your choice.


##### Question & Response:

> 1. Fix Route [https://docs.okra.ng/reference/fetchauths] Issue


#### Answer

Dear [Customer Name],

I am writing to inform you that we have successfully resolved the issue with your API. Upon investigation, our technical team discovered that the issue was caused by using the wrong API reference in your code.

Here is the right api reference for https://docs.okra.ng/reference/fetchauths, send a post request to the route [https://api.okra.ng/v2/products/auths] include `limit` parameters in your api call `BODY`, and the `bearer token` in the api call `Header`.

Here's an example of how to retrieve the bank account associated with a record's current, savings, and domiciliary accounts, along with high-level account data and balances.\ in Node.js, Fetch Auths:

```
var axios = require('axios');
var data = JSON.stringify({
  "page": 1
});

var config = {
  method: 'post',
  url: 'https://api.okra.ng/v2/products/auths',
  headers: { 
    'Authorization': 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGE2MzU4MTMwYTk0MzQ4NmYzM2RjZWQiLCJpYXQiOjE2NzU4NDk5NTR9.DP2dfE9xDXKwviPeMQa6a1_pXkxIa3C8G8kPbg9o1Vk', 
    'Content-Type': 'application/json', 
    'Cookie': 'AWSALB=+p4pxZjQR6jzAvVs2ieBSuSPwlN0O9yagqtADih3OzgRnb5o+Dwk7YvxV5IILJYAgfd3r0Bju2NIs5NaEweqdTW8sQ8r8ENyl7oOQQahv7ilyGuu62pcm6q2N86s; AWSALBCORS=+p4pxZjQR6jzAvVs2ieBSuSPwlN0O9yagqtADih3OzgRnb5o+Dwk7YvxV5IILJYAgfd3r0Bju2NIs5NaEweqdTW8sQ8r8ENyl7oOQQahv7ilyGuu62pcm6q2N86s'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

We understand that it can be challenging to navigate complex APIs, and we apologize for any confusion this may have caused. Our team has taken steps to ensure that this type of issue does not occur in the future, including providing clearer documentation and improving our support channels.

We are pleased to report that your API is now fully functional, and you should be able to use it without any further issues. If you have any questions or concerns, please do not hesitate to reach out to us.

Thank you for choosing our services, and we look forward to continuing to support your business.

Best regards,

Akolade<br>
Technical Support Specialist



> 2. Fix Route [https://docs.okra.ng/reference/getidentitybydate] Issue


#### Answer

Dear [Customer Name],

I am writing to inform you that we have successfully resolved the issue with your API. Upon investigation, our technical team discovered that the issue was caused by using the wrong API reference in your code.

Here is the right api reference for https://docs.okra.ng/reference/getidentitybydate, send a post request to the route [https://api.okra.ng/v2/identity/getByDate] include `to`, `from`, `limit` parameters in your api call `BODY`, and the `bearer token` in the api call `Header`.

Here's an example of how to Get identity by date in Node.js:

```
var axios = require('axios');
var data = JSON.stringify({
  "page": 1,
  "from": "2023-02-01",
  "to": "2023-03-01"
});

var config = {
  method: 'post',
  url: 'https://api.okra.ng/v2/identity/getByDate',
  headers: { 
    'Authorization': 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGE2MzU4MTMwYTk0MzQ4NmYzM2RjZWQiLCJpYXQiOjE2NzU4NDk5NTR9.DP2dfE9xDXKwviPeMQa6a1_pXkxIa3C8G8kPbg9o1Vk', 
    'Content-Type': 'application/json', 
    'Cookie': 'AWSALB=+p4pxZjQR6jzAvVs2ieBSuSPwlN0O9yagqtADih3OzgRnb5o+Dwk7YvxV5IILJYAgfd3r0Bju2NIs5NaEweqdTW8sQ8r8ENyl7oOQQahv7ilyGuu62pcm6q2N86s; AWSALBCORS=+p4pxZjQR6jzAvVs2ieBSuSPwlN0O9yagqtADih3OzgRnb5o+Dwk7YvxV5IILJYAgfd3r0Bju2NIs5NaEweqdTW8sQ8r8ENyl7oOQQahv7ilyGuu62pcm6q2N86s'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

We understand that it can be challenging to navigate complex APIs, and we apologize for any confusion this may have caused. Our team has taken steps to ensure that this type of issue does not occur in the future, including providing clearer documentation and improving our support channels.

We are pleased to report that your API is now fully functional, and you should be able to use it without any further issues. If you have any questions or concerns, please do not hesitate to reach out to us.

Thank you for choosing our services, and we look forward to continuing to support your business.

Best regards,

Akolade<br>
Technical Support Specialist





